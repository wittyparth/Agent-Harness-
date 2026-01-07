# 🔒 PHASE 11: SECURITY AUDIT

> **Security review before launch. Find and fix vulnerabilities.**

---

## 🎯 PURPOSE

Comprehensive security audit:
- Verify all security controls
- Check for common vulnerabilities
- Review configuration
- Prepare security documentation

**Time Investment**: 2-4 hours
**Skip Risk**: Data breach, unauthorized access, compliance failure

---

## 📥 INPUTS REQUIRED

1. Working application (all prior phases)
2. Security requirements from Phase 02
3. Architecture decisions from Phase 03

---

## 📤 EXPECTED OUTPUTS

1. **Security Audit Report**
   - Issues found
   - Remediation completed
   - Remaining risks documented

2. **Security Documentation**
   - Security controls in place
   - Incident response contacts

---

## 🔄 PROCESS

### Step 1: Authentication Security Audit

**Password Security:**
- [ ] Passwords hashed with Argon2id or bcrypt
- [ ] Minimum password length enforced (8+ characters)
- [ ] Password strength requirements clear
- [ ] Passwords not logged anywhere
- [ ] Passwords not in error messages

**Session/Token Security:**
- [ ] Access tokens short-lived (15 min recommended)
- [ ] Refresh tokens properly secured
- [ ] Refresh token rotation implemented
- [ ] Token revocation works (logout)
- [ ] Sessions invalidated on password change
- [ ] HttpOnly cookies (if using cookies)
- [ ] Secure flag on cookies in production
- [ ] SameSite attribute on cookies

**Brute Force Protection:**
- [ ] Rate limiting on login endpoint
- [ ] Rate limiting on password reset
- [ ] Account lockout after repeated failures (optional)
- [ ] CAPTCHA for repeated failures (optional)

**Password Reset:**
- [ ] Tokens are random and unguessable
- [ ] Tokens are single-use
- [ ] Tokens expire quickly (1 hour)
- [ ] Same response for valid/invalid emails
- [ ] Password change invalidates all sessions

### Step 2: Authorization Security Audit

**Access Control:**
- [ ] Every endpoint checks authentication
- [ ] Every endpoint checks authorization
- [ ] Resource ownership verified
- [ ] Role-based access control enforced
- [ ] Cannot access others' data via ID manipulation
- [ ] Cannot escalate privileges

**Test Authorization:**
- [ ] Access user A's data as user B → 403
- [ ] Access admin endpoint as user → 403
- [ ] Modify resource owned by another user → 403
- [ ] Access protected endpoint without token → 401

### Step 3: Input Validation Audit

**All Inputs Validated:**
- [ ] All API endpoints validate input
- [ ] All form inputs validated (client + server)
- [ ] File uploads validated (type, size)
- [ ] Query parameters validated
- [ ] Path parameters validated
- [ ] Headers validated (if used)

**Injection Prevention:**
- [ ] SQL injection impossible (parameterized queries)
- [ ] NoSQL injection prevented
- [ ] Command injection prevented
- [ ] LDAP injection prevented (if applicable)

**XSS Prevention:**
- [ ] All output encoded
- [ ] User content sanitized
- [ ] CSP headers configured
- [ ] No innerHTML with user content

### Step 4: Data Protection Audit

**Encryption:**
- [ ] TLS 1.2+ everywhere (no plain HTTP)
- [ ] Valid SSL certificates
- [ ] Sensitive data encrypted at rest
- [ ] Database encryption enabled

**Sensitive Data:**
- [ ] Passwords never stored in plain text
- [ ] API keys never in code/logs
- [ ] PII protected appropriately
- [ ] Credit card data handled per PCI (if applicable)
- [ ] Sensitive data masked in logs

**Data Minimization:**
- [ ] Only necessary data collected
- [ ] Retention policies defined
- [ ] Data deletion possible

### Step 5: Configuration Security Audit

