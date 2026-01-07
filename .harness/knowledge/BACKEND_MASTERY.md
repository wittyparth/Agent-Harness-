# 🔧 BACKEND ENGINEERING MASTERY

> **Complete knowledge for building production-grade backend systems.**
> **What a 20+ year veteran engineer knows about building APIs and services.**

---

## 🎯 CORE MISSION

The backend is the foundation. Users never see it, but they experience every flaw. Your job is to build systems that are:
- **Secure**: Protect user data, prevent unauthorized access
- **Reliable**: Handle failures gracefully, maintain uptime
- **Performant**: Respond quickly under load
- **Scalable**: Grow with demand without redesign
- **Maintainable**: Easy to understand, debug, and extend

---

## 📋 COMPLETE BACKEND IMPLEMENTATION GUIDE

### PHASE 1: API DESIGN (Before Writing Any Code)

#### 1.1 API Contract First

**Before implementing anything, define the complete API:**
- All endpoints with paths and HTTP methods
- Request body schemas with types and validation rules
- Response schemas for success AND all error cases
- Authentication requirements per endpoint
- Rate limit tiers per endpoint category
- Pagination strategy for list endpoints

**Why this matters**: Frontend and backend can develop in parallel. No surprises during integration. API becomes the contract.

#### 1.2 RESTful Design Principles

**Resource Naming**
- Use nouns, not verbs: `/users` not `/getUsers`
- Use plural: `/users` not `/user`
- Nest for relationships: `/users/{id}/orders`
- Use lowercase with hyphens: `/user-preferences` not `/userPreferences`

**HTTP Methods**
| Method | Purpose | Idempotent | Body |
|--------|---------|------------|------|
| GET | Read resource(s) | Yes | No |
| POST | Create resource | No | Yes |
| PUT | Full update/replace | Yes | Yes |
| PATCH | Partial update | Yes | Yes |
| DELETE | Remove resource | Yes | No |

**HTTP Status Codes**
| Code | When to Use |
|------|-------------|
| 200 | Successful GET, PUT, PATCH, DELETE |
| 201 | Successful POST (resource created) |
| 204 | Successful DELETE (no content to return) |
| 400 | Invalid input (validation failed) |
| 401 | Not authenticated (no valid credentials) |
| 403 | Authenticated but not authorized |
| 404 | Resource not found |
| 409 | Conflict (duplicate resource, state conflict) |
| 422 | Valid syntax but unprocessable (business logic rejected) |
| 429 | Rate limit exceeded |
| 500 | Server error (something unexpected broke) |

#### 1.3 API Versioning

**Version from day one.** Options:
- URL prefix: `/api/v1/users` (recommended for simplicity)
- Header: `Accept-Version: v1`

**Migration strategy**: Support v1 and v2 simultaneously during migration period.

---

### PHASE 2: AUTHENTICATION

#### 2.1 Authentication Methods

**JWT (JSON Web Tokens)**
- Stateless, scalable across servers
- Use for: APIs accessed by web/mobile apps
- Access token: Short-lived (15 minutes)
- Refresh token: Longer-lived (7-30 days), stored securely
- Implement refresh token rotation (new refresh token on each use)
- Maintain revocation list for logout/security events

**Session-Based**
- Server stores session state
- Use for: Traditional web apps, simpler to implement
- Session ID in HttpOnly cookie
- Server-side session store (Redis for distributed systems)
- Add CSRF protection

**API Keys**
- Use for: Service-to-service, third-party integrations
- Hash and store (never store plain text)
- Scope to specific permissions
- Rotate regularly (every 90 days recommendation)
- Monitor for anomalous usage

#### 2.2 Password Security

**Storage**
- NEVER store plain text passwords
- Use Argon2id (preferred) or bcrypt (industry standard)
- Salt is automatic with these algorithms
- Use high work factor (12+ for bcrypt)

**Requirements**
- Minimum 8 characters (recommend 12+)
- Allow long passwords (up to 100+ chars)
- Check against known breached passwords
- Don't require arbitrary complexity rules (proven less effective)

**Password Reset Flow**
1. User requests reset with email
2. Generate cryptographically random token (minimum 32 bytes)
3. Hash token, store with expiration (1 hour max)
4. Send email with reset link containing plain token
5. On reset page: verify token hash exists and not expired
6. Allow password change: enforce password rules
7. Mark token as used (one-time use)
8. Invalidate ALL sessions for the user (security measure)
9. Send confirmation email that password was changed
10. Optionally: notify user of location/device that made change

