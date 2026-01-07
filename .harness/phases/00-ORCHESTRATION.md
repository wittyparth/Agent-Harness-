# 🎯 PHASE 00: ORCHESTRATION GUIDE

> **This document explains how all phases work together and how to navigate them.**

---

## 🔄 THE COMPLETE DEVELOPMENT LIFECYCLE

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        FULL SDLC FLOW                                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  [DISCOVERY] → [REQUIREMENTS] → [ARCHITECTURE] → [DESIGN] → [CONTRACT] │
│       │              │               │              │            │       │
│       ▼              ▼               ▼              ▼            ▼       │
│   Validate       Define          Choose         Create        Define    │
│   the idea       features        tech stack     UI/UX         APIs      │
│                                                                          │
│                              ↓                                          │
│                                                                          │
│  [BACKEND DEV] ←──────→ [FRONTEND DEV]                                  │
│       │                       │                                          │
│       └───────────┬───────────┘                                          │
│                   ▼                                                      │
│            [INTEGRATION]                                                 │
│                   │                                                      │
│                   ▼                                                      │
│  [TESTING] → [SECURITY] → [PERFORMANCE] → [DEVOPS] → [DOCS] → [LAUNCH] │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 PHASE OVERVIEW

| Phase | Name | Purpose | Typical Duration | Key Output |
|-------|------|---------|------------------|------------|
| 01 | DISCOVERY | Validate idea, understand market | 1-2 hours | Validated concept document |
| 02 | REQUIREMENTS | Define features, user stories | 2-4 hours | Complete requirements doc |
| 03 | ARCHITECTURE | System design, tech choices | 2-4 hours | Architecture decision record |
| 04 | UX-DESIGN | User flows, wireframes | 2-4 hours | User flow diagrams |
| 05 | UI-DESIGN | Visual design, components | 4-8 hours | Design system document |
| 06 | API-CONTRACT | Define all APIs | 2-4 hours | OpenAPI specification |
| 07 | BACKEND-DEV | Implement server | 8-24 hours | Working API |
| 08 | FRONTEND-DEV | Implement UI | 8-24 hours | Working UI |
| 09 | INTEGRATION | Connect FE + BE | 2-4 hours | Integrated application |
| 10 | TESTING | Comprehensive tests | 4-8 hours | Test suite |
| 11 | SECURITY | Security audit | 2-4 hours | Security report |
| 12 | PERFORMANCE | Optimization | 2-4 hours | Optimized application |
| 13 | DEVOPS | Containerization, CI/CD | 2-4 hours | Deployment config |
| 14 | DOCUMENTATION | All documentation | 2-4 hours | Complete docs |
| 15 | LAUNCH | Final checks, deploy | 1-2 hours | Live application |

---

## 🚦 PHASE RULES

### Sequential Flow (Default)
```
Phase N must be COMPLETE before starting Phase N+1
```

Exceptions:
- Phases 07 (Backend) and 08 (Frontend) can run in PARALLEL after Phase 06
- Minor documentation (Phase 14) can happen throughout

### Quality Gates
Every phase has a quality gate checklist. The gate MUST pass before proceeding.

```
[Phase Work] → [Quality Gate Check] → [Gate Passes?]
                                            │
                    ┌───────────────────────┴──────────────────────┐
                    │                                              │
                   YES                                            NO
                    │                                              │
                    ▼                                              ▼
            [Proceed to Next Phase]                    [Fix Issues First]
```

### Phase Completion Criteria
A phase is complete when:
1. ✅ All required outputs exist
2. ✅ Quality gate checklist passes
3. ✅ State files are updated
4. ✅ Git commit is made

---

## 📁 PHASE FILE STRUCTURE

Each phase file (`.harness/phases/XX-NAME.md`) contains:

```markdown
# Phase XX: NAME

## 🎯 Purpose
What this phase achieves

## 📥 Inputs Required
What must exist before starting

## 📤 Expected Outputs
What must exist when complete

## 🔄 Process
Step-by-step guide with expert knowledge

## ✅ Quality Gate
Checklist that must pass

## 📚 Knowledge References
Links to relevant mastery documents

## ⚠️ Common Mistakes
What to avoid

## 💡 Tips
Pro tips for this phase
```

---

## 🔗 PHASE DEPENDENCIES

### Hard Dependencies (Must Complete First)
```
01 → 02 → 03 → 04 → 05 → 06 → [07 & 08] → 09 → 10 → 11 → 12 → 13 → 14 → 15
```

