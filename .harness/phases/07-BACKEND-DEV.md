# 🔧 PHASE 07: BACKEND DEVELOPMENT

> **Build the server-side of the application. API, database, business logic.**

---

## 🎯 PURPOSE

Implement the complete backend system:
- Database schema and migrations
- API endpoints per contract
- Business logic
- Authentication and authorization
- Integrations with external services

**Time Investment**: 8-24 hours (depending on complexity)
**Skip Risk**: N/A - This is a core development phase

---

## 📥 INPUTS REQUIRED

1. API Contract (Phase 06)
   - OpenAPI specification
   - Type definitions
   - Validation rules
2. Architecture Document (Phase 03)
3. Data Model

---

## 📤 EXPECTED OUTPUTS

1. **Working API**
   - All endpoints functional
   - Authentication working
   - Authorization enforced

2. **Database**
   - Schema implemented
   - Migrations created
   - Seed data for development

3. **Tests**
   - Unit tests for business logic
   - Integration tests for API

---

## 🔄 PROCESS

### Step 1: Project Setup

**Initialize Project:**
- Create project with appropriate framework
- Configure linting and formatting
- Set up testing framework
- Configure environment variables
- Set up database connection

**Directory Structure:**
```
src/
├── config/           # Configuration management
├── modules/          # Feature modules
│   ├── auth/
│   ├── users/
│   └── [feature]/
├── common/           # Shared code
│   ├── middleware/
│   ├── guards/
│   ├── utils/
│   └── exceptions/
├── database/         # Database schema, migrations, seeds
└── types/           # Type definitions
```

### Step 2: Database Implementation

**Execute in Order:**

1. **Create Schema**
   - Implement all tables from data model
   - Define all relationships
   - Add appropriate indexes
   - Add constraints (unique, check, etc.)

2. **Create Migrations**
   - One migration per logical change
   - Reversible (up and down)
   - Version controlled

3. **Seed Data**
   - Development seed data
   - Test seed data
   - Admin user for development

**Reference:** `.harness/knowledge/DATABASE_MASTERY.md`

### Step 3: Authentication Implementation

**Implement in Order:**

1. **User Model**
   - Email, hashed password
   - Email verification status
   - Timestamps
   - Profile fields

2. **Password Hashing**
   - Use Argon2id or bcrypt
   - High work factor

