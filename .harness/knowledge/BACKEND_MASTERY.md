# 🔧 BACKEND MASTERY

> **Deep expertise for building production-grade backend applications.**
> **Reference this document during Phases 06, 07, 09, 11, 12.**

---

## 🎯 BACKEND EXCELLENCE STANDARDS

A production-grade backend must achieve:
- **Response Time**: P50 < 100ms, P95 < 200ms, P99 < 500ms
- **Availability**: 99.9% uptime target
- **Security**: OWASP Top 10 protected
- **Scalability**: Horizontally scalable architecture
- **Observability**: Structured logging, metrics, tracing
- **Documentation**: Complete OpenAPI specification
- **Testing**: > 80% code coverage

---

## 📁 PROJECT STRUCTURE

### Recommended Structure (Language-Agnostic Pattern)

```
src/
├── modules/                  # Feature modules (domain-driven)
│   ├── auth/
│   │   ├── auth.controller.ts    # HTTP handlers
│   │   ├── auth.service.ts       # Business logic
│   │   ├── auth.repository.ts    # Data access
│   │   ├── auth.dto.ts           # Data transfer objects
│   │   ├── auth.validation.ts    # Input validation
│   │   └── auth.test.ts          # Tests
│   │
│   ├── users/
│   │   ├── users.controller.ts
│   │   ├── users.service.ts
│   │   ├── users.repository.ts
│   │   └── ...
│   │
│   └── [feature]/
│
├── common/                   # Shared code
│   ├── middleware/
│   │   ├── auth.middleware.ts
│   │   ├── rate-limit.middleware.ts
│   │   ├── error-handler.middleware.ts
│   │   └── request-logger.middleware.ts
│   │
│   ├── guards/               # Authorization guards
│   │   ├── auth.guard.ts
│   │   └── roles.guard.ts
│   │
│   ├── decorators/           # Custom decorators
│   │   ├── current-user.decorator.ts
│   │   └── roles.decorator.ts
│   │
│   ├── filters/              # Exception filters
│   │   └── http-exception.filter.ts
│   │
│   ├── interceptors/
│   │   ├── transform.interceptor.ts
│   │   └── logging.interceptor.ts
│   │
│   └── utils/
│       ├── hash.ts
│       ├── token.ts
│       └── validation.ts
│
├── database/
│   ├── prisma/
│   │   ├── schema.prisma
│   │   └── migrations/
│   ├── seeds/
│   │   └── seed.ts
│   └── prisma.service.ts
│
├── config/
│   ├── app.config.ts
│   ├── database.config.ts
│   ├── jwt.config.ts
│   └── index.ts
│
├── types/
│   ├── express.d.ts          # Express type extensions
│   └── global.d.ts
│
└── main.ts                   # Application entry point
```

---

## 🔐 AUTHENTICATION PATTERNS

### JWT with Refresh Token Rotation