**Password Reset Security Considerations:**
- Don't reveal if email exists (same message for found/not found)
- Rate limit reset requests (3 per hour per email)
- Token must be single-use
- Short expiration (1 hour maximum)
- Log all reset attempts for security audit
- Alert user if multiple reset attempts

#### 2.3 Email Verification Flow

**Registration with Email Verification:**
1. User registers with email/password
2. Create user in "pending" or "unverified" state
3. Generate verification token (32+ bytes random)
4. Hash token, store with user
5. Send verification email with link containing plain token
6. User clicks link → verify token hash matches
7. Mark email as verified, activate account
8. Allow token refresh if expired (new token, same flow)

**Email Verification Best Practices:**
- Longer expiration than password reset (24-72 hours)
- Allow resend (rate limited: 3 per hour)
- Allow login before verification but limit features
- Re-verify if email changes
- Double opt-in for marketing compliance

#### 2.4 OAuth / Social Login Flows

**OAuth 2.0 Authorization Code Flow (Recommended for Web):**
1. User clicks "Login with Google/GitHub/etc."
2. Redirect to provider's authorization URL with:
   - client_id (your app's ID)
   - redirect_uri (where to return)
   - scope (what data you need)
   - state (CSRF protection, random string, store in session)
   - response_type=code
3. User authenticates with provider
4. Provider redirects back with authorization code + state
5. Verify state matches what you stored (CSRF protection)
6. Exchange code for tokens (server-side, using client_secret):
   - POST to provider's token endpoint
   - Include: code, client_id, client_secret, redirect_uri
   - Receive: access_token, refresh_token (optional), id_token (OIDC)
7. Fetch user profile using access_token
8. Find or create user in your database (see account linking)
9. Create session/JWT for your application

**OAuth Provider-Specific Notes:**

| Provider | Scopes to Request | User ID Field |
|----------|-------------------|---------------|
| Google | openid email profile | sub (from id_token) |
| GitHub | user:email | id |
| Facebook | email public_profile | id |
| Microsoft | openid email profile | sub (from id_token) |
| Apple | email name | sub (from id_token) |

**OAuth Security Requirements:**
- ALWAYS verify state parameter (CSRF protection)
- Exchange code server-side (never expose client_secret)
- Validate id_token signature if using OIDC
- Store provider's user ID (not email) as primary link
- Use HTTPS for all redirect URIs
- Keep client_secret truly secret

#### 2.5 Account Linking

**When User OAuth's with Same Email as Existing Account:**

| Scenario | Recommended Action |
|----------|-------------------|
| Existing password user, new OAuth | Link accounts (same email, verified) OR require login first |
| Existing OAuth user, same provider | Log in (match by provider + provider_user_id) |
| Existing OAuth user, different provider | Link if emails match and verified |
| No existing account | Create new account |

**Account Linking Data Model:**
```
users:
  - id
  - email
  - password_hash (nullable for OAuth-only users)
  - email_verified
  
user_oauth_accounts:
  - user_id (FK to users)
  - provider (google, github, etc.)
  - provider_user_id (unique per provider)
  - access_token (encrypted)
  - refresh_token (encrypted)
  - created_at
  
Unique constraint: (provider, provider_user_id)
```

**Account Linking Security:**
- Only link if email is verified on both sides
- Confirm with user before linking
- Allow unlinking OAuth accounts
- Keep at least one auth method (can't unlink last one)

#### 2.6 Session Security

- Regenerate session ID after login (prevent session fixation)
- Set secure cookie flags: HttpOnly, Secure, SameSite=Strict
- Implement session timeout (absolute and idle)
- Allow users to see/revoke active sessions
- Invalidate all sessions on password change

#### 2.4 Multi-Factor Authentication (MFA)

Implement when security is critical:
- TOTP (Time-based One-Time Password) - most common
- SMS (less secure, but better than none)
- Hardware keys (FIDO2/WebAuthn) - most secure
- Recovery codes (stored securely, one-time use)

---

### PHASE 3: AUTHORIZATION

#### 3.1 Authorization Models

**Role-Based Access Control (RBAC)**
- Users have roles, roles have permissions
- Simple to understand and implement
- Good for: Most applications

**Attribute-Based Access Control (ABAC)**
- Decisions based on user attributes, resource attributes, context
- More flexible, more complex
- Good for: Complex permission requirements

**Resource-Based Authorization**
- Check ownership/relationship to resource
- "Can this user edit THIS document?"
- Always combine with role checks

#### 3.2 Authorization Rules

**Check Authorization on Every Request**
- Frontend checks are for UX only
- Backend must validate independently
- Don't trust frontend-provided role/permission info

**Defense in Depth**
1. Route-level guards (is user authenticated?)
2. Role checks (does user have required role?)
3. Resource checks (does user own/have access to this specific resource?)

**Principle of Least Privilege**
- Grant minimum access needed
- Default to denied
- Require explicit grants

---

### PHASE 4: INPUT VALIDATION

#### 4.1 Validation Strategy

**Validate Everything**
- Never trust client input
- Validate on server even if validated on client
- Validate early (at entry point)

**What to Validate**
- Type: Is it the expected type (string, number, boolean, etc.)?
- Format: Does it match expected format (email, UUID, date)?
- Length/Range: Within acceptable bounds?
- Allowed values: If enum, is it an allowed value?
- Business rules: Does it make sense in context?

**Validation Response**
- Return all validation errors at once (not one at a time)
- Specify which field failed and why
- Use consistent error format:
```
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input",
    "details": [
      {"field": "email", "message": "Invalid email format"},
      {"field": "age", "message": "Must be at least 18"}
    ]
  }
}
```

#### 4.2 Sanitization

**Strip/Normalize**
- Trim whitespace
- Normalize unicode
- Convert consistent case where appropriate

**Escape for Context**
- SQL: Use parameterized queries (never string concatenation)
- HTML: Escape output (handled by templating engines)
- JSON: Use proper serializers

---

### PHASE 5: DATABASE DESIGN & ACCESS

#### 5.1 Schema Design Principles

**Normalization**
- Start with 3rd Normal Form (no redundancy)
- Denormalize only for proven performance needs
- Document why when you denormalize

**Primary Keys**
- Use UUIDs for public-facing IDs (prevent enumeration)
- Use auto-increment integers for internal relations (smaller, faster)
- Never expose internal IDs externally

**Standard Fields on Every Table**
- `id`: Primary key
- `created_at`: When created
- `updated_at`: When last modified
- `deleted_at`: For soft deletes (if used)

**Soft Deletes vs Hard Deletes**
- Soft delete: Set deleted_at, preserve data
- Use when: Data recovery needed, audit trail, foreign key dependencies
- Hard delete: Actually remove from database
- Use when: Privacy compliance (GDPR), storage concerns, truly unnecessary

#### 5.2 Index Strategy

**When to Add Index**
- Columns used in WHERE clauses
- Columns used in JOIN conditions
- Columns used in ORDER BY
- Unique constraints

**When NOT to Add Index**
- Low-cardinality columns (few distinct values)
- Tables with very few rows
- Columns rarely queried
- Write-heavy tables (indexes slow writes)

**Composite Index Rules**
- Column order matters (leftmost prefix rule)
- Put equality conditions before range conditions
- Include all columns used in WHERE for covering index

#### 5.3 Query Optimization

**Avoid N+1 Queries**
- For each item in list, don't make separate query
- Use eager loading/joins to fetch related data
- Batch operations when possible

**Pagination**
- Offset/limit: Simple but slow for deep pages
- Cursor-based: More complex but consistent performance
- For large datasets, prefer cursor-based

**Connection Pooling**
- Don't create connection per request
- Use connection pool with appropriate size
- Size = (~2 × CPU cores) + disk spindles (rough guideline)

---

### PHASE 6: CACHING

#### 6.1 What to Cache

**Good Cache Candidates**
- Frequently accessed data
- Expensive to compute/fetch
- Rarely changes
- Same for many users

**Poor Cache Candidates**
- Rapidly changing data
- User-specific data (in shared cache)
- Extremely large responses
- Data that must be real-time accurate

#### 6.2 Caching Layers

**Client-Side Cache**
- Browser cache (via HTTP headers)
- Good for: Static assets, rarely-changing API responses

**CDN Cache**
- Edge caching (via Cache-Control headers)
- Good for: Static assets, public API responses

**Application Cache**
- In-memory (local to instance) or distributed (Redis/Memcached)
- Good for: Database query results, computed data, sessions

**Database Query Cache**
- Built into many databases
- Limited control, but useful for repeated exact queries

#### 6.3 Cache Invalidation Strategies

**Time-Based (TTL)**
- Simplest: data expires after N seconds
- Choose TTL based on: acceptable staleness, data change frequency
- Use for: Data that can be slightly stale

**Event-Based (Write-Through/Write-Behind)**
- Invalidate/update cache on data change
- Ensures cache matches database
- Use for: Data that must be fresh

**Cache-Aside Pattern**
- Application checks cache, fetches from DB if miss, populates cache
- Most flexible, most common
- Application controls caching logic

---

### PHASE 7: RATE LIMITING

#### 7.1 Rate Limit Tiers

| Tier | Scope | Example Limit | Purpose |
|------|-------|---------------|---------|
| **Standard** | Per user | 1000 req/hour | Normal API usage |
| **Anonymous** | Per IP | 100 req/hour | Unauthenticated access |
| **Authentication** | Per IP | 5 req/15min | Prevent brute force |
| **Expensive Operations** | Per user | 10 req/hour | Protect heavy endpoints |
| **Upload** | Per user | 100MB/hour | Prevent storage abuse |
| **Search** | Per user | 100 req/min | Protect search infrastructure |

#### 7.2 Implementation Considerations

**Algorithm Choice**
- Token Bucket: Allows burst, smooth rate over time
- Sliding Window: More accurate, slightly more complex
- Fixed Window: Simplest, can have boundary issues

**Response Headers**
```
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 872
X-RateLimit-Reset: 1609459200
Retry-After: 3600 (on 429 response)
```

**Rate Limit by**
- User ID (authenticated requests)
- IP address (fallback, can be spoofed/shared)
- API key (for service accounts)
- Combination (IP + endpoint for auth endpoints)

---

### PHASE 8: ERROR HANDLING

#### 8.1 Error Response Format

Use consistent format across all endpoints:
```
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",      // Machine-readable
    "message": "User not found",        // Human-readable
    "details": { ... }                  // Optional: additional context
  }
}
```

#### 8.2 Error Handling Principles

**For Clients**
- Return appropriate HTTP status codes
- Provide actionable error messages
- Never expose internal details (stack traces, queries, paths)
- Include request ID for support tickets

**For Operations**
- Log all errors with full context
- Structure logs for searchability
- Include: request ID, user ID, endpoint, timestamp, stack trace
- Mask sensitive data in logs

**Error Categories**
| Type | Status | How to Handle |
|------|--------|---------------|
| Validation Error | 400 | Return all field errors |
| Authentication Error | 401 | Clear message, don't reveal if user exists |
| Authorization Error | 403 | Clear message about what's not allowed |
| Not Found | 404 | Generic "not found" (don't reveal existence) |
| Conflict | 409 | Explain what conflicted |
| Server Error | 500 | Generic message, log full details |

---

### PHASE 9: LOGGING & OBSERVABILITY

#### 9.1 Logging Requirements

**What to Log**
- All requests (method, path, status, duration)
- All errors (with context)
- Authentication events (login, logout, failures)
- Authorization failures
- Business-critical events (orders, payments, etc.)
- Slow operations (queries, external calls)

**What NOT to Log**
- Passwords (plain or hashed)
- API keys/secrets
- Full credit card numbers
- Personal data (unless required for debugging)
- Health check requests (too noisy)

**Log Format**
- Structured JSON (not plain text)
- Include: timestamp, level, message, request_id, user_id, context
- Consistent field names across services

**Log Levels**
| Level | When to Use |
|-------|-------------|
| ERROR | Operation failed, needs attention |
| WARN | Unexpected but handled, potential issue |
| INFO | Normal operations, key events |
| DEBUG | Detailed info for troubleshooting (not in production) |

#### 9.2 Monitoring Metrics

**RED Method (For Services)**
- **R**ate: Requests per second
- **E**rrors: Failed requests per second
- **D**uration: Time per request (p50, p95, p99)

**USE Method (For Resources)**
- **U**tilization: How much is used (CPU %, memory %)
- **S**aturation: How queued up is work
- **E**rrors: Error count

**Key Metrics to Track**
- Request rate overall and per endpoint
- Error rate overall and by type
- Latency (p50, p95, p99)
- Database query time
- External service call time
- Cache hit rate
- Queue depth (if using queues)

#### 9.3 Distributed Tracing

For multi-service systems:
- Generate request ID at entry point
- Pass through all service calls
- Include in all logs
- Enables end-to-end request tracking

---

### PHASE 10: SECURITY HARDENING

#### 10.1 OWASP Top 10 Protection

| Vulnerability | Prevention |
|--------------|------------|
| **Injection** | Parameterized queries, input validation, ORM |
| **Broken Authentication** | Strong passwords, MFA, secure session management |
| **Sensitive Data Exposure** | Encrypt at rest/transit, minimize data collection |
| **XXE** | Disable external entities in XML parsers |
| **Broken Access Control** | Check authorization on every request |
| **Security Misconfiguration** | Secure defaults, remove debug info in production |
| **XSS** | Output encoding, CSP headers |
| **Insecure Deserialization** | Validate input structure, use safe formats |
| **Using Vulnerable Components** | Keep dependencies updated, scan regularly |
| **Insufficient Logging** | Comprehensive logging and monitoring |

#### 10.2 Security Headers

| Header | Value | Purpose |
|--------|-------|---------|
| Strict-Transport-Security | max-age=31536000; includeSubDomains | Force HTTPS |
| X-Content-Type-Options | nosniff | Prevent MIME sniffing |
| X-Frame-Options | DENY | Prevent clickjacking |
| Content-Security-Policy | script-src 'self' | Control resource sources |
| Referrer-Policy | strict-origin-when-cross-origin | Control referrer info |

#### 10.3 Encryption

**In Transit**
- TLS 1.2 minimum, prefer 1.3
- Valid certificates (Let's Encrypt is free)
- HTTPS only (redirect HTTP)

**At Rest**
- Database-level encryption
- Encrypt individual sensitive fields
- Encrypt file storage

**Secrets Management**
- Never commit secrets to code
- Use environment variables or secret manager
- Rotate secrets regularly
- Different secrets per environment

---

### PHASE 11: BACKGROUND JOBS & QUEUES

#### 11.1 When to Use Background Jobs

- Sending emails/notifications
- Processing uploads
- Generating reports
- Calling slow external APIs
- Any operation > 2 seconds

#### 11.2 Queue Patterns

**At-Least-Once Delivery**
- Default for most queues
- Job may run multiple times
- Make operations idempotent

**Idempotency**
- Running job twice produces same result as once
- Use idempotency keys for external operations
- Check if already processed before processing

**Retry Strategy**
- Exponential backoff (double wait time each retry)
- Maximum retry count (3-5 typically)
- Dead letter queue for failed jobs
- Alert on dead letter queue growth

---

### PHASE 12: EXTERNAL INTEGRATIONS

#### 12.1 Calling External APIs

**Resilience**
- Set timeouts (connect: 5s, read: 30s typical)
- Implement retry with backoff (for idempotent calls)
- Circuit breaker for persistent failures
- Fallback behavior when service unavailable

**Security**
- Store API keys securely
- Use least privilege tokens
- Validate response data (don't trust external sources)

**Logging**
- Log all external calls (URL, status, duration)
- Mask sensitive data in logs
- Track failure rates

#### 12.2 Webhooks (Receiving)

**Verification**
- Validate signature if provided
- Verify IP allowlist if applicable
- Check timestamp to prevent replay

**Processing**
- Respond quickly (2-5 seconds max)
- Process in background job
- Make processing idempotent (webhooks may repeat)
- Acknowledge receipt, process async

---

## ✅ BACKEND QUALITY CHECKLIST

Before marking backend complete:

### API
- [ ] All endpoints implemented per API contract
- [ ] Request validation on all inputs
- [ ] Consistent response format
- [ ] Proper HTTP status codes
- [ ] API documentation complete and accurate
- [ ] Versioning in place

### Authentication & Authorization
- [ ] Authentication working for all protected routes
- [ ] Password hashing with Argon2id/bcrypt
- [ ] Token expiration and refresh working
- [ ] Authorization checked on every request
- [ ] Resource ownership verified
- [ ] Session/token revocation possible

### Security
- [ ] SQL injection impossible (parameterized queries)
- [ ] All inputs validated
- [ ] Secrets in environment variables
- [ ] HTTPS enforced
- [ ] Security headers configured
- [ ] Rate limiting active
- [ ] Audit logging enabled

### Database
- [ ] Schema migrations versioned
- [ ] Indexes on query columns
- [ ] No N+1 queries
- [ ] Connection pooling configured
- [ ] Backup strategy in place

### Reliability
- [ ] Error handling on all paths
- [ ] Graceful error responses
- [ ] Health check endpoint
- [ ] Logging comprehensive
- [ ] Monitoring in place

### Performance
- [ ] Response times within target (p95 < 200ms)
- [ ] Database queries optimized
- [ ] Caching where appropriate
- [ ] Load tested

---

## 💡 HARD-LEARNED LESSONS

1. **Never trust client input**: Validate everything on the server, even if validated on client.

2. **Authentication ≠ Authorization**: Being logged in doesn't mean allowed to do everything.

3. **Every endpoint can be called directly**: Frontend hiding a button doesn't prevent API call.

4. **Logging saves days of debugging**: Log comprehensively, you'll thank yourself.

5. **Idempotency prevents disasters**: Networks fail, retries happen, design for it.

6. **Databases are the bottleneck**: Most performance issues are database-related.

7. **Caching is hard**: Invalidation bugs are worse than no caching at all.

8. **Rate limiting is mandatory**: Without it, one client can take down your service.

9. **Background jobs need monitoring**: Silent failures are the worst kind.

10. **Security is not optional**: One breach can destroy everything you've built.

---

**Apply this knowledge to every backend decision.**