3. **Registration**
   - Validate input
   - Check email uniqueness
   - Create user
   - Generate verification token
   - Send verification email
   - Return success (don't auto-login for security)

4. **Email Verification**
   - Verify token
   - Mark email verified
   - Allow resend (rate limited)

5. **Login**
   - Validate credentials
   - Check email verified (if required)
   - Generate access token (short-lived: 15 min)
   - Generate refresh token (longer: 7 days)
   - Store refresh token hash
   - Return tokens

6. **Token Refresh**
   - Validate refresh token
   - Check not revoked
   - Generate new tokens
   - Rotate refresh token
   - Invalidate old refresh token

7. **Logout**
   - Revoke refresh token
   - Client deletes tokens

8. **Password Reset**
   - Request: Generate token, send email
   - Reset: Validate token, update password, invalidate sessions
   - Rate limit requests

9. **OAuth (if needed)**
   - Configure providers (Google, GitHub, etc.)
   - Handle callback
   - Create or link account
   - Generate tokens

**Reference:** `.harness/knowledge/BACKEND_MASTERY.md` - Authentication section

### Step 4: Authorization Implementation

1. **Define Roles**
   - Admin, User, etc.
   - Permissions per role

2. **Middleware/Guards**
   - Authentication check (is user logged in?)
   - Role check (has required role?)
   - Resource ownership check (owns this resource?)

3. **Apply to Routes**
   - All protected routes require auth
   - Admin routes require admin role
   - Resource routes check ownership

**Reference:** `.harness/knowledge/BACKEND_MASTERY.md` - Authorization section

### Step 5: Core Features Implementation

**For Each Feature Module:**

1. **Data Layer**
   - Repository with CRUD operations
   - Query methods needed by business logic
   - Pagination support

2. **Business Logic**
   - Service layer with business rules
   - Input validation
   - Error handling
   - Event emission (if needed)

3. **API Layer**
   - Controller with route handlers
   - Request validation
   - Response formatting
   - Error responses

4. **Tests**
   - Unit tests for service
   - Integration tests for API

**Implementation Order:**
- Implement features in dependency order
- Core features first
- Optional features last

### Step 6: Input Validation

**For Every Endpoint:**

1. **Define validation schema**
   - Required fields
   - Type checking
   - Format validation (email, URL, etc.)
   - Length/range limits
   - Custom business rules

2. **Apply validation**
   - Validate at route entry point
   - Return all errors at once
   - Consistent error format

**Reference:** `.harness/knowledge/BACKEND_MASTERY.md` - Input Validation section

### Step 7: Error Handling

1. **Standard Error Responses**
   - Consistent error format
   - Appropriate HTTP status codes
   - Human-readable messages
   - No stack traces in production

2. **Global Error Handler**
   - Catch unhandled errors
   - Log with context
   - Return generic error to client

3. **Specific Error Handling**
   - Validation errors (400)
   - Authentication errors (401)
   - Authorization errors (403)
   - Not found errors (404)
   - Conflict errors (409)
   - Server errors (500)

**Reference:** `.harness/knowledge/BACKEND_MASTERY.md` - Error Handling section

### Step 8: Logging Implementation

1. **Structured Logging**
   - JSON format
   - Timestamp
   - Level
   - Context (request ID, user ID, etc.)

2. **Log All:**
   - Requests (duration, status)
   - Errors (with context)
   - Authentication events
   - Business-critical events

3. **Never Log:**
   - Passwords
   - Tokens
   - Sensitive personal data

**Reference:** `.harness/knowledge/BACKEND_MASTERY.md` - Logging section

### Step 9: Rate Limiting

1. **Configure Rate Limits**
   - Per endpoint category
   - Per user/IP
   - Stricter for auth endpoints

2. **Implement Rate Limiter**
   - Store counts (Redis or memory)
   - Return appropriate headers
   - Return 429 when exceeded

**Reference:** `.harness/knowledge/BACKEND_MASTERY.md` - Rate Limiting section

### Step 10: External Integrations

**For Each External Service:**

1. **Create Client Wrapper**
   - Encapsulate API calls
   - Handle authentication
   - Implement retry logic
   - Timeout configuration

2. **Error Handling**
   - Handle failure gracefully
   - Don't expose external errors
   - Log failures for debugging

3. **Testing**
   - Mock in unit tests
   - Integration tests with sandbox (if available)

### Step 11: API Documentation

1. **Generate from Code**
   - OpenAPI spec from routes
   - Type definitions
   - Example requests/responses

2. **Interactive Docs**
   - Swagger UI or similar
   - Available in development
   - Optionally in production (authenticated)

---

## ✅ QUALITY GATE

Before proceeding to Phase 08, verify:

### API
- [ ] All endpoints from API contract implemented
- [ ] All endpoints return correct status codes
- [ ] All endpoints validate input
- [ ] All endpoints have error handling
- [ ] Response format matches contract
- [ ] API documentation complete

### Authentication
- [ ] Registration works
- [ ] Login works
- [ ] Logout works
- [ ] Token refresh works
- [ ] Password reset works
- [ ] Email verification works (if applicable)
- [ ] OAuth works (if applicable)

### Authorization
- [ ] All protected routes require authentication
- [ ] Role-based access control works
- [ ] Resource ownership checked
- [ ] Admin endpoints protected

### Database
- [ ] Schema matches design
- [ ] Migrations exist and work
- [ ] Seed data available
- [ ] Indexes on query columns
- [ ] Constraints enforced

### Security
- [ ] Passwords hashed correctly
- [ ] Rate limiting enabled
- [ ] Input validated
- [ ] No SQL injection possible
- [ ] Secrets in environment variables

### Code Quality
- [ ] No linting errors
- [ ] No type errors
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Test coverage adequate

- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

- `.harness/knowledge/BACKEND_MASTERY.md` - Complete backend guide
- `.harness/knowledge/DATABASE_MASTERY.md` - Database design
- `.harness/knowledge/SECURITY_MASTERY.md` - Security implementation
- `.harness/knowledge/TESTING_MASTERY.md` - Testing strategy

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Starting Without API Contract
Backend should implement the contract, not define it on the fly.

### Mistake 2: Skipping Validation
Every input must be validated. No exceptions.

### Mistake 3: Insufficient Error Handling
Every code path needs error handling.

### Mistake 4: Hardcoded Secrets
Never commit secrets. Use environment variables.

### Mistake 5: Missing Authorization
Authentication ≠ Authorization. Check both.

### Mistake 6: No Tests
Writing tests saves time in the long run.

---

## 💡 TIPS

1. **Build incrementally**: One feature at a time, fully tested

2. **Test as you go**: Don't save testing for the end

3. **Log generously**: You'll thank yourself when debugging

4. **Document edge cases**: In code comments and tests

5. **Use the ORM properly**: Don't fight it, learn it

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 08: Frontend Development.**
