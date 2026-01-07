# 🔒 SECURITY MASTERY

> **Complete knowledge for building secure production applications.**
> **What a 20+ year veteran security engineer knows about protecting systems.**

---

## 🎯 CORE MISSION

Security is not a feature—it's a foundation. One breach can destroy a business. Your job is to build systems that:
- **Prevent unauthorized access**: Only right people access right things
- **Protect data**: Sensitive information stays confidential
- **Maintain integrity**: Data can't be tampered with undetected
- **Ensure availability**: System resists denial of service
- **Enable recovery**: Can recover from incidents

---

## 📋 COMPLETE SECURITY IMPLEMENTATION GUIDE

### PHASE 1: OWASP TOP 10 PROTECTION

Every application must address these most critical vulnerabilities:

#### 1.1 Injection (SQL, NoSQL, OS, LDAP)

**What It Is:** Attacker input is interpreted as code/commands.

**Prevention:**
- Use parameterized queries / prepared statements (NEVER string concatenation)
- Use ORM/query builders (with parameterization)
- Escape special characters for the specific interpreter
- Validate input against strict schemas
- Least privilege database accounts

**Verification:**
- Code review for dynamic query construction
- Automated scanning (SAST tools)
- Penetration testing

#### 1.2 Broken Authentication

**What It Is:** Flaws in login, session, and identity management.

**Prevention:**
- Strong password requirements (length > complexity)
- Multi-factor authentication for critical apps
- Rate limit login attempts (5 attempts / 15 minutes)
- Account lockout after repeated failures
- Secure password reset flow (see Backend Mastery)
- Session timeout (idle and absolute)
- Secure cookie flags (HttpOnly, Secure, SameSite)
- Regenerate session on login

**Verification:**
- Test with credential stuffing
- Test account lockout
- Test session management

#### 1.3 Sensitive Data Exposure

**What It Is:** Sensitive data exposed due to lack of protection.

**Prevention:**
- Identify and classify sensitive data
- Encrypt in transit (TLS 1.2+ everywhere)
- Encrypt at rest (database encryption, field-level for PII)
- Don't store sensitive data unless necessary
- Mask/truncate in logs and displays
- Secure key management
- Purge data when no longer needed

**Types of Sensitive Data:**
- Passwords (never store plain text)
- Personal Identifiable Information (PII)
- Financial data (credit cards, bank accounts)
- Health information
- Authentication tokens
- API keys

#### 1.4 XML External Entities (XXE)

**What It Is:** XML parsers processing malicious external entity references.

**Prevention:**
- Disable external entity processing in XML parsers
- Use JSON instead of XML when possible
- Validate and sanitize XML input
- Update XML libraries regularly

#### 1.5 Broken Access Control

**What It Is:** Users can access resources/actions they shouldn't.

**Prevention:**
- Check authorization on EVERY request (server-side)
- Default deny (require explicit grants)
- Use role-based or attribute-based access control
- Verify resource ownership
- Don't rely on frontend hiding elements
- Log access control failures
- Rate limit to prevent enumeration

**Common Mistakes:**
- Checking if user is logged in but not if they own the resource
- Trusting user-provided IDs without verification
- Only hiding UI elements instead of enforcing server-side

#### 1.6 Security Misconfiguration

**What It Is:** Insecure default settings, incomplete configuration.

**Prevention:**
- Disable debug mode in production
- Remove default accounts/passwords
- Remove unused features/frameworks/ports
- Configure security headers (see below)
- Keep software updated
- Automate security configuration
- Different credentials per environment
- Regular security audits

#### 1.7 Cross-Site Scripting (XSS)

**What It Is:** Malicious scripts injected into pages viewed by others.

**Types:**
- Reflected: Input reflected back immediately
- Stored: Input stored and displayed later
- DOM-based: Client-side script manipulation