```typescript
// common/utils/token.ts
import jwt from 'jsonwebtoken';
import { randomBytes } from 'crypto';

interface TokenPayload {
  userId: string;
  email: string;
  role: string;
}

export const ACCESS_TOKEN_EXPIRY = '15m';
export const REFRESH_TOKEN_EXPIRY = '7d';

export function generateAccessToken(payload: TokenPayload): string {
  return jwt.sign(payload, process.env.JWT_ACCESS_SECRET!, {
    expiresIn: ACCESS_TOKEN_EXPIRY,
  });
}

export function generateRefreshToken(): string {
  return randomBytes(64).toString('hex');
}

export function verifyAccessToken(token: string): TokenPayload {
  return jwt.verify(token, process.env.JWT_ACCESS_SECRET!) as TokenPayload;
}

// modules/auth/auth.service.ts
export class AuthService {
  async login(email: string, password: string) {
    // 1. Find user
    const user = await this.userRepository.findByEmail(email);
    if (!user) {
      throw new UnauthorizedException('Invalid credentials');
    }
    
    // 2. Verify password
    const isValid = await this.verifyPassword(password, user.passwordHash);
    if (!isValid) {
      throw new UnauthorizedException('Invalid credentials');
    }
    
    // 3. Generate tokens
    const accessToken = generateAccessToken({
      userId: user.id,
      email: user.email,
      role: user.role,
    });
    
    const refreshToken = generateRefreshToken();
    const refreshTokenHash = await hashToken(refreshToken);
    
    // 4. Store refresh token (with family tracking for rotation)
    await this.tokenRepository.create({
      userId: user.id,
      tokenHash: refreshTokenHash,
      family: randomBytes(16).toString('hex'), // Token family for detecting reuse
      expiresAt: addDays(new Date(), 7),
    });
    
    return {
      accessToken,
      refreshToken,
      user: this.sanitizeUser(user),
    };
  }
  
  async refreshTokens(refreshToken: string) {
    // 1. Find token
    const tokenHash = await hashToken(refreshToken);
    const storedToken = await this.tokenRepository.findByHash(tokenHash);
    
    if (!storedToken || storedToken.expiresAt < new Date()) {
      throw new UnauthorizedException('Invalid refresh token');
    }
    
    // 2. Check if token was already used (reuse detection)
    if (storedToken.usedAt) {
      // Token reuse detected! Revoke entire family
      await this.tokenRepository.revokeFamily(storedToken.family);
      throw new UnauthorizedException('Token reuse detected');
    }
    
    // 3. Mark token as used
    await this.tokenRepository.markUsed(storedToken.id);
    
    // 4. Generate new tokens
    const user = await this.userRepository.findById(storedToken.userId);
    const newAccessToken = generateAccessToken({
      userId: user.id,
      email: user.email,
      role: user.role,
    });
    
    const newRefreshToken = generateRefreshToken();
    const newRefreshTokenHash = await hashToken(newRefreshToken);
    
    // 5. Store new refresh token (same family)
    await this.tokenRepository.create({
      userId: user.id,
      tokenHash: newRefreshTokenHash,
      family: storedToken.family, // Same family
      expiresAt: addDays(new Date(), 7),
    });
    
    return {
      accessToken: newAccessToken,
      refreshToken: newRefreshToken,
    };
  }
}
```

### Password Hashing

```typescript
// common/utils/hash.ts
import argon2 from 'argon2';

// Argon2id is recommended (memory-hard, resistant to side-channel attacks)
export async function hashPassword(password: string): Promise<string> {
  return argon2.hash(password, {
    type: argon2.argon2id,
    memoryCost: 65536, // 64 MB
    timeCost: 3,       // 3 iterations
    parallelism: 4,    // 4 parallel threads
  });
}

export async function verifyPassword(
  password: string,
  hash: string
): Promise<boolean> {
  return argon2.verify(hash, password);
}

// For tokens (simpler, faster)
export async function hashToken(token: string): Promise<string> {
  const { createHash } = await import('crypto');
  return createHash('sha256').update(token).digest('hex');
}
```

---

## 🛡️ AUTHORIZATION PATTERNS

### Role-Based Access Control (RBAC)

```typescript
// common/decorators/roles.decorator.ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';

export enum Role {
  ADMIN = 'ADMIN',
  USER = 'USER',
  GUEST = 'GUEST',
}

export const Roles = (...roles: Role[]) => SetMetadata(ROLES_KEY, roles);

// common/guards/roles.guard.ts
import { Injectable, CanActivate, ExecutionContext } from '@nestjs/common';
import { Reflector } from '@nestjs/core';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private reflector: Reflector) {}
  
  canActivate(context: ExecutionContext): boolean {
    const requiredRoles = this.reflector.getAllAndOverride<Role[]>(
      ROLES_KEY,
      [context.getHandler(), context.getClass()]
    );
    
    if (!requiredRoles) {
      return true; // No roles required
    }
    
    const { user } = context.switchToHttp().getRequest();
    return requiredRoles.includes(user.role);
  }
}

// Usage in controller
@Controller('admin')
@UseGuards(AuthGuard, RolesGuard)
export class AdminController {
  @Get('users')
  @Roles(Role.ADMIN)
  getAllUsers() {
    // Only admins can access
  }
}
```

### Resource Ownership Check

