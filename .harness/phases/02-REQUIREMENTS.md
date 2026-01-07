# 📋 PHASE 02: REQUIREMENTS

> **Define WHAT we're building with precision. Ambiguity here multiplies problems later.**

---

## 🎯 PURPOSE

Transform the validated idea into detailed, actionable requirements:
- Define all features with acceptance criteria
- Create user stories that drive development
- Prioritize features for MVP vs future
- Establish non-functional requirements
- Create a feature map for the entire product

**Time Investment**: 2-4 hours
**Skip Risk**: Building the wrong thing or endless scope creep

---

## 📥 INPUTS REQUIRED

1. Completed Discovery Document (from Phase 01)
2. User available to clarify requirements

---

## 📤 EXPECTED OUTPUTS

1. **Requirements Document** (`projects/[name]/docs/REQUIREMENTS.md`)
   - Feature list with priorities
   - User stories with acceptance criteria
   - Non-functional requirements
   - Out of scope items

2. **User Story Backlog** (`projects/[name]/docs/USER_STORIES.md`)
   - All user stories in proper format
   - Acceptance criteria
   - Priority levels

3. **Updated State Files**
   - ACTIVE_PROJECT.md updated
   - DECISION_LOG.md with scope decisions

---

## 🔄 PROCESS

### Step 1: Feature Brainstorm

Starting from the discovery document, list ALL possible features:

```markdown
## FEATURE BRAINSTORM

### Instructions
- List every feature you can imagine
- Don't filter yet - capture everything
- Include obvious AND ambitious features
- Group by functional area

### Categories to Consider
- User Management (signup, login, profile, settings)
- Core Functionality (main value delivery)
- Data Management (CRUD operations)
- Communication (notifications, emails, messaging)
- Admin Features (if applicable)
- Integrations (third-party services)
- Analytics/Reporting
- Billing/Payments (if applicable)
- Social Features (sharing, collaboration)
- Mobile-specific (if applicable)
```

### Step 2: Feature Prioritization

Use MoSCoW method:

```markdown
## FEATURE PRIORITIZATION (MoSCoW)

### Must Have (MVP - Cannot launch without)
Features that are essential for the product to work at all.
| Feature | Reason it's essential |
|---------|----------------------|
| User registration | Can't have users without signup |
| [Core feature 1] | Delivers primary value |
| ... | ... |

### Should Have (High Priority - Launch soon after MVP)
Important features that significantly improve value but aren't essential.
| Feature | Value it adds |
|---------|--------------|
| ... | ... |

### Could Have (Medium Priority - Nice to have)
Features that add value but can wait.
| Feature | Value it adds |
|---------|--------------|
| ... | ... |

### Won't Have (This Release)
Features explicitly out of scope for now.
| Feature | Why not now |
|---------|------------|
| ... | ... |
```

### Step 3: User Stories

Convert features to user stories:

```markdown
## USER STORY FORMAT

As a [type of user]
I want to [action/goal]
So that [benefit/value]

### Acceptance Criteria
- Given [context]
- When [action]
- Then [expected result]
```

#### Example User Stories

```markdown
## USER STORY: US-001 - User Registration

### Story
As a new visitor
I want to create an account with email and password
So that I can access the platform features

### Acceptance Criteria
1. Given I am on the homepage
   When I click "Sign Up"
   Then I see a registration form

2. Given I am on the registration form
   When I submit valid email and password (min 8 chars, 1 number, 1 uppercase)
   Then my account is created and I receive a confirmation email

3. Given I am on the registration form
   When I submit an email that already exists
   Then I see an error "This email is already registered"

4. Given I am on the registration form
   When I submit an invalid email format
   Then I see an error "Please enter a valid email"

5. Given I am on the registration form
   When I submit a weak password
   Then I see specific feedback on password requirements

### Priority: MUST HAVE
### Estimated Complexity: Medium
### Dependencies: Email service integration
```

### Step 4: Non-Functional Requirements

Define quality attributes:

```markdown
## NON-FUNCTIONAL REQUIREMENTS

### Performance
- Page load time: < 3 seconds on 3G
- API response time: < 200ms for 95th percentile
- Time to interactive: < 4 seconds
- Support concurrent users: [X number]

### Scalability
- Handle [X] users in first month
- Handle [Y] users in first year
- Database should support [Z] records

### Security
- HTTPS everywhere
- Authentication required for [which features]
- Data encryption at rest for [which data]
- GDPR/Privacy compliance needed? [Yes/No]
- Two-factor authentication needed? [Yes/No]

### Availability
- Target uptime: [99.9%? 99%?]
- Acceptable downtime window: [When?]
- Disaster recovery requirements

### Compatibility
- Browsers: Chrome, Firefox, Safari, Edge (latest 2 versions)
- Mobile responsive: Yes
- Native mobile app needed: [Yes/No]
- Offline capability needed: [Yes/No]

### Accessibility
- WCAG level target: [AA/AAA]
- Screen reader support: [Required/Nice-to-have]
- Keyboard navigation: Required

### Usability
- First-time user success rate target: [X%]
- User should complete [key action] in < [X] minutes
- Help documentation required: [Yes/No]

### Internationalization
- Languages needed: [List]
- RTL support needed: [Yes/No]
- Currency/date format localization: [Yes/No]
```