**Prevention:**
- Encode output based on context (HTML, JS, CSS, URL)
- Use auto-escaping template engines
- Content Security Policy headers
- Sanitize HTML if you must accept it (use proven libraries)
- Never use innerHTML with user content
- Validate input (but don't rely solely on it)

#### 1.8 Insecure Deserialization

**What It Is:** Untrusted data deserialized into dangerous operations.

**Prevention:**
- Avoid serializing/deserializing untrusted data
- Use simple data formats (JSON) over native serialization
- Implement integrity checks (signatures)
- Enforce strict type constraints
- Log deserialization exceptions
- Run deserialization in isolated environments

#### 1.9 Using Components with Known Vulnerabilities

**What It Is:** Using libraries/frameworks with known security flaws.

**Prevention:**
- Inventory all dependencies (direct and transitive)
- Monitor for vulnerabilities (Dependabot, Snyk, etc.)
- Update regularly (at least monthly review)
- Remove unused dependencies
- Prefer well-maintained libraries
- Subscribe to security advisories

**Tools:**
- npm audit / yarn audit
- pip-audit
- OWASP Dependency-Check
- Snyk, Dependabot, Renovate

#### 1.10 Insufficient Logging & Monitoring

**What It Is:** Attacks go undetected due to lack of visibility.

**Prevention:**
- Log all authentication events (success and failure)
- Log access control failures
- Log input validation failures
- Log exceptions and errors
- Structured logging with context
- Centralized log aggregation
- Real-time alerting
- Regular log review
- Incident response plan

---

### PHASE 2: SECURE HEADERS

#### 2.1 Essential Security Headers

| Header | Value | Purpose |
|--------|-------|---------|
| `Strict-Transport-Security` | `max-age=31536000; includeSubDomains; preload` | Force HTTPS |
| `X-Content-Type-Options` | `nosniff` | Prevent MIME sniffing |
| `X-Frame-Options` | `DENY` or `SAMEORIGIN` | Prevent clickjacking |
| `X-XSS-Protection` | `0` (disable) | Use CSP instead |
| `Referrer-Policy` | `strict-origin-when-cross-origin` | Control referrer info |
| `Permissions-Policy` | `geolocation=(), camera=(), microphone=()` | Restrict browser features |

#### 2.2 Content Security Policy (CSP)

**Basic Restrictive CSP:**
```
Content-Security-Policy: 
  default-src 'self';
  script-src 'self';
  style-src 'self';
  img-src 'self' data: https:;
  font-src 'self';
  object-src 'none';
  frame-ancestors 'none';
  base-uri 'self';
  form-action 'self';
```

**CSP Best Practices:**
- Start with restrictive policy
- Test in report-only mode first
- Avoid 'unsafe-inline' unless nonce/hash used
- Avoid 'unsafe-eval' (breaks some frameworks)
- Use specific domains, not wildcards
- Monitor reports for violations

#### 2.3 CORS Configuration

**When You Need CORS:**
- API accessed from different domain than served
- Frontend on app.example.com, API on api.example.com

**CORS Best Practices:**
- Whitelist specific origins (not *)
- Limit allowed methods
- Limit allowed headers
- Set appropriate max-age for preflight caching
- Credentials require non-wildcard origin

---

### PHASE 3: SECRETS MANAGEMENT

#### 3.1 What Are Secrets

- Database credentials
- API keys (third-party services)
- JWT signing keys
- Encryption keys
- OAuth client secrets
- SSH keys
- TLS certificates/private keys

#### 3.2 Secrets Management Rules

**Never:**
- Commit to version control
- Log secrets
- Put in URLs
- Share in plain text
- Use same secret across environments
- Hardcode in application code

**Always:**
- Use environment variables or secret manager
- Rotate regularly (90 days for most, less for critical)
- Use least privilege (specific scope)
- Audit secret access
- Encrypt at rest
- Limit who can access

#### 3.3 Secret Storage Options

| Method | Use When | Pros | Cons |
|--------|----------|------|------|
| Environment variables | Simple apps, containers | Simple, standard | Can leak in logs/debug |
| Secret manager (AWS, GCP, Vault) | Production, compliance needs | Audit, rotation, encryption | Complexity, cost |
| Encrypted config files | When manager not available | Works anywhere | Key management challenge |
| CI/CD secrets | Build/deploy secrets | Integrated with pipeline | Varies by platform |

---

### PHASE 4: INPUT VALIDATION & OUTPUT ENCODING

#### 4.1 Input Validation Strategy

**Validate Everything:**
- All user input (forms, query params, headers)
- All API inputs
- All file uploads
- All URL parameters
- Webhook payloads
- Imported data

**Validation Approach:**
1. **Type checking**: Is it the expected type?
2. **Format validation**: Does it match pattern (email, phone)?
3. **Range/length**: Within acceptable bounds?
4. **Whitelist**: If fixed set, is it an allowed value?
5. **Business rules**: Does it make sense in context?

**Validation Rules:**
- Validate on server (never trust client)
- Validate as early as possible
- Reject invalid input (don't try to sanitize into valid)
- Return clear error messages
- Log validation failures (potential attack indicators)

#### 4.2 Output Encoding

**Encode Based on Context:**

| Context | Encoding |
|---------|----------|
| HTML body | HTML entity encode |
| HTML attribute | Attribute encode |
| JavaScript | JavaScript encode |
| URL | URL encode |
| CSS | CSS encode |
| SQL | Parameterized queries (not encoding) |

---

### PHASE 5: FILE UPLOAD SECURITY

#### 5.1 File Upload Risks

- Malicious executables
- Scripts (PHP, JSP, etc.)
- Path traversal (../../../etc/passwd)
- Denial of service (huge files)
- File type mismatch (fake extensions)

#### 5.2 File Upload Protection

**Verification:**
- Check file extension (whitelist allowed)
- Check MIME type (don't trust Content-Type header)
- Check magic bytes (actual file content)
- Scan with antivirus for sensitive applications

**Storage:**
- Store outside web root (not directly accessible)
- Generate random filenames (don't use user-provided)
- Avoid path traversal (strip directory separators)
- Store metadata separately from files

**Limits:**
- Maximum file size
- Maximum total storage per user
- Rate limit upload frequency
- Limit file types strictly

**Serving Files:**
- Serve with Content-Disposition: attachment
- Set correct Content-Type
- Use CDN/separate domain for user content
- Re-encode images to strip metadata

---

### PHASE 6: API SECURITY

#### 6.1 API Authentication

- Use standard authentication (OAuth 2.0, JWT)
- API keys for service-to-service (limit scope)
- Rotate credentials regularly
- TLS for all API traffic

#### 6.2 API Rate Limiting

| Endpoint Type | Recommended Limit |
|---------------|-------------------|
| Authentication | 5 req / 15 min |
| Password reset | 3 req / hour |
| General API | 1000 req / hour |
| Expensive operations | 10 req / hour |
| Search/query | 100 req / minute |
| File upload | Size-based limits |

#### 6.3 API Input Validation

- Validate all parameters (path, query, body)
- Type checking with schemas
- Size limits on all inputs
- Reject extra/unknown fields

#### 6.4 API Security Checklist

- [ ] Authentication required for protected endpoints
- [ ] Authorization checked per request
- [ ] Rate limiting enabled
- [ ] Input validation on all inputs
- [ ] TLS required
- [ ] Security headers configured
- [ ] CORS properly configured
- [ ] No sensitive data in URLs
- [ ] Logging enabled

---

### PHASE 7: DATA PROTECTION

#### 7.1 Encryption Standards

**Symmetric Encryption (data at rest):**
- Use: AES-256-GCM
- Avoid: DES, 3DES, AES-ECB

**Hashing (passwords, tokens):**
- Use: Argon2id, bcrypt, scrypt
- Avoid: MD5, SHA1, plain SHA256 for passwords

**Asymmetric Encryption (key exchange, signatures):**
- Use: RSA 2048+, ECDSA P-256+
- Avoid: RSA < 2048

**TLS:**
- Use: TLS 1.2 or 1.3
- Avoid: SSL, TLS 1.0, TLS 1.1

#### 7.2 Data Classification

| Class | Examples | Protection Level |
|-------|----------|------------------|
| Public | Marketing content | None required |
| Internal | Employee directory | Access control |
| Confidential | Business data | Encryption, access control |
| Restricted | PII, financial | Encryption at rest/transit, audit, minimize |

#### 7.3 Data Minimization

- Only collect what you need
- Only keep as long as needed
- Only access when necessary
- Anonymize when possible
- Delete when no longer required
- Document retention policies

---

### PHASE 8: AUDIT LOGGING

#### 8.1 What to Audit Log

**Authentication Events:**
- Login attempts (success and failure)
- Logout
- Password changes
- MFA events
- Account lockouts
- Session creation/destruction

**Authorization Events:**
- Access control failures
- Privilege escalation attempts
- Permission changes

**Data Events:**
- Create/update/delete of sensitive data
- Data exports
- Bulk operations

**Administrative Events:**
- Configuration changes
- User management
- System events

#### 8.2 Audit Log Content

Each log entry should contain:
- Timestamp (UTC, high precision)
- Event type
- User/actor ID
- IP address
- Resource affected
- Action taken
- Outcome (success/failure)
- Request ID (for correlation)

#### 8.3 Audit Log Protection

- Write-only (no modification/deletion)
- Encrypted in transit and at rest
- Separate storage from application data
- Backup and retain per policy
- Tamper detection (hashing/signing)
- Access restricted to security team

---

### PHASE 9: INCIDENT RESPONSE

#### 9.1 Preparation

- Document incident response plan
- Define severity levels
- Establish communication channels
- Identify response team
- Regular drills/tabletop exercises

#### 9.2 Response Process

1. **Detection**: Identify that incident occurred
2. **Containment**: Limit damage (disable accounts, block IPs)
3. **Eradication**: Remove threat (patch, clean up)
4. **Recovery**: Restore normal operations
5. **Lessons Learned**: Document and improve

#### 9.3 Breach Response

- Legal/compliance notification requirements
- User notification obligations
- Preserve evidence
- Document everything
- Post-incident review

---

## ✅ SECURITY QUALITY CHECKLIST

Before marking security complete:

### Authentication & Authorization
- [ ] Strong password policy enforced
- [ ] Multi-factor authentication available
- [ ] Rate limiting on auth endpoints
- [ ] Session management secure
- [ ] Authorization checked on every request
- [ ] OAuth flows secure (if used)

### Data Protection
- [ ] Sensitive data encrypted at rest
- [ ] TLS everywhere (no exceptions)
- [ ] No sensitive data in logs
- [ ] Data minimization practiced
- [ ] Retention policies defined

### API Security
- [ ] All inputs validated
- [ ] Rate limiting enabled
- [ ] Security headers configured
- [ ] CORS properly restricted
- [ ] Error messages don't leak info

### Infrastructure
- [ ] Dependencies scanned for vulnerabilities
- [ ] Secrets properly managed
- [ ] Least privilege access
- [ ] Audit logging enabled
- [ ] Monitoring and alerting active

### Compliance
- [ ] OWASP Top 10 addressed
- [ ] Regulatory requirements met
- [ ] Penetration testing scheduled
- [ ] Incident response plan exists

---

## 💡 HARD-LEARNED LESSONS

1. **Security is never finished**: It's ongoing, not a one-time task.

2. **Defense in depth**: Multiple layers catch what others miss.

3. **Assume breach**: Design for when (not if) attackers get in.

4. **The weakest link fails**: Security is only as strong as the weakest point.

5. **Complexity is the enemy**: Simple systems are easier to secure.

6. **Trust nothing from outside**: All external input is suspect.

7. **Secrets will leak**: Plan for rotation and revocation.

8. **Audit logs solve mysteries**: Log enough to reconstruct events.

9. **Security vs usability**: Find balance, but never sacrifice core security.

10. **People are the biggest risk**: Social engineering bypasses technical controls.

---

**Apply this knowledge to every security decision.**
