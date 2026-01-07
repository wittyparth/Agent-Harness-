# 🧪 TESTING MASTERY

> **Complete knowledge for building comprehensive test suites.**
> **What a 20+ year veteran engineer knows about ensuring software quality.**

---

## 🎯 CORE MISSION

Tests are your safety net and documentation. They ensure:
- **Correctness**: Code does what it's supposed to
- **Regression Prevention**: Changes don't break existing functionality
- **Confidence**: Deploy without fear
- **Documentation**: Tests show how code should behave
- **Design Feedback**: Hard-to-test code is often poorly designed

---

## 📋 COMPLETE TESTING IMPLEMENTATION GUIDE

### PHASE 1: TESTING STRATEGY

#### 1.1 The Testing Pyramid

```
         /\
        /  \      E2E Tests (Few)
       /----\     - Full user journeys
      /      \    - Critical paths only
     /--------\   
    /          \  Integration Tests (Some)
   /------------\ - Components working together
  /              \ - API tests
 /----------------\
/                  \ Unit Tests (Many)
 ------------------  - Individual functions
                     - Business logic
```

**Distribution Target:**
- Unit Tests: 70% of tests
- Integration Tests: 20% of tests
- E2E Tests: 10% of tests

#### 1.2 What to Test (Priority Order)

1. **Critical User Journeys**
   - Signup, login, logout
   - Core value-delivery features
   - Checkout/payment (if applicable)
   - Data creation and modification

2. **Business Logic**
   - Calculations
   - Validations
   - State transitions
   - Authorization rules

3. **Edge Cases**
   - Empty inputs
   - Maximum values
   - Invalid inputs
   - Concurrent operations
   - Error conditions

4. **Integration Points**
   - API endpoints
   - Database operations
   - External service calls
   - Message queues

#### 1.3 What NOT to Test (or Test Minimally)

- Third-party library internals
- Framework code
- Trivial getter/setters
- Private implementation details that may change
- UI layout (unless critical)

---

### PHASE 2: UNIT TESTING

#### 2.1 Unit Test Principles

**What Makes a Good Unit Test:**
- **Fast**: Runs in milliseconds
- **Isolated**: No external dependencies (DB, network, file system)
- **Repeatable**: Same result every time
- **Self-validating**: Pass/fail is automatic
- **Timely**: Written close to code being tested

**AAA Pattern:**
1. **Arrange**: Set up test data and conditions
2. **Act**: Execute the code being tested
3. **Assert**: Verify the results

#### 2.2 What to Unit Test

**Always Unit Test:**
- Pure functions (calculations, transformations)
- Validation logic
- Business rules
- State machines
- Utility functions
- Error handling paths

**Unit Test Examples:**
```
Test: calculateTotalPrice
  - Should calculate correct total for single item
  - Should calculate correct total for multiple items
  - Should apply discount correctly
  - Should handle zero quantity
  - Should throw for negative quantity
  - Should round to 2 decimal places
```

#### 2.3 Mocking and Stubbing

**When to Mock:**
- External services (APIs, databases)
- Time/date functions
- Random number generation
- File system operations
- Network requests

**When NOT to Mock:**
- The code you're testing
- Simple value objects
- Pure functions

**Mocking Best Practices:**
- Mock at boundaries (not deep implementation)
- Verify mock was called correctly
- Use realistic mock data
- Don't mock what you don't own (wrap it first)

#### 2.4 Test Naming Conventions

**Format:** `should_[expected behavior]_when_[condition]`

Examples:
- `should_return_user_when_valid_id_provided`
- `should_throw_not_found_when_user_does_not_exist`
- `should_hash_password_when_user_created`
- `should_reject_when_email_already_exists`

#### 2.5 Test Data Management

**Use Factories/Builders:**
- Create test data consistently
- Override only relevant fields per test
- Avoid magic values (use named constants)

**Test Data Principles:**
- Each test creates its own data
- Tests don't depend on each other
- Clean up after tests (or use transactions)
- Use realistic but fake data

---

### PHASE 3: INTEGRATION TESTING

#### 3.1 Integration Test Scope

**What Integration Tests Cover:**
- Multiple components working together
- Database operations
- API endpoints
- Service interactions
- Cache behavior

#### 3.2 API Testing

**For Every API Endpoint, Test:**

| Scenario | What to Verify |
|----------|---------------|
| Happy path | Correct response, status code |
| Validation errors | 400 with error details |
| Authentication required | 401 when missing |
| Authorization denied | 403 when not permitted |
| Resource not found | 404 with message |
| Conflict | 409 for duplicates |
| Rate limiting | 429 when exceeded |
| Server error | 500 handled gracefully |

**For POST/PUT/PATCH Endpoints:**
- Valid data creates/updates correctly
- Missing required fields rejected
- Invalid field formats rejected
- Extra fields ignored or rejected
- Partial updates work correctly (PATCH)

**For GET Endpoints:**
- Returns correct data
- Filtering works
- Sorting works
- Pagination works
- Empty results handled