**Secrets Management:**
- [ ] No secrets in source code
- [ ] No secrets in Docker images
- [ ] Secrets in environment variables or secret manager
- [ ] Different secrets per environment
- [ ] Secrets rotation possible

**Production Configuration:**
- [ ] Debug mode disabled
- [ ] Default credentials changed
- [ ] Unnecessary features disabled
- [ ] Error messages don't leak info
- [ ] Stack traces not shown to users

**Dependencies:**
- [ ] No known vulnerable dependencies
- [ ] Dependencies up to date
- [ ] Automated vulnerability scanning enabled

### Step 6: Security Headers Audit

**Verify Headers Present:**
- [ ] `Strict-Transport-Security` (HSTS)
- [ ] `X-Content-Type-Options: nosniff`
- [ ] `X-Frame-Options: DENY`
- [ ] `Content-Security-Policy`
- [ ] `Referrer-Policy`
- [ ] `Permissions-Policy`

**CORS Configuration:**
- [ ] Not using wildcard (*) with credentials
- [ ] Specific origins whitelisted
- [ ] Appropriate methods allowed
- [ ] Credentials handled correctly

### Step 7: Logging & Monitoring Audit

**Security Logging:**
- [ ] Authentication attempts logged
- [ ] Authorization failures logged
- [ ] Input validation failures logged
- [ ] Errors logged with context
- [ ] Admin actions logged

**Log Security:**
- [ ] Logs don't contain sensitive data
- [ ] Log access restricted
- [ ] Log tampering prevented
- [ ] Log retention defined

**Monitoring:**
- [ ] Alerts for security events
- [ ] Alerts for unusual patterns
- [ ] Monitoring dashboard available

### Step 8: API Security Audit

**Rate Limiting:**
- [ ] Rate limits on all endpoints
- [ ] Stricter limits on auth endpoints
- [ ] Rate limit headers returned
- [ ] 429 response when exceeded

**API Security:**
- [ ] API versioning in place
- [ ] Proper error responses (no stack traces)
- [ ] No sensitive data in URLs
- [ ] Request size limits enforced

### Step 9: Infrastructure Security (Pre-Deploy)

**Network:**
- [ ] Database not publicly accessible
- [ ] Firewall rules configured
- [ ] SSH key authentication only
- [ ] Admin access restricted

**Server:**
- [ ] OS patched
- [ ] Unnecessary ports closed
- [ ] Minimal installed packages
- [ ] Secure file permissions

### Step 10: Security Documentation

**Create Security Documentation:**
- Security controls in place
- Authentication mechanism
- Authorization model
- Data protection measures
- Incident response contacts
- Security update process

---

## ✅ QUALITY GATE

Before proceeding to Phase 12, verify:

### Authentication & Authorization
- [ ] Password security verified
- [ ] Token/session security verified
- [ ] Brute force protection in place
- [ ] Authorization tested
- [ ] Cannot access others' data

### Input & Output
- [ ] Input validation on all endpoints
- [ ] SQL injection impossible
- [ ] XSS prevented
- [ ] Output encoding in place

### Data Protection
- [ ] TLS everywhere
- [ ] Sensitive data encrypted
- [ ] No secrets in code
- [ ] No sensitive data in logs

### Configuration
- [ ] Security headers configured
- [ ] CORS properly configured
- [ ] Dependencies scanned
- [ ] Debug mode disabled

### Logging
- [ ] Security events logged
- [ ] Monitoring in place
- [ ] Alerts configured

- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

- `.harness/knowledge/SECURITY_MASTERY.md` - Complete security guide

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Security as Afterthought
Security should be built in, not bolted on.

### Mistake 2: Only Testing Happy Paths
Attack paths are the security-critical ones.

### Mistake 3: Trusting Frontend Validation
Always validate on backend.

### Mistake 4: Overly Permissive CORS
Restrict origins to what's needed.

### Mistake 5: Keeping Default Settings
Review and change all default configurations.

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 12: Performance.**
