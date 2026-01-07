# 📝 TYPES DEFINITION

> **Shared type definitions between frontend and backend.**
> **This is the single source of truth for data shapes.**

---

## ⚠️ IMPORTANT

This file defines ALL types shared between frontend and backend.
Both sides MUST use these exact definitions.

**Updates to this file require:**
1. Update this document
2. Update backend types
3. Update frontend types
4. Update API contract
5. Verify integration

---

## 📋 Template

When creating types for your project, follow this structure:

```typescript
// =========================================
// 🔐 AUTH TYPES
// =========================================

/**
 * User object returned from API
 */
interface User {
  id: string;                    // UUID
  email: string;
  emailVerified: boolean;
  name: string | null;
  avatarUrl: string | null;
  role: UserRole;
  createdAt: string;             // ISO 8601 date string
  updatedAt: string;             // ISO 8601 date string
}

type UserRole = 'user' | 'admin';

/**
 * Registration request body
 */
interface RegisterRequest {
  email: string;                 // Valid email format
  password: string;              // 8+ characters
  name: string;                  // 1-100 characters
}

/**
 * Registration response
 */
interface RegisterResponse {
  user: User;
  message: string;               // "Verification email sent"
}

/**
 * Login request body
 */
interface LoginRequest {
  email: string;
  password: string;
}

/**
 * Auth tokens response
 */
interface AuthTokens {
  accessToken: string;
  refreshToken: string;
  expiresIn: number;            // Seconds until access token expires
}

/**
 * Login response
 */
interface LoginResponse {
  user: User;
  tokens: AuthTokens;
}

/**
 * Password reset request
 */
interface PasswordResetRequest {
  email: string;
}

/**
 * Password reset confirmation
 */
interface PasswordResetConfirm {
  token: string;
  newPassword: string;
}

// =========================================
// 📦 RESOURCE TYPES (Example)
// =========================================

/**
 * Example resource
 */
interface Resource {
  id: string;
  name: string;
  description: string | null;
  status: ResourceStatus;
  ownerId: string;
  createdAt: string;
  updatedAt: string;
}

type ResourceStatus = 'draft' | 'active' | 'archived';

/**
 * Create resource request
 */
interface CreateResourceRequest {
  name: string;                  // 1-100 characters
  description?: string;          // Optional, max 1000 characters
  status?: ResourceStatus;       // Defaults to 'draft'
}

/**
 * Update resource request (partial)
 */
interface UpdateResourceRequest {
  name?: string;
  description?: string;
  status?: ResourceStatus;
}

// =========================================
// 📄 PAGINATION
// =========================================

interface PaginationParams {
  page?: number;                 // 1-indexed, default 1
  limit?: number;                // Default 20, max 100
  sortBy?: string;               // Field to sort by
  sortOrder?: 'asc' | 'desc';    // Default 'desc'
}

interface PaginatedResponse<T> {
  data: T[];
  meta: {
    total: number;
    page: number;
    limit: number;
    totalPages: number;
    hasNextPage: boolean;
    hasPrevPage: boolean;
  };
}

// =========================================
// ❌ ERROR TYPES
// =========================================

interface ApiError {
  error: {
    code: string;                // Machine-readable error code
    message: string;             // Human-readable message
    details?: ValidationError[]; // Field-level errors
  };
}

interface ValidationError {
  field: string;
  message: string;
}

// Common error codes
type ErrorCode =
  | 'VALIDATION_ERROR'
  | 'UNAUTHORIZED'
  | 'FORBIDDEN'
  | 'NOT_FOUND'
  | 'CONFLICT'
  | 'RATE_LIMIT_EXCEEDED'
  | 'INTERNAL_ERROR';
```

---

## 📋 Type Conventions

### Field Naming
- Use camelCase for all field names
- Boolean fields: `is*`, `has*`, `can*`
- Dates: `*At` (createdAt, updatedAt, deletedAt)
- IDs: `*Id` or just `id`

### Date Handling
- All dates as ISO 8601 strings in API responses
- Frontend parses to Date objects if needed
- Backend uses native date types internally

### Optional Fields
- Use `?` for optional fields in requests
- Use `| null` for nullable fields in responses
- Never use `undefined` in responses

### IDs
- Use UUIDs for all public-facing IDs
- String type (not separate UUID type)

---

## 📋 Adding New Types

When adding a new resource type:

1. Define the main interface
2. Define create request type
3. Define update request type
4. Define query/filter params type
5. Add to API contract
6. Update this document
7. Update frontend/backend implementations

---

**Keep this file synchronized with actual implementations.**