**For DELETE Endpoints:**
- Resource deleted
- Related data handled (cascade or prevent)
- Already deleted returns 404 or 204
- Authorization checked

#### 3.3 Database Integration Tests

**What to Test:**
- CRUD operations work correctly
- Constraints enforced (unique, foreign key)
- Transactions commit/rollback properly
- Complex queries return expected results
- Indexes are used (for performance tests)

**Database Test Setup:**
- Use real database (same type as production)
- Run in transactions and rollback
- Or truncate/reset between tests
- Isolated test database per test run

#### 3.4 External Service Testing

**Options:**
1. **Mock/Stub**: Fast, isolated, no real calls
2. **Contract Tests**: Verify mock matches real API
3. **Sandbox Environment**: Real API in test mode
4. **Record/Replay**: Record real responses, replay in tests

**What to Test:**
- Success responses handled
- Error responses handled
- Timeout handling
- Retry logic
- Rate limiting respected

---

### PHASE 4: END-TO-END (E2E) TESTING

#### 4.1 E2E Test Strategy

**Only Test Critical Paths:**
- User registration and login
- Main value-delivery workflow
- Checkout/payment (if applicable)
- Critical admin functions

**Why Limit E2E Tests:**
- Slow to run
- Brittle (break with UI changes)
- Expensive to maintain
- Harder to debug

#### 4.2 E2E Test Implementation

**Best Practices:**
- Use stable selectors (data-testid, not CSS classes)
- Wait for elements properly (no fixed sleeps)
- Test user behavior, not implementation
- Run in CI pipeline
- Have retry mechanism for flaky tests
- Screenshot/video on failure

**What to Verify:**
- User can complete the journey
- Data persists correctly
- Navigation works
- Error messages appear
- Success confirmations shown

#### 4.3 E2E Test Scenarios

**Example: User Registration E2E**
1. Navigate to signup page
2. Fill in valid registration data
3. Submit form
4. Verify redirect to dashboard/welcome
5. Verify user can log out
6. Verify user can log back in

**Example: Form Validation E2E**
1. Navigate to form
2. Submit without filling required fields
3. Verify error messages appear
4. Fill invalid email format
5. Verify email error
6. Fill valid data
7. Submit successfully

---

### PHASE 5: SPECIFIC TEST TYPES

#### 5.1 Authentication Testing

**Test Cases for Login:**
- Valid credentials → successful login
- Invalid password → 401, generic error
- Non-existent user → 401, generic error (same message)
- Account locked → appropriate error
- MFA required → prompt for code
- Session created with correct expiration

**Test Cases for Logout:**
- Session invalidated
- Token no longer works
- Redirect to login page

**Test Cases for Password Reset:**
- Request with valid email → email sent
- Request with invalid email → same response (security)
- Valid token → can reset password
- Expired token → error
- Used token → error
- New password must meet requirements

**Test Cases for OAuth:**
- Redirect to provider
- Callback creates/links account
- State parameter validated
- Errors handled gracefully

#### 5.2 Authorization Testing

**Test Cases:**
- User can access their own resources
- User cannot access others' resources
- Admin can access admin endpoints
- Regular user cannot access admin endpoints
- Deleted/deactivated user cannot access
- Permission changes take effect immediately

#### 5.3 Validation Testing

**For Each Validated Field, Test:**
- Valid input accepted
- Missing required field rejected
- Too short/long rejected
- Invalid format rejected
- SQL injection attempts rejected
- XSS attempts rejected
- Edge cases (empty string, whitespace, unicode)

#### 5.4 Concurrency Testing

**Test Cases:**
- Simultaneous updates don't lose data
- Race conditions handled
- Optimistic locking works
- Deadlocks don't occur
- Rate limiting works under load

#### 5.5 Error Handling Testing

**Test Cases:**
- Network failure handled
- Timeout handled
- Database unavailable handled
- External service failure handled
- Invalid responses handled
- Recovery works when service returns

---

### PHASE 6: PERFORMANCE TESTING

#### 6.1 Performance Test Types

| Type | Purpose | When to Run |
|------|---------|-------------|
| **Load Testing** | Normal expected load | Before major releases |
| **Stress Testing** | Beyond normal load | Periodically |
| **Spike Testing** | Sudden traffic spikes | Before marketing campaigns |
| **Endurance Testing** | Sustained load over time | Monthly |

#### 6.2 Performance Metrics

**Response Time:**
- p50 (median): Typical experience
- p95: Most users' experience
- p99: Worst case for most

**Throughput:**
- Requests per second
- Transactions per second

**Error Rate:**
- Under normal load: < 0.1%
- Under stress: acceptable degradation

**Resource Usage:**
- CPU, memory, disk I/O
- Database connections
- Network bandwidth

#### 6.3 Performance Test Targets

| Metric | Target | Maximum |
|--------|--------|---------|
| API response time (p95) | < 200ms | < 500ms |
| Page load time | < 2s | < 4s |
| Database query time | < 50ms | < 200ms |
| Error rate under load | < 0.1% | < 1% |