### Step 5: Feature Dependencies Map

```markdown
## FEATURE DEPENDENCIES

### Dependency Graph
[Feature A] ──depends on──> [Feature B]
Example:
- Password Reset → Email Service
- User Profile → User Registration
- Checkout → Shopping Cart → Product Catalog

### Build Order (Suggested)
Based on dependencies, build in this order:
1. Foundation (Auth, Core Data Models)
2. Core Value Features
3. Enhancement Features
4. Polish Features

### External Dependencies
| Feature | External Dependency | Status |
|---------|--------------------|---------
| Email | SendGrid/Resend API | Need to set up |
| Payments | Stripe | Need to set up |
| ... | ... | ... |
```

### Step 6: Scope Definition

Clearly define what's IN and OUT:

```markdown
## SCOPE DEFINITION

### In Scope (MVP)
- [Feature 1]
- [Feature 2]
- [Feature 3]
- ...

### Out of Scope (MVP) - To be added later
- [Feature A] - Will add in v1.1
- [Feature B] - Will add in v1.2
- [Feature C] - Maybe never

### Explicit Exclusions
These are NOT being built and won't be added:
- [Thing 1] - Reason
- [Thing 2] - Reason

### Scope Change Process
Any request to change scope must:
1. Be documented in DECISION_LOG.md
2. Assess impact on timeline
3. Get explicit approval
4. Update this document
```

### Step 7: Create Requirements Document

Combine everything into the final document:

```markdown
# Requirements Document: [Project Name]

## Document Info
- Version: 1.0
- Last Updated: [Date]
- Status: [Draft/Review/Approved]

## Executive Summary
[Brief overview of requirements]

## Feature List (Prioritized)
[Table from Step 2]

## User Stories
[All stories from Step 3]

## Non-Functional Requirements
[From Step 4]

## Dependencies
[From Step 5]

## Scope
[From Step 6]

## Glossary
[Define any domain-specific terms]

## Sign-off
Requirements reviewed and approved: [Yes/Pending]
Date: [Date]
```

---

## ✅ QUALITY GATE

Before proceeding to Phase 03, verify:

- [ ] All features are listed and categorized
- [ ] MVP features clearly identified (Must Have)
- [ ] Each feature has at least one user story
- [ ] User stories have complete acceptance criteria
- [ ] Non-functional requirements defined
- [ ] Dependencies mapped
- [ ] Scope clearly defined (in/out)
- [ ] Requirements document created and saved
- [ ] User has reviewed and agreed to scope
- [ ] ACTIVE_PROJECT.md updated
- [ ] DECISION_LOG.md updated with scope decisions
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

This phase is primarily about product definition.
Reference Discovery Document for context.

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Vague User Stories
❌ "As a user, I want to log in"
✅ "As a returning user, I want to log in with email/password so that I can access my saved data"

### Mistake 2: Missing Acceptance Criteria
Every story needs testable acceptance criteria. No exceptions.

### Mistake 3: Hidden Complexity
"Simple login" might include: signup, login, logout, password reset, email verification, 
remember me, session management, social login... 
Make complexity visible.

### Mistake 4: No Prioritization
Everything is important = nothing is important.
Force rank features.

### Mistake 5: Scope Creep Acceptance
"Can we just add one more thing?" 
Always assess impact, don't just say yes.

### Mistake 6: Ignoring Non-Functional
"It should be fast" is not a requirement.
"Page load < 3 seconds on 3G" is a requirement.

---

## 💡 TIPS

### Tip 1: Start with Happy Path
Define the ideal user journey first, then edge cases.

### Tip 2: Question Every Feature
"What's the cost of NOT having this feature?"
If answer is "not much," it's not Must Have.

### Tip 3: Think in Releases
MVP → v1.1 → v1.2
Plan the roadmap, even if roughly.

### Tip 4: Include the "Un-requirements"
Explicitly listing what you WON'T build prevents scope creep.

### Tip 5: Acceptance Criteria Are Tests
Write acceptance criteria as if they were test cases.
This makes them precise and testable.

### Tip 6: Time-Box Discussions
Don't spend forever on requirements. 
Set a time limit, make decisions, move on.

---

## 📝 EXAMPLE OUTPUT

```markdown
# Requirements: TaskFlow

## MVP Features (Must Have)

### F-001: User Authentication
- US-001: User Registration (email/password)
- US-002: User Login
- US-003: User Logout
- US-004: Password Reset

### F-002: Team Management
- US-010: Create Team
- US-011: Invite Team Members
- US-012: Accept Team Invitation
- US-013: View Team Members

### F-003: Tool Integrations
- US-020: Connect GitHub
- US-021: Connect Linear
- US-022: View Integration Status

### F-004: Status Dashboard
- US-030: View Team Dashboard
- US-031: See Recent Activity
- US-032: Filter by Time Range

## Should Have Features (v1.1)
- Slack notifications
- Weekly digest emails
- Custom status templates

## Out of Scope
- Mobile native app
- AI-generated summaries
- Video call integration
```

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 03: Architecture.**
