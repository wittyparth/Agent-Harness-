# 💻 CODE QUALITY CHECKLIST

> **Quality gate for development phases (Phase 07-09).**

---

## ✅ Code Standards

### General
- [ ] No linting errors
- [ ] No type errors
- [ ] Consistent code style
- [ ] Clear naming conventions
- [ ] Comments on complex logic
- [ ] No console.log/print in production
- [ ] No hardcoded values (use constants/config)
- [ ] No commented-out code
- [ ] No TODO without issue reference

### Functions/Methods
- [ ] Single responsibility
- [ ] Clear input/output
- [ ] Error handling
- [ ] Reasonable length (< 50 lines guideline)
- [ ] Documented public interfaces

### Files
- [ ] One concern per file
- [ ] Reasonable file size
- [ ] Clear file naming
- [ ] Proper directory structure

---

## ✅ Backend Quality

### API Implementation
- [ ] All endpoints from contract implemented
- [ ] Correct HTTP methods
- [ ] Correct status codes
- [ ] Consistent response format
- [ ] All errors handled

### Input Validation
- [ ] All inputs validated
- [ ] Validation schemas match contract
- [ ] Error messages helpful
- [ ] No SQL/injection possible

### Authentication
- [ ] Password hashing correct (Argon2id/bcrypt)
- [ ] Token generation secure
- [ ] Token validation correct
- [ ] Session management secure
- [ ] Logout invalidates session

### Authorization
- [ ] All routes check authentication
- [ ] All routes check authorization
- [ ] Resource ownership verified
- [ ] No authorization bypass possible

### Database
- [ ] Queries parameterized
- [ ] No N+1 queries
- [ ] Transactions where needed
- [ ] Indexes on query columns
- [ ] Migrations versioned

### Error Handling
- [ ] All errors caught
- [ ] Generic errors to client
- [ ] Detailed errors in logs
- [ ] Recovery paths exist

### Logging
- [ ] Structured logging
- [ ] Key events logged
- [ ] No sensitive data in logs
- [ ] Request ID traces

---

## ✅ Frontend Quality

### Components
- [ ] All components from design system built
- [ ] All states implemented
- [ ] Props typed
- [ ] Default props sensible
- [ ] Reusable where appropriate

### State Management
- [ ] State categorized correctly
- [ ] Server state cached properly
- [ ] No prop drilling
- [ ] State updates efficient

### Data Fetching
- [ ] Loading states shown
- [ ] Error states handled
- [ ] Empty states designed
- [ ] Optimistic updates where appropriate
- [ ] Cache invalidation correct

### Forms
- [ ] Validation works
- [ ] Error messages clear
- [ ] Submit handling correct
- [ ] Loading state on submit
- [ ] Preserves input on error

### Performance
- [ ] No unnecessary re-renders
- [ ] Lists virtualized if long
- [ ] Images optimized
- [ ] Code split by route

### Accessibility
- [ ] Semantic HTML
- [ ] Keyboard navigable
- [ ] Focus management correct
- [ ] ARIA labels where needed
- [ ] Contrast passing

---

## ✅ Testing Quality

### Unit Tests
- [ ] Business logic tested
- [ ] Edge cases covered
- [ ] Error paths tested
- [ ] Tests are isolated
- [ ] Tests are deterministic

### Integration Tests
- [ ] API endpoints tested
- [ ] All status codes tested
- [ ] Authentication tested
- [ ] Authorization tested

### E2E Tests
- [ ] Critical paths covered
- [ ] Auth flow tested
- [ ] Core feature tested
- [ ] Tests not flaky

### Coverage
- [ ] Line coverage > 70%
- [ ] Critical paths 100%
- [ ] Tests meaningful (not just for coverage)

---

## ✅ Security Quality

### Code Security
- [ ] No secrets in code
- [ ] No secrets in logs
- [ ] Inputs validated
- [ ] Outputs encoded
- [ ] Dependencies scanned

### Runtime Security
- [ ] Auth/authz enforced
- [ ] Rate limiting active
- [ ] HTTPS only
- [ ] Security headers set
- [ ] CORS restricted

---

## 📋 Sign-off

Code quality verified:

| Item | Status | Notes |
|------|--------|-------|
| Backend Code | [ ] Complete | |
| Frontend Code | [ ] Complete | |
| Tests | [ ] Passing | |
| Security | [ ] Verified | |
| Ready for Integration | [ ] Yes | |

---

**Pass all items before proceeding to next phase.**