---

### PHASE 7: SECURITY TESTING

#### 7.1 Security Test Cases

**Authentication:**
- Brute force protected (rate limiting)
- Password complexity enforced
- Sessions timeout correctly
- Tokens expire correctly

**Input Validation:**
- SQL injection attempts blocked
- XSS attempts blocked
- Path traversal blocked
- Command injection blocked

**Authorization:**
- Horizontal access control (can't access other users' data)
- Vertical access control (can't escalate privileges)
- API keys/tokens properly scoped

**Data Protection:**
- Sensitive data encrypted in transit
- Sensitive data encrypted at rest
- No sensitive data in logs
- No sensitive data in URLs

#### 7.2 Security Testing Tools

- OWASP ZAP (automated scanning)
- Burp Suite (manual testing)
- sqlmap (SQL injection)
- Dependency scanners (npm audit, safety)

---

### PHASE 8: TEST ORGANIZATION

#### 8.1 Test File Structure

```
tests/
├── unit/
│   ├── services/
│   │   ├── user.service.test.ts
│   │   └── order.service.test.ts
│   ├── utils/
│   │   └── validation.test.ts
│   └── hooks/
│       └── use-auth.test.ts
├── integration/
│   ├── api/
│   │   ├── auth.test.ts
│   │   ├── users.test.ts
│   │   └── orders.test.ts
│   └── database/
│       └── user.repository.test.ts
├── e2e/
│   ├── auth.e2e.ts
│   ├── checkout.e2e.ts
│   └── onboarding.e2e.ts
└── fixtures/
    ├── users.ts
    ├── orders.ts
    └── factories.ts
```

#### 8.2 Test Configuration

**Environments:**
- Unit tests: In-memory, no external deps
- Integration tests: Test database, mocked externals
- E2E tests: Full stack, test environment

**CI Pipeline:**
1. Unit tests (fast, run on every commit)
2. Integration tests (medium, run on PR)
3. E2E tests (slow, run before merge)

---

### PHASE 9: TEST COVERAGE

#### 9.1 Coverage Targets

| Coverage Type | Minimum | Ideal |
|---------------|---------|-------|
| Line coverage | 70% | 85% |
| Branch coverage | 60% | 80% |
| Function coverage | 80% | 90% |
| Critical path coverage | 100% | 100% |

#### 9.2 Coverage Anti-patterns

**Don't:**
- Chase 100% coverage (diminishing returns)
- Test only to increase coverage
- Count tests without assertions
- Exclude files to improve numbers

**Do:**
- Require coverage for critical paths
- Review what's not covered
- Focus on meaningful tests
- Use coverage to find gaps

---

### PHASE 10: TEST MAINTENANCE

#### 10.1 Keeping Tests Healthy

**Regular Maintenance:**
- Fix flaky tests immediately
- Update tests when requirements change
- Remove obsolete tests
- Refactor duplicate test code
- Keep tests fast

**Flaky Test Handling:**
- Identify root cause (timing, data, order)
- Add proper waits (not sleeps)
- Isolate test data
- Run in sequence if needed
- Quarantine while fixing

#### 10.2 Test Documentation

**Document:**
- How to run tests locally
- Test environment setup
- Test data management
- How to add new tests
- CI/CD integration

---

## ✅ TESTING QUALITY CHECKLIST

Before marking testing complete:

### Coverage
- [ ] Critical paths have tests
- [ ] Business logic has unit tests
- [ ] API endpoints have integration tests
- [ ] At least one E2E test per critical journey
- [ ] Error paths tested
- [ ] Edge cases tested

### Test Quality
- [ ] Tests are independent
- [ ] Tests are deterministic
- [ ] Test names are descriptive
- [ ] No flaky tests
- [ ] Tests run in CI

### Security Testing
- [ ] Authentication tested
- [ ] Authorization tested
- [ ] Input validation tested
- [ ] No hardcoded credentials in tests

### Performance
- [ ] Tests run quickly enough
- [ ] Slow tests identified
- [ ] Performance baselines established

---

## 💡 HARD-LEARNED LESSONS

1. **Write tests first for bugs**: When you find a bug, write a test that fails first, then fix.

2. **Test behavior, not implementation**: Tests that verify behavior survive refactoring.

3. **One assertion per test is a guideline, not a rule**: Test one concept, maybe multiple assertions.

4. **Flaky tests are worse than no tests**: They destroy confidence and waste time.

5. **Fast tests get run**: If tests are slow, people skip them.

6. **Testing is a skill**: It takes practice to write good tests.

7. **Test the interface, not the implementation**: Test public APIs, not private methods.

8. **Coverage is a tool, not a goal**: High coverage with bad tests is worse than low coverage with good tests.

9. **Delete tests that don't add value**: Maintenance cost is real.

10. **Test what can break**: Don't test constructors and trivial getters.

---

**Apply this knowledge to every testing decision.**