### Knowledge Dependencies (Reference During Phase)
```
Phase 03 (Architecture)  → BACKEND_MASTERY.md, DATABASE_MASTERY.md
Phase 04 (UX Design)     → UI_UX_MASTERY.md
Phase 05 (UI Design)     → UI_UX_MASTERY.md, FRONTEND_MASTERY.md
Phase 06 (API Contract)  → BACKEND_MASTERY.md
Phase 07 (Backend Dev)   → BACKEND_MASTERY.md, DATABASE_MASTERY.md, SECURITY_MASTERY.md
Phase 08 (Frontend Dev)  → FRONTEND_MASTERY.md, UI_UX_MASTERY.md
Phase 10 (Testing)       → TESTING_MASTERY.md
Phase 11 (Security)      → SECURITY_MASTERY.md
Phase 12 (Performance)   → FRONTEND_MASTERY.md, BACKEND_MASTERY.md
Phase 13 (DevOps)        → DEVOPS_MASTERY.md
```

---

## 🎛️ PHASE NAVIGATION

### Starting a Phase
1. Confirm previous phase is complete
2. Read the phase file completely
3. Review referenced knowledge documents
4. Prepare required inputs
5. Begin the process

### During a Phase
1. Follow the process step-by-step
2. Update ACTIVE_PROJECT.md as you progress
3. Log decisions in DECISION_LOG.md
4. Make incremental git commits

### Completing a Phase
1. Verify all outputs exist
2. Go through quality gate checklist
3. Fix any failing items
4. Update ACTIVE_PROJECT.md (mark phase complete)
5. Make completion git commit
6. Proceed to next phase

---

## 🔀 PARALLEL PHASES

### Backend + Frontend (Phases 07 & 08)
These phases CAN run in parallel because:
- Phase 06 defines the API contract (source of truth)
- Frontend can mock API responses based on spec
- Backend implements to spec
- Both converge in Phase 09 (Integration)

### Coordination Requirements
When working on parallel phases:
1. API spec changes require updating BOTH sides
2. Type definitions must stay in sync
3. Integration tests validate compatibility

---

## ⏪ GOING BACK TO A PREVIOUS PHASE

Sometimes you need to revisit a previous phase. Rules:

### Valid Reasons to Go Back
- Requirements changed (discovered in later phase)
- Technical constraint found (need architectural change)
- User feedback (design needs update)

### Process for Going Back
1. Document WHY in DECISION_LOG.md
2. Update ACTIVE_PROJECT.md to new current phase
3. Make git commit noting the rollback
4. Complete the phase again
5. Propagate changes to all affected subsequent phases

### What NOT to Do
- Don't skip re-running affected phases
- Don't leave phases inconsistent
- Don't rush through re-work

---

## 📊 PROGRESS TRACKING

### Phase Progress Calculation
```
Phase Progress = (Completed Steps / Total Steps) × 100%
```

### Overall Project Progress
```
Overall Progress = Σ(Phase Weight × Phase Completion) / Total Weight

Phase Weights (approximate):
- Discovery:      5%
- Requirements:   5%
- Architecture:   5%
- UX Design:      5%
- UI Design:     10%
- API Contract:   5%
- Backend Dev:   20%
- Frontend Dev:  20%
- Integration:    5%
- Testing:       10%
- Security:       3%
- Performance:    2%
- DevOps:         3%
- Documentation:  2%
- Launch:         5%
```

---

## 🚨 BLOCKERS

### Types of Blockers
1. **Missing Requirement**: Need clarification from human
2. **Technical Limitation**: Need to find alternative approach
3. **External Dependency**: Waiting for third-party
4. **Decision Needed**: Multiple valid options, need human choice

### Handling Blockers
1. Document blocker in ACTIVE_PROJECT.md
2. Assess if work can continue on other tasks
3. If blocked completely, notify human
4. Once resolved, document resolution

---

## 🔄 ITERATION WITHIN A PHASE

### Build → Review → Improve Cycle
```
[Build Initial Version] → [Review Against Standards] → [Improve Based on Gaps]
         ↑                                                       │
         └───────────────────────────────────────────────────────┘
```

### When to Stop Iterating
- All quality gate items pass
- Standards from mastery docs are met
- No obvious improvements remain
- Diminishing returns territory

---

## 📋 QUICK REFERENCE

### Phase Status Symbols
- `[ ]` Not started
- `[~]` In progress
- `[x]` Complete
- `[!]` Blocked

### Common Commands
```bash
# Check current phase
Read ACTIVE_PROJECT.md

# Start next phase
Update ACTIVE_PROJECT.md, read phase file

# Complete phase
Verify quality gate, update ACTIVE_PROJECT.md, git commit

# Log decision
Add entry to DECISION_LOG.md
```

---

**Now read the phase file for your current phase and begin work.**