```typescript
// Always check resource ownership
async function updateProject(userId: string, projectId: string, data: UpdateProjectDto) {
  const project = await this.projectRepository.findById(projectId);
  
  if (!project) {
    throw new NotFoundException('Project not found');
  }
  
  // Check ownership
  if (project.ownerId !== userId) {
    throw new ForbiddenException('You do not have access to this project');
  }
  
  return this.projectRepository.update(projectId, data);
}
```

---

## ✅ INPUT VALIDATION

### Zod Schema Validation (JavaScript/TypeScript)

```typescript
// modules/users/users.validation.ts
import { z } from 'zod';

export const createUserSchema = z.object({
  email: z
    .string()
    .email('Invalid email format')
    .max(255)
    .transform((email) => email.toLowerCase().trim()),
  password: z
    .string()
    .min(8, 'Password must be at least 8 characters')
    .max(100)
    .regex(
      /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)/,
      'Password must contain uppercase, lowercase, and number'
    ),
  name: z
    .string()
    .min(1, 'Name is required')
    .max(100)
    .transform((name) => name.trim()),
});

export const updateUserSchema = z.object({
  name: z.string().min(1).max(100).trim().optional(),
  avatarUrl: z.string().url().optional(),
});

export const paginationSchema = z.object({
  page: z.coerce.number().int().min(1).default(1),
  limit: z.coerce.number().int().min(1).max(100).default(20),
  sort: z.enum(['createdAt', '-createdAt', 'name', '-name']).default('-createdAt'),
});

export type CreateUserInput = z.infer<typeof createUserSchema>;
export type UpdateUserInput = z.infer<typeof updateUserSchema>;

// Usage in controller
@Post()
async createUser(@Body() body: unknown) {
  const data = createUserSchema.parse(body); // Throws if invalid
  return this.usersService.create(data);
}
```

### Express Validation Middleware

```typescript
// common/middleware/validate.middleware.ts
import { Request, Response, NextFunction } from 'express';
import { ZodSchema, ZodError } from 'zod';

export function validate(schema: ZodSchema) {
  return (req: Request, res: Response, next: NextFunction) => {
    try {
      req.body = schema.parse(req.body);
      next();
    } catch (error) {
      if (error instanceof ZodError) {
        return res.status(400).json({
          error: {
            code: 'VALIDATION_ERROR',
            message: 'Invalid input',
            details: error.errors.map((e) => ({
              field: e.path.join('.'),
              message: e.message,
            })),
          },
        });
      }
      next(error);
    }
  };
}

// Usage
router.post('/users', validate(createUserSchema), createUser);
```

---

## 🚨 ERROR HANDLING

### Centralized Error Handler

```typescript
// common/filters/http-exception.filter.ts
import { 
  ExceptionFilter, 
  Catch, 
  ArgumentsHost, 
  HttpException,
  HttpStatus,
  Logger,
} from '@nestjs/common';
import { Request, Response } from 'express';

@Catch()
export class HttpExceptionFilter implements ExceptionFilter {
  private readonly logger = new Logger(HttpExceptionFilter.name);
  
  catch(exception: unknown, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const response = ctx.getResponse<Response>();
    const request = ctx.getRequest<Request>();
    
    let status = HttpStatus.INTERNAL_SERVER_ERROR;
    let message = 'Internal server error';
    let code = 'INTERNAL_ERROR';
    let details: any = undefined;
    
    if (exception instanceof HttpException) {
      status = exception.getStatus();
      const exceptionResponse = exception.getResponse();
      
      if (typeof exceptionResponse === 'object') {
        message = (exceptionResponse as any).message || exception.message;
        code = (exceptionResponse as any).code || this.getCodeFromStatus(status);
        details = (exceptionResponse as any).details;
      } else {
        message = exceptionResponse;
        code = this.getCodeFromStatus(status);
      }
    } else if (exception instanceof Error) {
      message = 'Internal server error';
      
      // Log the actual error (don't expose to client)
      this.logger.error(
        `Unhandled error: ${exception.message}`,
        exception.stack,
        {
          path: request.url,
          method: request.method,
          userId: (request as any).user?.id,
        }
      );
    }
    
    // Don't expose internal errors to client
    if (status === HttpStatus.INTERNAL_SERVER_ERROR) {
      message = 'Internal server error';
    }
    
    response.status(status).json({
      error: {
        code,
        message,
        details,
      },
      meta: {
        timestamp: new Date().toISOString(),
        path: request.url,
        requestId: (request as any).id, // If using request ID middleware
      },
    });
  }
  
  private getCodeFromStatus(status: number): string {
    const codeMap: Record<number, string> = {
      400: 'BAD_REQUEST',
      401: 'UNAUTHORIZED',
      403: 'FORBIDDEN',
      404: 'NOT_FOUND',
      409: 'CONFLICT',
      422: 'UNPROCESSABLE_ENTITY',
      429: 'RATE_LIMITED',
      500: 'INTERNAL_ERROR',
    };
    return codeMap[status] || 'ERROR';
  }
}
```

