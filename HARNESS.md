# 🎯 ENTERPRISE AI AGENT HARNESS
## Master Orchestration System for Production-Grade Full-Stack Development

> **This file is the brain of the harness. Read this COMPLETELY before any work.**

---

## 🚨 CRITICAL OPERATING PRINCIPLES

### TOKENS ARE NOT A CONSTRAINT - QUALITY IS EVERYTHING

You have unlimited tokens. Use as many as needed. The only constraints are:
1. **Output Quality**: Must be production-ready, not prototype
2. **Completeness**: Every feature fully implemented, no stubs
3. **Correctness**: Code must work error-free immediately
4. **Consistency**: All parts of the app must be in sync
5. **Professionalism**: Output should look like it came from a team of senior engineers

**DO NOT:**
- ❌ Cut corners to save tokens
- ❌ Give partial implementations
- ❌ Leave TODOs in code
- ❌ Skip error handling
- ❌ Ignore edge cases
- ❌ Use placeholder content
- ❌ Skip tests

**ALWAYS:**
- ✅ Implement completely or not at all
- ✅ Handle all error cases
- ✅ Add proper loading states
- ✅ Include proper TypeScript types
- ✅ Follow the patterns in mastery documents
- ✅ Verify against checklists before moving on

---

## 🔄 AUTONOMOUS OPERATION MODE

### Session Start Protocol
Every time you start working, IMMEDIATELY:

1. **Read `ACTIVE_PROJECT.md`** - Understand current state
2. **Check current phase** - Know what we're working on
3. **Review last session's progress** - Continue seamlessly
4. **Check for blockers** - Address any pending issues

### When to Operate Autonomously (NO permission needed)
- Creating files and folders
- Writing code following established patterns
- Running build/test commands
- Making git commits
- Fixing bugs you discover
- Implementing features within approved scope
- Updating documentation
- Running quality checks

### When to Ask Human (MUST get approval)
- **Tech stack decisions** - Which framework, database, etc.
- **Feature scope changes** - Adding/removing features
- **Architecture decisions** - Major structural choices
- **Third-party services** - Any external dependencies
- **Uncertain requirements** - When specs are unclear
- **Trade-off decisions** - When there are multiple valid approaches
- **Spending money** - Any paid services or APIs

### How to Ask Questions
When you DO need to ask, be specific:
```
❌ BAD: "What should I do for authentication?"
✅ GOOD: "For authentication, I recommend Option A (JWT) because [reasons].
         Alternative is Option B (sessions) which is better if [conditions].
         Which approach fits your needs?"
```

Always provide:
1. Your recommendation
2. Why you recommend it
3. Alternatives with trade-offs
4. Simple yes/no or A/B choice when possible

---

## 📁 STATE MANAGEMENT SYSTEM

### How State is Preserved (Solves Context Limit)

All state is stored in files, NOT conversation memory:

| File | Purpose |
|------|---------|
| `ACTIVE_PROJECT.md` | Current project state, what's done, what's next |
| `DECISION_LOG.md` | All decisions with reasoning (audit trail) |
| `projects/[name]/PROJECT_STATE.md` | Detailed project-specific state |
| `.harness/sync/API_SPEC.yaml` | API contract (keeps FE/BE in sync) |

### After Every Significant Action, Update State:
1. Mark task complete in `ACTIVE_PROJECT.md`
2. Log any decisions to `DECISION_LOG.md`
3. Update `PROJECT_STATE.md` with details
4. Make a git commit

### State File Format
```markdown
## Current Phase: [01-15]
## Current Task: [What you're working on]
## Progress: [X% complete]
## Last Updated: [timestamp]
## Next Action: [What to do next]
```

---

## 🔢 COMPLETE SDLC PHASES

### The 15-Phase Development Lifecycle

```
PHASE 01: DISCOVERY
    ↓ Validate idea, understand market
PHASE 02: REQUIREMENTS  
    ↓ Define features, user stories
PHASE 03: ARCHITECTURE
    ↓ Choose tech stack, design system
PHASE 04: UX DESIGN
    ↓ User flows, wireframes
PHASE 05: UI DESIGN
    ↓ Design system, components
PHASE 06: API CONTRACT ⭐ [Critical for sync]
    ↓ Define ALL APIs before coding
PHASE 07: BACKEND DEV
    ↓ Implement APIs
PHASE 08: FRONTEND DEV
    ↓ Implement UI
PHASE 09: INTEGRATION
    ↓ Connect everything
PHASE 10: TESTING
    ↓ Comprehensive tests
PHASE 11: SECURITY
    ↓ Security audit & fixes
PHASE 12: PERFORMANCE
    ↓ Optimization
PHASE 13: DEVOPS
    ↓ Containerization, CI/CD
PHASE 14: DOCUMENTATION
    ↓ All docs
PHASE 15: LAUNCH
    ↓ Final checks, deploy
```

### Phase Rules
1. **Sequential by default** - Complete each phase before moving on
2. **Quality gates** - Must pass checklist before next phase
3. **No skipping** - Even for "simple" projects
4. **Can iterate** - Go back to improve, but forward progress is primary

---

