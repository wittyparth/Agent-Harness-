# 📊 ACTIVE PROJECT STATUS

> **This file is the persistent memory. Read this at the START of every session.**
> **Update this file after every significant action.**

---

## ⚠️ CURRENT STATUS

```
┌─────────────────────────────────────────────────────────┐
│  NO ACTIVE PROJECT                                       │
│                                                          │
│  To start a new project:                                │
│  1. Run workflow: Create new project                    │
│  2. Answer the discovery questions                      │
│  3. This file will be updated automatically             │
└─────────────────────────────────────────────────────────┘
```

---

## 📁 WHEN A PROJECT IS ACTIVE, THIS FILE SHOWS:

### Project Overview
```markdown
## Project: [Project Name]
## Type: [SaaS / Marketplace / E-commerce / AI App / etc.]
## Started: [Date]
## Target Completion: [Date]
## Repository: [URL]
## Staging URL: [URL]
## Production URL: [URL]
```

### Current Phase
```markdown
## Current Phase: [01-15] - [Phase Name]
## Phase Progress: [X%]
## Current Task: [What you're working on right now]
## Next Task: [What comes after current task]
```

### Phase Completion Status
```markdown
### Completed Phases
- [x] Phase 01: DISCOVERY (100%) - Completed [date]
- [x] Phase 02: REQUIREMENTS (100%) - Completed [date]
- [ ] Phase 03: ARCHITECTURE (50%) ← CURRENT
- [ ] Phase 04: UX-DESIGN (0%)
- [ ] Phase 05: UI-DESIGN (0%)
- [ ] Phase 06: API-CONTRACT (0%)
- [ ] Phase 07: BACKEND-DEV (0%)
- [ ] Phase 08: FRONTEND-DEV (0%)
- [ ] Phase 09: INTEGRATION (0%)
- [ ] Phase 10: TESTING (0%)
- [ ] Phase 11: SECURITY (0%)
- [ ] Phase 12: PERFORMANCE (0%)
- [ ] Phase 13: DEVOPS (0%)
- [ ] Phase 14: DOCUMENTATION (0%)
- [ ] Phase 15: LAUNCH (0%)
```

### Current Sprint Tasks
```markdown
### Sprint Tasks (Current Phase)
- [x] Task 1: Completed
- [x] Task 2: Completed
- [ ] Task 3: In Progress ← CURRENT
- [ ] Task 4: Pending
- [ ] Task 5: Pending
```

### Blockers & Decisions
```markdown
### Blockers
- None currently

### Pending Decisions (Need Human Input)
- Decision #XX: [Brief description] - See DECISION_LOG.md

### Recent Decisions Made
- Decision #15: Chose PostgreSQL for database (see DECISION_LOG.md #15)
- Decision #14: JWT with refresh tokens for auth (see DECISION_LOG.md #14)
```

### Key Links & References
```markdown
### Project Files
- Requirements: projects/[name]/docs/REQUIREMENTS.md
- Architecture: projects/[name]/docs/ARCHITECTURE.md
- API Spec: .harness/sync/API_SPEC.yaml
- Design System: projects/[name]/docs/DESIGN_SYSTEM.md

### External Links
- Figma: [URL]
- GitHub: [URL]
- Staging: [URL]
- Production: [URL]
```

### Session Log
```markdown
### Last Session Summary
**Date**: [Date]
**Duration**: [X hours]
**What was done**:
- Completed user authentication API
- Added rate limiting middleware
- Fixed bug in login form

**What to do next**:
1. Implement password reset flow
2. Add email verification
3. Write tests for auth module
```

---

## 📝 HOW TO UPDATE THIS FILE

### After Starting Work
1. Read entire file to understand current state
2. Confirm current phase and task
3. Proceed with work

### After Completing a Task
1. Mark task as complete [x]
2. Update progress percentage
3. Add to session log

### After Completing a Phase
1. Mark phase as 100% complete
2. Increment to next phase
3. Add phase completion to session log
4. Make git commit: `[phase-XX] complete: [phase name]`

### After Making a Decision
1. Log decision in DECISION_LOG.md
2. Reference decision number here
3. Update affected project files

### At End of Session
1. Update "Last Session Summary"
2. Clearly state "What to do next"
3. Make git commit with progress

---

## 🚀 STARTING A NEW PROJECT

To initialize a new project, follow these steps:

1. **Create Project Folder**
   ```
   projects/[project-name]/
   ```

2. **Create Project State File**
   ```
   projects/[project-name]/PROJECT_STATE.md
   ```

3. **Update This File**
   - Fill in project overview section
   - Set current phase to 01-DISCOVERY
   - Set all phases to 0%

4. **Begin Phase 01**
   - Read `.harness/phases/01-DISCOVERY.md`
   - Follow the discovery process
   - Document findings

5. **First Git Commit**
   ```
   [phase-01] init: project setup for [project-name]
   ```

---

## ⚡ QUICK STATUS CHECK

Use this section for rapid status assessment:

```
PROJECT:        [None]
PHASE:          [None]
PROGRESS:       [0%]
BLOCKERS:       [None]
LAST UPDATED:   [Never]
NEXT ACTION:    [Start a new project]
```

---

**When you see active project data above, continue from where it left off.**
**When empty, ask the user what project they want to build.**
