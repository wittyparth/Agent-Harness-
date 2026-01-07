# 📐 PHASE 06: API CONTRACT

> **Define ALL APIs before writing a single line of code. This is how you prevent frontend/backend sync issues.**

---

## 🎯 PURPOSE

This is the **most critical phase for preventing integration problems**:
- Define every API endpoint with complete specifications
- Create OpenAPI/Swagger specification
- Define request/response schemas
- Generate TypeScript types for both frontend and backend
- Establish the contract that both sides implement to

**Time Investment**: 2-4 hours
**Skip Risk**: Frontend and backend out of sync, integration nightmares

---

## 📥 INPUTS REQUIRED

1. Requirements Document (Phase 02)
2. Architecture Document (Phase 03)
3. UX/UI Design Documents (Phase 04-05)
4. Data Model

---

## 📤 EXPECTED OUTPUTS

1. **OpenAPI Specification** (`.harness/sync/API_SPEC.yaml`)
   - All endpoints defined
   - Request/response schemas
   - Authentication requirements
   - Error responses

2. **Types Document** (`.harness/sync/TYPES.md`)
   - All shared types
   - TypeScript definitions

3. **Contracts Document** (`.harness/sync/CONTRACTS.md`)
   - Data validation rules
   - Business logic constraints

---

## 🔄 PROCESS

### Step 1: Inventory All API Needs

From requirements and UI flows, list every API call needed:

```markdown
## API INVENTORY

### Authentication
- [ ] POST /api/auth/register
- [ ] POST /api/auth/login
- [ ] POST /api/auth/logout
- [ ] POST /api/auth/refresh
- [ ] POST /api/auth/forgot-password
- [ ] POST /api/auth/reset-password

### Users
- [ ] GET /api/users/me
- [ ] PATCH /api/users/me
- [ ] DELETE /api/users/me

### [Resource 1]
- [ ] GET /api/[resources]
- [ ] POST /api/[resources]
- [ ] GET /api/[resources]/:id
- [ ] PATCH /api/[resources]/:id
- [ ] DELETE /api/[resources]/:id

### [Continue for all resources...]
```

### Step 2: Define Each Endpoint

For EVERY endpoint, specify:

```markdown
## ENDPOINT SPECIFICATION TEMPLATE

### [METHOD] [PATH]
**Summary**: [What it does in one sentence]
**Auth Required**: Yes/No
**Roles Allowed**: [All authenticated / Admin only / etc.]

#### Request
**Headers**:
```
Authorization: Bearer <token> (if auth required)
Content-Type: application/json
```

**Path Parameters**: (if any)
| Name | Type | Required | Description |
|------|------|----------|-------------|
| id | string (UUID) | Yes | Resource ID |

**Query Parameters**: (if any)
| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| page | number | No | 1 | Page number |
| limit | number | No | 20 | Items per page |
| sort | string | No | -createdAt | Sort field |

**Request Body**: (if POST/PUT/PATCH)
```json
{
  "field1": "string (required, 1-100 chars)",
  "field2": "number (optional, min: 0)",
  "field3": "boolean (optional, default: false)"
}
```

#### Response

**Success (200/201)**:
```json
{
  "data": {
    "id": "uuid",
    "field1": "string",
    "field2": 123,
    "createdAt": "2024-01-01T00:00:00Z"
  },
  "meta": {
    "timestamp": "2024-01-01T00:00:00Z"
  }
}
```

**Error Responses**:
| Code | When | Body |
|------|------|------|
| 400 | Invalid input | `{ "error": { "code": "VALIDATION_ERROR", "message": "...", "details": [...] }}` |
| 401 | Not authenticated | `{ "error": { "code": "UNAUTHORIZED", "message": "..." }}` |
| 403 | Not authorized | `{ "error": { "code": "FORBIDDEN", "message": "..." }}` |
| 404 | Not found | `{ "error": { "code": "NOT_FOUND", "message": "..." }}` |
| 429 | Rate limited | `{ "error": { "code": "RATE_LIMITED", "message": "..." }}` |

#### Example
```bash
curl -X POST https://api.example.com/api/resources \
  -H "Authorization: Bearer eyJ..." \
  -H "Content-Type: application/json" \
  -d '{"field1": "value"}'
```
```

### Step 3: Create OpenAPI Specification

Create the complete OpenAPI 3.0 spec:

```yaml
# .harness/sync/API_SPEC.yaml

openapi: 3.0.3
info:
  title: [Project Name] API
  version: 1.0.0
  description: API specification for [Project Name]

servers:
  - url: http://localhost:3000/api
    description: Local development
  - url: https://api.example.com
    description: Production

components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT

  schemas:
    # Common schemas
    Error:
      type: object
      properties:
        error:
          type: object
          properties:
            code:
              type: string
              example: VALIDATION_ERROR
            message:
              type: string
              example: Invalid input
            details:
              type: array
              items:
                type: object

    PaginationMeta:
      type: object
      properties:
        page:
          type: integer
        limit:
          type: integer
        total:
          type: integer
        totalPages:
          type: integer

    # Domain schemas
    User:
      type: object
      properties:
        id:
          type: string
          format: uuid
        email:
          type: string
          format: email
        name:
          type: string
        createdAt:
          type: string
          format: date-time
      required:
        - id
        - email
        - name
        - createdAt

    CreateUserInput:
      type: object
      properties:
        email:
          type: string
          format: email
          minLength: 5
          maxLength: 255
        password:
          type: string
          minLength: 8
          maxLength: 100
        name:
          type: string
          minLength: 1
          maxLength: 100
      required:
        - email
        - password
        - name

    # [Add all other schemas...]

paths:
  /auth/register:
    post:
      summary: Register new user
      tags:
        - Authentication
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/CreateUserInput'
      responses:
        '201':
          description: User created successfully
          content:
            application/json:
              schema:
                type: object
                properties:
                  data:
                    $ref: '#/components/schemas/User'
                  token:
                    type: string
        '400':
          description: Validation error
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '409':
          description: Email already exists
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

  # [Add all other paths...]

security:
  - bearerAuth: []
```

