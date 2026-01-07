# 🧪 PHASE 10: TESTING

> **Comprehensive testing to ensure quality. Unit, integration, E2E, and more.**

---

## 🎯 PURPOSE

Ensure the application is thoroughly tested:
- Complete unit test coverage for business logic
- Integration tests for API
- E2E tests for user journeys
- Performance baseline
- Accessibility testing

**Time Investment**: 4-8 hours
**Skip Risk**: Bugs in production, regressions, unreliable system

---

## 📥 INPUTS REQUIRED

1. Integrated application (Phase 09)
2. User stories with acceptance criteria (Phase 02)
3. API contract (Phase 06)

---

## 📤 EXPECTED OUTPUTS

1. **Test Suites**
   - Unit tests
   - Integration tests
   - E2E tests

2. **Test Coverage Report**
   - Coverage metrics
   - Identified gaps

3. **Test Documentation**
   - How to run tests
   - Test data management

---

## 🔄 PROCESS

### Step 1: Unit Test Audit

**Review Existing Unit Tests:**
- Are all business logic functions tested?
- Are edge cases covered?
- Are error paths tested?

**Add Missing Unit Tests For:**

**Backend:**
- [ ] Validation functions
- [ ] Business logic services
- [ ] Authorization helpers
- [ ] Utility functions
- [ ] Data transformation functions

**Frontend:**
- [ ] Custom hooks
- [ ] Utility functions
- [ ] State management logic
- [ ] Form validation schemas

### Step 2: Integration Test Audit

**Backend API Tests:**
For each endpoint, test:

| Scenario | What to Verify |
|----------|---------------|
| Valid request | Correct response, status code |
| Missing required field | 400 with error details |
| Invalid field format | 400 with error details |
| Unauthenticated | 401 |
| Unauthorized | 403 |
| Resource not found | 404 |
| Duplicate/conflict | 409 |

**Add Missing API Tests:**
- [ ] All CRUD endpoints
- [ ] All authentication endpoints
- [ ] All edge cases
- [ ] Error responses

### Step 3: E2E Test Implementation

**Critical Paths to Test:**

**Authentication Flow:**
```
1. Navigate to signup
2. Fill registration form
3. Submit
4. Verify redirect/confirmation
5. Login with new credentials
6. Verify access to protected area
7. Logout
8. Verify redirect to public area
```

**Core Feature Flow:**
```
1. Login
2. Navigate to feature
3. Complete primary action
4. Verify success
5. Verify data persisted
```

**Error Recovery Flow:**
```
1. Navigate to form
2. Submit invalid data
3. Verify error messages
4. Fix errors
5. Submit valid data
6. Verify success
```

### Step 4: Accessibility Testing

**Automated Testing:**
- Run axe-core or similar
- Fix all critical/serious issues
- Document minor issues for backlog

**Manual Testing:**
- [ ] Keyboard navigation works
- [ ] Tab order is logical
- [ ] Focus indicators visible
- [ ] Screen reader makes sense
- [ ] Skip link works
- [ ] Headings are hierarchical

### Step 5: Performance Testing

**Frontend Performance:**
- Run Lighthouse audit
- Target scores: Performance > 90, Accessibility > 90
- Identify and fix top issues

**Backend Performance:**
- Measure response times for key endpoints
- Identify slow queries
- Set baseline for monitoring

**Performance Checklist:**
- [ ] Lighthouse Performance > 90
- [ ] LCP < 2.5s
- [ ] CLS < 0.1
- [ ] API P95 < 200ms

### Step 6: Security Testing

**Automated Scanning:**
- Run SAST tools
- Check dependencies for vulnerabilities
- Fix critical issues

**Manual Security Tests:**
- [ ] SQL injection attempts rejected
- [ ] XSS attempts sanitized
- [ ] Authentication bypass impossible
- [ ] Authorization enforced
- [ ] Rate limiting works
- [ ] CORS properly configured

### Step 7: Cross-Browser Testing

**Browsers to Test:**
- Chrome (latest 2 versions)
- Firefox (latest 2 versions)
- Safari (latest 2 versions)
- Edge (latest 2 versions)
- Mobile Safari (iOS)
- Chrome Mobile (Android)

**For Each Browser, Verify:**
- [ ] Layout correct
- [ ] Functionality works
- [ ] No console errors
- [ ] Forms work
- [ ] Authentication works

### Step 8: Mobile Testing

**Device Testing:**
- Test on actual mobile devices (not just emulator)
- Test on different screen sizes
- Test touch interactions

**Mobile Checklist:**
- [ ] Layouts work at 320px
- [ ] Touch targets adequate (44px)
- [ ] Forms usable on mobile
- [ ] Keyboard doesn't obscure inputs
- [ ] Navigation works

### Step 9: Test Coverage Analysis

**Coverage Targets:**
- Line coverage: > 70%
- Branch coverage: > 60%
- Critical paths: 100%

**Identify Gaps:**
- Review uncovered code
- Prioritize critical areas
- Add tests for gaps

### Step 10: Test Documentation

**Document:**
- How to run all tests locally
- How to run tests in CI
- Test environment setup
- Test data management
- Known test limitations

---

## ✅ QUALITY GATE

Before proceeding to Phase 11, verify:

### Unit Tests
- [ ] All business logic tested
- [ ] Edge cases covered
- [ ] Error paths tested
- [ ] Coverage targets met

### Integration Tests
- [ ] All API endpoints tested
- [ ] All error responses tested
- [ ] All authentication scenarios tested
- [ ] All authorization scenarios tested

### E2E Tests
- [ ] Authentication flow tested
- [ ] Core feature flow tested
- [ ] Error handling tested
- [ ] Mobile flow tested

### Other Testing
- [ ] Accessibility audit passed
- [ ] Performance baselines set
- [ ] Security tests passed
- [ ] Cross-browser tested
- [ ] Mobile tested

### CI/CD
- [ ] Tests run in CI
- [ ] Tests must pass to deploy
- [ ] Coverage reported

- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

- `.harness/knowledge/TESTING_MASTERY.md` - Complete testing guide

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Testing Only Happy Paths
Error paths and edge cases are where bugs hide.

### Mistake 2: Brittle E2E Tests
Use stable selectors (data-testid, not CSS classes).

### Mistake 3: Slow Test Suite
Slow tests don't get run. Optimize.

### Mistake 4: Ignoring Flaky Tests
Fix or delete flaky tests immediately.

### Mistake 5: No CI Integration
Tests must run automatically.

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 11: Security.**