### Custom Exception Classes

```typescript
// common/exceptions/index.ts
import { HttpException, HttpStatus } from '@nestjs/common';

export class ValidationException extends HttpException {
  constructor(details: Array<{ field: string; message: string }>) {
    super(
      {
        code: 'VALIDATION_ERROR',
        message: 'Validation failed',
        details,
      },
      HttpStatus.BAD_REQUEST
    );
  }
}

export class ResourceNotFoundException extends HttpException {
  constructor(resource: string, id: string) {
    super(
      {
        code: 'NOT_FOUND',
        message: `${resource} with ID ${id} not found`,
      },
      HttpStatus.NOT_FOUND
    );
  }
}

export class ConflictException extends HttpException {
  constructor(message: string) {
    super(
      {
        code: 'CONFLICT',
        message,
      },
      HttpStatus.CONFLICT
    );
  }
}
```

---

## 🚦 RATE LIMITING

### Token Bucket with Redis

```typescript
// common/middleware/rate-limit.middleware.ts
import { Redis } from 'ioredis';

interface RateLimitConfig {
  limit: number;      // Max requests
  window: number;     // Time window in seconds
  keyPrefix: string;  // Redis key prefix
}

export function rateLimit(redis: Redis, config: RateLimitConfig) {
  return async (req: Request, res: Response, next: NextFunction) => {
    const key = `${config.keyPrefix}:${getKey(req)}`;
    
    const multi = redis.multi();
    multi.incr(key);
    multi.expire(key, config.window);
    
    const results = await multi.exec();
    const current = results?.[0]?.[1] as number;
    
    // Set rate limit headers
    res.setHeader('X-RateLimit-Limit', config.limit);
    res.setHeader('X-RateLimit-Remaining', Math.max(0, config.limit - current));
    res.setHeader('X-RateLimit-Reset', Date.now() + config.window * 1000);
    
    if (current > config.limit) {
      return res.status(429).json({
        error: {
          code: 'RATE_LIMITED',
          message: 'Too many requests. Please try again later.',
        },
      });
    }
    
    next();
  };
}

function getKey(req: Request): string {
  // Use user ID if authenticated, otherwise IP
  const userId = (req as any).user?.id;
  if (userId) return `user:${userId}`;
  
  const ip = req.ip || req.headers['x-forwarded-for'] || 'unknown';
  return `ip:${ip}`;
}

// Usage with different limits
const apiLimiter = rateLimit(redis, {
  limit: 1000,
  window: 3600, // 1 hour
  keyPrefix: 'rl:api',
});

const authLimiter = rateLimit(redis, {
  limit: 5,
  window: 900, // 15 minutes
  keyPrefix: 'rl:auth',
});

router.use('/api', apiLimiter);
router.use('/api/auth/login', authLimiter);
```

---

## 📊 DATABASE PATTERNS

### Repository Pattern

