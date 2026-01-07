# 🎨 PHASE 04: UX DESIGN

> **Define HOW users will interact with the system. User flows, not visuals yet.**

---

## 🎯 PURPOSE

Design the user experience before any visual design or code:
- Map all user journeys
- Define screen-by-screen flows
- Ensure intuitive interactions
- Identify all states and edge cases
- Create wireframes (structure only)

**Time Investment**: 2-4 hours
**Skip Risk**: Confusing UX, endless redesigns, frustrated users

---

## 📥 INPUTS REQUIRED

1. Requirements Document (Phase 02)
2. User Stories with acceptance criteria
3. Architecture decisions (Phase 03)

---

## 📤 EXPECTED OUTPUTS

1. **User Flow Diagrams** (`projects/[name]/docs/USER_FLOWS.md`)
   - Complete journey maps
   - Decision points
   - Error paths

2. **Wireframes** (`projects/[name]/docs/WIREFRAMES/`)
   - Low-fidelity layouts
   - Screen structure
   - Component placement

3. **Interaction Specifications** (`projects/[name]/docs/INTERACTIONS.md`)
   - How elements behave
   - Transitions and feedback

---

## 🔄 PROCESS

### Step 1: Identify User Types

Define each distinct user type:
- Primary user persona
- Secondary user personas
- Admin users (if applicable)
- Guest/anonymous users

For each persona, note:
- Goals (what they want to achieve)
- Context (when/where they use the app)
- Technical proficiency
- Frequency of use

### Step 2: Map Core User Journeys

For each major feature, map the complete journey:

**Journey Map Format:**
```
[Entry Point] → [Step 1] → [Step 2] → ... → [Goal Achieved]
                    ↓
              [Error Path] → [Recovery]
```

**Essential Journeys to Map:**
1. New user onboarding (signup → first value)
2. Returning user login
3. Core action completion (main value of app)
4. Error recovery
5. Account management

**For Each Step, Define:**
- What user sees
- What user can do
- What happens next
- What can go wrong
- How to recover from errors

### Step 3: Screen Inventory

List every screen/view needed:

**Screen Categories:**
- Authentication (login, signup, forgot password, reset password)
- Onboarding (welcome, setup wizard, first-use guidance)
- Main navigation (home, dashboard)
- Feature screens (one per major feature)
- Settings/preferences
- Profile/account
- Error pages (404, 500, offline)
- Empty states
- Loading states

**For Each Screen, Note:**
- Purpose
- Entry points (how user gets here)
- Exit points (where user can go)
- Key components
- States (loading, empty, error, success, partial)

### Step 4: Define Screen States

**Every screen has multiple states:**

| State | What to Show |
|-------|--------------|
| Loading | Skeleton that matches content shape |
| Empty | Helpful message + action to add first item |
| Error | What went wrong + how to fix/retry |
| Partial | Some data loaded, more loading |
| Complete | Full content |
| Offline | Network unavailable message |

### Step 5: Create Low-Fidelity Wireframes

**Wireframe Guidelines:**
- Black and white / grayscale only
- No styling details (colors, fonts, shadows)
- Focus on layout and structure
- Show content hierarchy
- Indicate interactive elements
- Show different states

**Each Wireframe Should Show:**
- Header/navigation
- Main content area layout
- Key interactive elements
- Content placeholder shapes
- Call-to-action placement

### Step 6: Define Interactions

**For Each Interactive Element, Specify:**

| Element | Trigger | Feedback | Result |
|---------|---------|----------|--------|
| Submit button | Click | Disable, show spinner | Form submits |
| Delete button | Click | Confirmation modal | Item deleted |
| Search input | Type | Debounced results | Results shown |

**Common Interaction Patterns:**

| Pattern | When to Use |
|---------|-------------|
| Inline editing | Quick single-field edits |
| Modal form | Multi-field with focus |
| Page navigation | Complex multi-step process |
| Slide panel | Detail view without losing context |
| Toast/notification | Confirmation of action |
| Confirmation dialog | Destructive actions |

### Step 7: Navigation Design

**Define Navigation Structure:**
- Primary navigation (always visible)
- Secondary navigation (within sections)
- Breadcrumbs (deep hierarchy)
- Quick actions

**Navigation Principles:**
- User knows where they are
- User knows where they can go
- User can get back easily
- Important actions are visible
- Navigation is consistent

### Step 8: Form Flow Design

**For Each Form, Define:**
- Field order (logical grouping)
- Required vs optional fields
- Field types and input methods
- Validation timing (on blur, on submit)
- Error message location
- Success confirmation

**Form UX Principles:**
- Ask for minimum necessary
- Group related fields
- Use appropriate input types
- Show password requirements upfront
- Auto-focus first field
- Submit on Enter
- Preserve input on error

### Step 9: Error Handling UX

**Error Categories:**
1. Validation errors (field-level)
2. Business logic errors (form-level)
3. System errors (page-level)
4. Network errors (offline)

**For Each Error Type, Define:**
- Message location
- Message content (helpful, not technical)
- Recovery action
- Visual treatment

### Step 10: Mobile Considerations

**Responsive Decisions:**
- What stays on mobile
- What changes on mobile
- What hides on mobile
- Touch target sizes (min 44px)
- Thumb-friendly placement
- Mobile navigation pattern

---

## ✅ QUALITY GATE

Before proceeding to Phase 05, verify:

- [ ] All user personas defined
- [ ] Core user journeys mapped
- [ ] All screens identified
- [ ] All screen states defined (loading, empty, error)
- [ ] Wireframes created for key screens
- [ ] Interactions specified
- [ ] Navigation structure defined
- [ ] Form flows designed
- [ ] Error handling UX defined
- [ ] Mobile considerations documented
- [ ] User has reviewed and approved flows
- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

- `.harness/knowledge/UI_UX_MASTERY.md` - Design principles

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Skipping Wireframes
Going straight to visual design leads to endless revisions.
Get structure right first.

### Mistake 2: Forgetting Error States
Every screen can error. Design for it.

### Mistake 3: Ignoring Empty States
First-time users see empty states. Make them helpful.

### Mistake 4: Desktop-Only Thinking
Design for mobile from the start.

### Mistake 5: Assuming Users Know
Users don't read instructions. Design for discovery.

---

## 💡 TIPS

1. **Think in user tasks**: Not "product page" but "user finds product"

2. **Draw on paper first**: Fastest way to explore ideas

3. **Walk through as user**: Physically click through flows

4. **Test wireframes early**: Low cost to change now

5. **Document decisions**: WHY this flow, not just what

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 05: UI Design.**