### Step 4: Define TypeScript Types

```markdown
# .harness/sync/TYPES.md

## Shared TypeScript Types

These types are the SOURCE OF TRUTH. Both frontend and backend must use them.

### Entity Types

```typescript
// User
interface User {
  id: string;
  email: string;
  name: string;
  avatarUrl?: string;
  createdAt: string; // ISO 8601
  updatedAt: string;
}

// [Entity 2]
interface [Entity2] {
  // ...
}
```

### API Request Types

```typescript
// Auth
interface RegisterInput {
  email: string;
  password: string;
  name: string;
}

interface LoginInput {
  email: string;
  password: string;
}

// [Resource] CRUD
interface Create[Resource]Input {
  // required fields
}

interface Update[Resource]Input {
  // optional fields
}

interface [Resource]QueryParams {
  page?: number;
  limit?: number;
  sort?: string;
  filter?: {
    // filter options
  };
}
```

### API Response Types

```typescript
// Standard success response
interface ApiResponse<T> {
  data: T;
  meta?: {
    timestamp: string;
  };
}

// Paginated response
interface PaginatedResponse<T> {
  data: T[];
  meta: {
    page: number;
    limit: number;
    total: number;
    totalPages: number;
  };
}

// Error response
interface ApiError {
  error: {
    code: string;
    message: string;
    details?: Array<{
      field: string;
      message: string;
    }>;
  };
}
```

### Enums

```typescript
enum UserRole {
  ADMIN = 'ADMIN',
  USER = 'USER',
}

enum [EntityStatus] {
  // ...
}
```
```

### Step 5: Define Validation Contracts

```markdown
# .harness/sync/CONTRACTS.md

## Data Validation Contracts

These rules must be enforced on BOTH frontend (for UX) and backend (for security).

### User Registration

| Field | Type | Required | Rules |
|-------|------|----------|-------|
| email | string | Yes | Valid email format, max 255 chars, lowercase |
| password | string | Yes | Min 8 chars, max 100, must include: uppercase, lowercase, number |
| name | string | Yes | Min 1 char, max 100, trimmed |

### [Resource] Creation

| Field | Type | Required | Rules |
|-------|------|----------|-------|
| ... | ... | ... | ... |

## Business Logic Constraints

### User
- Email must be unique (case-insensitive)
- Cannot delete self if only admin

### [Resource]
- [Constraint 1]
- [Constraint 2]

## Rate Limits

| Endpoint | Limit | Window |
|----------|-------|--------|
| POST /auth/login | 5 | 15 minutes |
| POST /auth/register | 3 | 1 hour |
| POST /auth/forgot-password | 3 | 1 hour |
| All other endpoints | 1000 | 1 hour |
```

### Step 6: Generate Documentation

The OpenAPI spec can generate:
- Interactive API docs (Swagger UI)
- API client code
- Server stubs
- TypeScript types (with openapi-typescript)

```markdown
## API Documentation Generation

### From OpenAPI Spec:

1. **Swagger UI** (interactive docs)
   - Host at /api/docs
   - Use swagger-ui-express or similar

2. **TypeScript Types**
   ```bash
   npx openapi-typescript .harness/sync/API_SPEC.yaml -o src/types/api.d.ts
   ```

3. **API Client** (optional)
   - Generate with openapi-generator
   - Or write custom client using types
```

---

## ✅ QUALITY GATE

Before proceeding to Phase 07, verify:

- [ ] Every required API endpoint is defined
- [ ] All endpoints have complete request/response specs
- [ ] OpenAPI specification is valid (use validator)
- [ ] TypeScript types defined for all entities
- [ ] Validation rules documented
- [ ] Error responses standardized
- [ ] Authentication requirements specified per endpoint
- [ ] Rate limits defined
- [ ] Pagination patterns defined for list endpoints
- [ ] User has reviewed API design
- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

- `.harness/knowledge/BACKEND_MASTERY.md` - API design patterns

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Incomplete Specs
"I'll figure out the response format when I build it."
No. Define it now. Saves hours of integration debugging.

### Mistake 2: Inconsistent Naming
- Use consistent naming: camelCase for JSON, kebab-case for URLs
- Use consistent response structures

### Mistake 3: Missing Error Cases
Define ALL possible error responses.
What happens on 404? On validation error? On auth failure?

### Mistake 4: Skipping Pagination
Any endpoint that returns a list MUST be paginated.
Otherwise it will fail at scale.

### Mistake 5: Ignoring Versioning
Plan for API versions even if v1 only.
Makes future changes manageable.

---

## 💡 TIPS

### Tip 1: Design for the Frontend
Write the API that makes frontend development easy.
Not the API that's easiest to implement on backend.

### Tip 2: Be Consistent
Pick conventions and stick to them:
- Always use `data` wrapper for responses
- Always return ISO 8601 dates
- Always use same error format

### Tip 3: Include Examples
In OpenAPI spec, include realistic examples.
Makes documentation more useful.

### Tip 4: Plan for Expansion
Use plural resource names (/users not /user).
Use nested routes for relationships (/users/:id/posts).

### Tip 5: Mock First
Use OpenAPI to generate mock server.
Frontend can start work immediately.

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 07: Backend Development.**