```typescript
// modules/users/users.repository.ts
import { Injectable } from '@nestjs/common';
import { PrismaService } from '@/database/prisma.service';
import { User, Prisma } from '@prisma/client';

@Injectable()
export class UsersRepository {
  constructor(private prisma: PrismaService) {}
  
  async findById(id: string): Promise<User | null> {
    return this.prisma.user.findUnique({
      where: { id },
    });
  }
  
  async findByEmail(email: string): Promise<User | null> {
    return this.prisma.user.findUnique({
      where: { email: email.toLowerCase() },
    });
  }
  
  async findMany(params: {
    skip?: number;
    take?: number;
    cursor?: Prisma.UserWhereUniqueInput;
    where?: Prisma.UserWhereInput;
    orderBy?: Prisma.UserOrderByWithRelationInput;
  }): Promise<{ users: User[]; total: number }> {
    const [users, total] = await this.prisma.$transaction([
      this.prisma.user.findMany(params),
      this.prisma.user.count({ where: params.where }),
    ]);
    
    return { users, total };
  }
  
  async create(data: Prisma.UserCreateInput): Promise<User> {
    return this.prisma.user.create({ data });
  }
  
  async update(id: string, data: Prisma.UserUpdateInput): Promise<User> {
    return this.prisma.user.update({
      where: { id },
      data,
    });
  }
  
  async delete(id: string): Promise<void> {
    await this.prisma.user.delete({ where: { id } });
  }
}
```

### Transaction Pattern

```typescript
// When multiple operations must succeed together
async transferCredits(fromUserId: string, toUserId: string, amount: number) {
  return this.prisma.$transaction(async (tx) => {
    // Check sender balance
    const sender = await tx.user.findUnique({
      where: { id: fromUserId },
    });
    
    if (!sender || sender.credits < amount) {
      throw new BadRequestException('Insufficient credits');
    }
    
    // Deduct from sender
    await tx.user.update({
      where: { id: fromUserId },
      data: { credits: { decrement: amount } },
    });
    
    // Add to recipient
    await tx.user.update({
      where: { id: toUserId },
      data: { credits: { increment: amount } },
    });
    
    // Create transfer record
    return tx.transfer.create({
      data: {
        fromUserId,
        toUserId,
        amount,
      },
    });
  });
}
```

---

## 📝 LOGGING

### Structured Logging

```typescript
// common/utils/logger.ts
import pino from 'pino';

export const logger = pino({
  level: process.env.LOG_LEVEL || 'info',
  transport: process.env.NODE_ENV === 'development' ? {
    target: 'pino-pretty',
    options: {
      colorize: true,
    },
  } : undefined,
  formatters: {
    level: (label) => ({ level: label }),
  },
  base: {
    service: process.env.SERVICE_NAME || 'api',
    environment: process.env.NODE_ENV,
  },
});

// Create child logger with request context
export function createRequestLogger(req: Request) {
  return logger.child({
    requestId: req.id,
    userId: (req as any).user?.id,
    method: req.method,
    path: req.path,
  });
}

// Usage
app.use((req, res, next) => {
  req.log = createRequestLogger(req);
  next();
});

// In service
this.logger.info({ userId, action: 'login' }, 'User logged in');
this.logger.error({ error, userId }, 'Failed to process payment');
```

---

## ✅ BACKEND QUALITY CHECKLIST

Before marking backend complete:

### API
- [ ] All endpoints implemented per API spec
- [ ] All endpoints validate input
- [ ] All endpoints handle authentication
- [ ] All endpoints check authorization
- [ ] All endpoints return correct status codes
- [ ] All error responses follow standard format
- [ ] Rate limiting implemented
- [ ] Pagination on list endpoints

### Security
- [ ] Passwords hashed with Argon2id/bcrypt
- [ ] JWT tokens short-lived (15 min)
- [ ] Refresh token rotation implemented
- [ ] All inputs validated and sanitized
- [ ] SQL injection impossible
- [ ] Secrets in environment variables
- [ ] Security headers configured
- [ ] CORS configured properly

### Database
- [ ] Schema matches design
- [ ] Migrations created
- [ ] Indexes on query columns
- [ ] Transactions for multi-step operations
- [ ] No N+1 queries

### Code Quality
- [ ] TypeScript strict mode
- [ ] No any types (or justified)
- [ ] Error handling everywhere
- [ ] Logging in key operations
- [ ] Tests written (> 80% coverage)

### Performance
- [ ] Response time < 200ms (P95)
- [ ] Connection pooling configured
- [ ] Caching where appropriate
- [ ] Queries optimized

---

**Reference this document when building any backend code.**