## 📚 KNOWLEDGE SYSTEM

### Mastery Documents Location
All deep knowledge is in `.harness/knowledge/`:

| Document | Contains |
|----------|----------|
| `FRONTEND_MASTERY.md` | React, Vue, Next.js, performance, state, a11y |
| `BACKEND_MASTERY.md` | API design, auth, any language, scalability |
| `DATABASE_MASTERY.md` | Schema design, queries, optimization |
| `SECURITY_MASTERY.md` | OWASP, encryption, auth patterns |
| `DEVOPS_MASTERY.md` | Docker, CI/CD, monitoring |
| `UI_UX_MASTERY.md` | Design systems, interactions, responsive |
| `TESTING_MASTERY.md` | All testing strategies |
| `AI_APPS_MASTERY.md` | LLM integration, RAG, agents |

### How to Use Knowledge Documents
1. **Before starting a phase**, read the relevant mastery doc
2. **While working**, reference specific sections
3. **When unsure**, the mastery doc is the source of truth
4. **Quality check** against mastery doc standards

---

## 🔗 SYNC SYSTEM (Frontend-Backend Alignment)

### The Problem
Frontend builds expecting one API format, backend builds another.
Result: Integration nightmare, wasted time, bugs.

### The Solution: API Contract First (Phase 06)

**RULE: No code is written until API contract is complete and approved.**

The sync system works like this:

1. **Phase 06 creates `API_SPEC.yaml`** - Complete OpenAPI specification
2. **Backend implements TO the spec** - Endpoints match exactly
3. **Frontend develops AGAINST the spec** - Can mock responses
4. **Integration is seamless** - Both sides already compatible

### Sync System Files
- `.harness/sync/API_SPEC.yaml` - OpenAPI 3.0 specification
- `.harness/sync/TYPES.md` - Shared type definitions
- `.harness/sync/CONTRACTS.md` - Data contracts and validation rules

### If Frontend and Backend Conflict
1. The API spec is the source of truth
2. The side that deviates must fix to match spec
3. Spec changes require explicit approval and propagation to both sides

---

## ✅ QUALITY GATES

### Every Phase Has a Quality Gate
Cannot proceed to next phase until gate passes.

### Gate Categories
1. **Completeness** - All required outputs exist
2. **Correctness** - Outputs are accurate
3. **Quality** - Meets standards in mastery docs
4. **Verification** - Tested/reviewed

### Checklist Files
Located in `.harness/quality/`:
- `DESIGN_CHECKLIST.md`
- `CODE_QUALITY_CHECKLIST.md`
- `SECURITY_CHECKLIST.md`
- `PERFORMANCE_CHECKLIST.md`
- `LAUNCH_CHECKLIST.md`

### How to Pass a Gate
1. Go through every item in relevant checklist
2. Mark items as ✅ or ❌
3. Fix all ❌ items before proceeding
4. Document any exceptions with reasoning

---

## 🔀 GIT WORKFLOW

### Branch Strategy
```
main                 - Production-ready code
└── develop          - Integration branch
    └── feature/*    - Feature branches
    └── fix/*        - Bug fixes
```

### Commit Convention
```
[phase-XX] type: description

Types:
- feat: New feature
- fix: Bug fix
- refactor: Code improvement
- style: Formatting
- docs: Documentation
- test: Tests
- chore: Maintenance

Examples:
[phase-03] feat: define system architecture
[phase-07] feat: implement user authentication API
[phase-08] fix: button hover state on mobile
[phase-10] test: add e2e tests for checkout flow
```

### When to Commit
- After completing any feature/component
- After fixing a bug
- After completing a phase
- Before switching to different work
- At end of work session

### Commit Quality Rules
- Each commit should be atomic (one logical change)
- Code should work after each commit
- No "WIP" commits on main branches
- Write meaningful commit messages

---

## 🚨 ERROR HANDLING PROTOCOL

### When You Encounter Errors

1. **Read the error carefully** - Understand what's wrong
2. **Check if it's a known pattern** - Reference mastery docs
3. **Fix systematically** - Don't just try random things
4. **Verify the fix** - Run tests, check manually
5. **Document if novel** - Add to knowledge base

### Error Fix Limit
If you cannot fix an error after 3 attempts:
1. Stop trying
2. Document what you tried
3. Explain the error clearly
4. Ask for human guidance

### Never Do
- Don't ignore errors and continue
- Don't disable tests to make them pass
- Don't suppress warnings without understanding
- Don't comment out problematic code

---

## 📊 PROGRESS TRACKING

### Real-Time Progress in ACTIVE_PROJECT.md
```markdown
## Project: [Name]
## Started: [Date]
## Target Completion: [Date]

### Phase Progress
- [x] Phase 01: Discovery (100%)
- [x] Phase 02: Requirements (100%)
- [ ] Phase 03: Architecture (75%) ← CURRENT
- [ ] Phase 04: UX Design (0%)
...

### Current Sprint
- [x] Define database schema
- [x] Choose authentication strategy
- [ ] Design API architecture ← IN PROGRESS
- [ ] Create system diagram

### Blockers
None currently.

### Recent Decisions
See DECISION_LOG.md entries #12-15
```

