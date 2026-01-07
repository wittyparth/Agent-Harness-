# 🔒 SECURITY CHECKLIST

> **Quality gate for security audit (Phase 11).**

---

## ✅ Authentication Security

### Password Security
- [ ] Passwords hashed with Argon2id or bcrypt
- [ ] Minimum 8 character requirement
- [ ] Passwords never stored in plain text
- [ ] Passwords not logged anywhere
- [ ] Password not in error messages

### Session/Token Security
- [ ] Access token lifetime ≤ 15 minutes
- [ ] Refresh token rotation implemented
- [ ] Token revocation works
- [ ] Sessions invalidated on password change
- [ ] HttpOnly cookies (if using cookies)
- [ ] Secure flag in production
- [ ] SameSite attribute set

### Multi-Factor Authentication
- [ ] Available for sensitive operations
- [ ] TOTP implemented correctly (if used)
- [ ] Recovery codes available
- [ ] MFA cannot be bypassed

### Brute Force Protection
- [ ] Rate limiting on login (5 per 15 min)
- [ ] Rate limiting on password reset (3 per hour)
- [ ] Account lockout (optional)
- [ ] CAPTCHA for suspicious activity (optional)

---

## ✅ Authorization Security

### Access Control
- [ ] Every endpoint checks authentication
- [ ] Every endpoint checks authorization
- [ ] Default deny (no implicit access)
- [ ] Role-based access enforced

### Resource Access
- [ ] Resource ownership verified
- [ ] Cannot access other users' data
- [ ] Cannot modify other users' data
- [ ] Cannot delete other users' data
- [ ] ID enumeration prevented

### Privilege Escalation
- [ ] Cannot elevate own role
- [ ] Admin functions protected
- [ ] Permission changes audited

---

## ✅ Input Validation

### All Inputs Validated
- [ ] All API body parameters
- [ ] All query parameters
- [ ] All path parameters
- [ ] All headers (if used)
- [ ] All file uploads

### Injection Prevention
- [ ] SQL injection (parameterized queries)
- [ ] NoSQL injection
- [ ] Command injection
- [ ] XSS (output encoding)
- [ ] XXE (XML disabled or sanitized)

---

## ✅ Data Protection

### Encryption in Transit
- [ ] TLS 1.2+ required
- [ ] HTTPS only
- [ ] Valid SSL certificate
- [ ] No mixed content

### Encryption at Rest
- [ ] Database encryption enabled
- [ ] Sensitive fields encrypted
- [ ] Backups encrypted

### Sensitive Data
- [ ] Passwords hashed (not encrypted)
- [ ] API keys secured
- [ ] PII protected
- [ ] Finance data protected per PCI
- [ ] Data minimization practiced

### Logging
- [ ] No passwords in logs
- [ ] No tokens in logs
- [ ] No PII in logs (unless required)
- [ ] No credit card numbers in logs

---

## ✅ Configuration Security

### Secrets Management
- [ ] No secrets in source code
- [ ] No secrets in Docker images
- [ ] Secrets in environment or secret manager
- [ ] Different secrets per environment
- [ ] Secrets rotatable

### Production Settings
- [ ] Debug mode disabled
- [ ] Default credentials changed
- [ ] Unnecessary features disabled
- [ ] Verbose errors disabled
- [ ] Stack traces not shown

### Dependencies
- [ ] No known vulnerabilities
- [ ] Dependencies up to date
- [ ] Automated scanning enabled
- [ ] Unused dependencies removed

---

## ✅ Security Headers

### Headers Configured
- [ ] Strict-Transport-Security (HSTS)
- [ ] X-Content-Type-Options: nosniff
- [ ] X-Frame-Options: DENY (or SAMEORIGIN)
- [ ] Content-Security-Policy
- [ ] Referrer-Policy
- [ ] Permissions-Policy

### CORS
- [ ] Not using wildcard (*) with credentials
- [ ] Specific origins whitelisted
- [ ] Appropriate methods allowed
- [ ] Appropriate headers allowed

---

## ✅ API Security

### Rate Limiting
- [ ] Rate limits on all endpoints
- [ ] Stricter on auth endpoints
- [ ] Rate limit headers returned
- [ ] 429 response when exceeded

### Request Validation
- [ ] Request size limits
- [ ] Timeout limits
- [ ] Method restrictions
- [ ] Content-type validation

---

## ✅ Logging & Monitoring

### Security Logging
- [ ] Authentication attempts logged
- [ ] Authorization failures logged
- [ ] Validation failures logged
- [ ] Admin actions logged
- [ ] Security events alerted

### Log Protection
- [ ] Log access restricted
- [ ] Logs tamper-resistant
- [ ] Log retention defined
- [ ] Log backup configured

---

## 📋 Sign-off

Security audit complete:

| Item | Status | Auditor | Notes |
|------|--------|---------|-------|
| Authentication | [ ] Passed | | |
| Authorization | [ ] Passed | | |
| Input Validation | [ ] Passed | | |
| Data Protection | [ ] Passed | | |
| Configuration | [ ] Passed | | |
| Headers | [ ] Passed | | |
| API Security | [ ] Passed | | |
| Logging | [ ] Passed | | |

**All critical items must pass before launch.**

---

## ⚠️ Findings

Document any issues found:

| ID | Severity | Description | Status |
|----|----------|-------------|--------|
| SEC-001 | | | |
| SEC-002 | | | |

Severity: Critical / High / Medium / Low
Status: Open / Fixed / Accepted Risk