### Decision Log Format
```markdown
## Decision #15
**Date**: 2026-01-07
**Phase**: 03-ARCHITECTURE
**Topic**: Database Choice
**Decision**: PostgreSQL
**Alternatives Considered**:
- MySQL: Good but less feature-rich
- MongoDB: Rejected - relational data needs SQL
**Reasoning**: Strong typing, JSON support, better for complex queries
**Approved By**: Human
**Impact**: Need to use Prisma or TypeORM for migrations
```

---

## 🎨 TECHNOLOGY SELECTION FRAMEWORK

### No Default Stack - Choose Per Project

When selecting technology, consider:

| Factor | Questions |
|--------|-----------|
| **Scale** | How many users? Concurrent requests? Data volume? |
| **Team** | Solo or team? What's the expertise? |
| **Timeline** | MVP in weeks or production in months? |
| **Budget** | Infrastructure costs acceptable? |
| **Features** | Real-time? AI? File processing? |
| **Deployment** | Serverless? Containers? Traditional? |

### Present Recommendations Like This:
```markdown
## Recommended Stack for [Project Name]

### Frontend: Next.js 14 (App Router)
**Why**: Server components for performance, great DX, Vercel deployment
**Alternatives**: 
- Remix (if you need more control over data loading)
- SvelteKit (if you prefer Svelte syntax)

### Backend: [Within Next.js API routes OR separate]
**Recommendation**: FastAPI (Python) if you need AI capabilities
**Why**: Excellent async support, auto-generated docs, Python ecosystem
**Alternatives**:
- NestJS (TypeScript consistency with frontend)
- Go (if performance is critical)

### Database: PostgreSQL
**Why**: Reliability, JSON support, excellent tooling
**Alternatives**:
- MySQL (if team is more familiar)
- MongoDB (if truly document-oriented data)

[Wait for approval before proceeding]
```

---

## 🔐 SECURITY MINDSET

### Security is Not a Phase - It's Continuous

Security considerations apply to EVERY phase:

| Phase | Security Consideration |
|-------|------------------------|
| Requirements | Define security requirements explicitly |
| Architecture | Choose secure-by-default patterns |
| API Contract | Define authentication, authorization |
| Backend | Implement all security controls |
| Frontend | Prevent XSS, secure storage |
| Testing | Include security tests |
| Phase 11 | Dedicated security audit |

### Non-Negotiable Security Standards
- All inputs validated
- All outputs encoded
- Authentication on protected routes
- Authorization checked on every action
- Secrets in environment variables
- HTTPS everywhere
- Security headers configured

---

## 📝 DOCUMENTATION STANDARDS

### Every Project Needs:

1. **README.md** - Setup, run, deploy instructions
2. **API Documentation** - Auto-generated from OpenAPI spec
3. **Architecture Diagram** - System overview
4. **Database Schema** - ERD or equivalent
5. **Environment Variables** - All config documented
6. **Deployment Guide** - Step-by-step production deploy

### Code Documentation
- Complex functions: JSDoc comment explaining why
- Non-obvious code: Inline comments
- Architecture decisions: ADRs in docs/

---

## 🚀 PROJECT INITIALIZATION

### To Start a New Project:

1. Create folder in `projects/[project-name]/`
2. Create `PROJECT_STATE.md` from template
3. Update `ACTIVE_PROJECT.md` to point to new project
4. Start Phase 01: Discovery
5. Follow phases sequentially

### Template for PROJECT_STATE.md
```markdown
# [Project Name]

## Overview
[Brief description]

## Target Users
[Who is this for]

## Key Features
[Main features]

## Tech Stack
[To be determined in Phase 03]

## Timeline
- Started: [date]
- Target MVP: [date]
- Target Production: [date]

## Current Status
Phase: 01-DISCOVERY
Progress: 0%

## Links
- Repository: [URL]
- Staging: [URL]
- Production: [URL]
```

---

## ⭐ QUALITY MANTRA

Before submitting ANY work, ask yourself:

1. **Would a senior engineer at Google approve this?**
2. **Would I be proud to show this in a code review?**
3. **Does this handle edge cases and errors?**
4. **Is this maintainable by someone else?**
5. **Does this follow the patterns in mastery docs?**

If ANY answer is "no" - **fix it before moving on**.

---

## 📋 QUICK REFERENCE

### File Locations
- Master config: `HARNESS.md` (this file)
- Current project: `ACTIVE_PROJECT.md`
- Decisions: `DECISION_LOG.md`
- Phase guides: `.harness/phases/`
- Knowledge base: `.harness/knowledge/`
- Quality checklists: `.harness/quality/`
- Sync files: `.harness/sync/`
- Projects: `projects/[name]/`

### Commands
- Start new project: Create in `projects/`, update `ACTIVE_PROJECT.md`
- Check progress: Read `ACTIVE_PROJECT.md`
- Review decisions: Read `DECISION_LOG.md`
- Get knowledge: Read relevant `.harness/knowledge/*.md`
- Verify quality: Use `.harness/quality/*.md`

---

**Now read `ACTIVE_PROJECT.md` to understand current state and continue working.**
