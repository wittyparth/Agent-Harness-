# ✨ PHASE 05: UI DESIGN

> **Create the visual design system. Colors, typography, components, and polish.**

---

## 🎯 PURPOSE

Transform wireframes into beautiful, consistent visual designs:
- Define complete design system
- Create component library specifications
- Establish visual language
- Ensure accessibility
- Define micro-interactions

**Time Investment**: 4-8 hours
**Skip Risk**: Inconsistent UI, unprofessional look, accessibility issues

---

## 📥 INPUTS REQUIRED

1. UX Design outputs (Phase 04)
   - User flows
   - Wireframes
   - Interaction specifications
2. Brand guidelines (if any exist)

---

## 📤 EXPECTED OUTPUTS

1. **Design System Document** (`projects/[name]/docs/DESIGN_SYSTEM.md`)
   - Color palette
   - Typography scale
   - Spacing system
   - Component specifications

2. **Component Library** (documentation)
   - All UI components defined
   - States for each component
   - Usage guidelines

3. **High-Fidelity Mockups** (key screens)
   - Visual design applied
   - All states shown

---

## 🔄 PROCESS

### Step 1: Define Color Palette

**Primary Colors (Brand):**
- Primary: Main brand color (used for CTAs, links, key actions)
- Primary variants: Lighter/darker for hover, disabled states

**Secondary Colors (Accent):**
- Secondary: Complementary accent color
- Secondary variants

**Semantic Colors (Meaning):**
- Success: Green tones (confirmations, positive actions)
- Warning: Yellow/amber tones (caution, attention)
- Error: Red tones (failures, destructive actions)
- Info: Blue tones (informational messages)

**Neutral Colors (UI):**
- Background colors (page, card, elevated)
- Text colors (primary, secondary, muted, disabled)
- Border colors
- Shadow colors

**Color Specification Format:**
```
Color Name: [Name]
Hex: #XXXXXX
Usage: [Where to use]
Accessibility: [Contrast info]
```

**Dark Mode Colors (if applicable):**
- All colors need dark mode variants
- Test contrast in both modes

### Step 2: Define Typography

**Font Selection:**
- Primary font (headings and body)
- Secondary font (if needed for contrast)
- Monospace font (for code, if applicable)

**Type Scale:**
| Name | Size | Line Height | Weight | Usage |
|------|------|-------------|--------|-------|
| H1 | 36-48px | 1.2 | Bold | Page titles |
| H2 | 28-36px | 1.25 | Semibold | Section headers |
| H3 | 22-28px | 1.3 | Semibold | Subsections |
| H4 | 18-22px | 1.35 | Medium | Card headers |
| Body | 16px | 1.5 | Normal | Main content |
| Small | 14px | 1.5 | Normal | Secondary text |
| Caption | 12px | 1.4 | Normal | Labels, hints |

**Responsive Typography:**
- Fluid scaling or breakpoint-based adjustments
- Mobile sizes generally smaller

### Step 3: Define Spacing System

**8-Point Grid:**
```
0: 0px
1: 4px   (tight)
2: 8px   (compact)
3: 12px  (comfortable)
4: 16px  (standard)
6: 24px  (related groups)
8: 32px  (section padding)
12: 48px (major sections)
16: 64px (page sections)
```

**Usage Guidelines:**
- Related elements: 8-16px
- Card padding: 16-24px
- Section spacing: 32-64px
- Page margins: 16px (mobile) to 64px (desktop)

### Step 4: Define Component Library

**Core Components:**

#### Buttons
| Variant | Usage | States |
|---------|-------|--------|
| Primary | Main actions, CTAs | default, hover, active, disabled, loading |
| Secondary | Secondary actions | all states |
| Outline | Alternative actions | all states |
| Ghost | Minimal emphasis | all states |
| Destructive | Delete, remove | all states |
| Link | Inline actions | default, hover |

**Button Sizes:**
- Small: 32px height (compact UIs)
- Default: 40px height (standard)
- Large: 48px height (prominent actions)

#### Form Inputs
| Component | Variants | States |
|-----------|----------|--------|
| Text Input | Default, with icon, with action | empty, filled, focused, error, disabled |
| Select | Single, searchable | all states |
| Checkbox | Default, indeterminate | unchecked, checked, disabled |
| Radio | Default | unchecked, checked, disabled |
| Switch/Toggle | Default | off, on, disabled |
| Textarea | Default, auto-grow | all states |

#### Feedback Components
- Toast/Notification: success, warning, error, info
- Alert/Banner: same variants
- Progress: determinate, indeterminate
- Skeleton: loading placeholder

#### Layout Components
- Card: with/without header, footer
- Modal/Dialog: sizes (sm, md, lg)
- Drawer/Slide-panel
- Tabs
- Accordion

#### Navigation Components
- Header: with logo, nav, actions
- Sidebar: with icons, collapsed state
- Breadcrumbs
- Pagination

### Step 5: Define Effects and Elevation

**Shadows (Elevation):**
```
Level 0: No shadow (flat)
Level 1: 0 1px 2px rgba(0,0,0,0.05) (subtle, cards)
Level 2: 0 4px 6px rgba(0,0,0,0.1) (raised, dropdown)
Level 3: 0 10px 15px rgba(0,0,0,0.1) (modal)
Level 4: 0 20px 25px rgba(0,0,0,0.1) (overlay)
```

**Border Radius:**
```
None: 0px
Small: 4px (buttons, tags)
Medium: 8px (cards, inputs)
Large: 12px (modals, panels)
Full: 9999px (pills, avatars)
```

### Step 6: Define Micro-Interactions

**Transitions:**
- Duration: 150ms (fast), 200ms (normal), 300ms (emphasized)
- Easing: ease-out for entrances, ease-in for exits

**Standard Animations:**
| Action | Animation |
|--------|-----------|
| Hover | Background color shift (150ms) |
| Focus | Ring appears (fast) |
| Button press | Scale down slightly |
| Modal open | Fade in + scale up |
| Toast appear | Slide in from edge |
| Loading | Skeleton shimmer |
| Success | Checkmark draw |

### Step 7: Define Responsive Breakpoints

```
Mobile: 0 - 639px
Tablet: 640px - 1023px
Desktop: 1024px - 1279px
Large: 1280px+
```

**Responsive Patterns:**
- Stack horizontal layouts on mobile
- Hide secondary navigation on mobile
- Full-width cards on mobile
- Adjust spacing per breakpoint
- Touch targets min 44px on mobile

### Step 8: Accessibility Specifications

**Color Contrast:**
- Normal text: 4.5:1 minimum
- Large text (18px+): 3:1 minimum
- UI elements: 3:1 minimum

**Focus Indicators:**
- All interactive elements must have visible focus
- Focus ring: 2px offset, contrasting color

**Touch Targets:**
- Minimum 44x44px on mobile
- Minimum 8px spacing between targets

**Motion:**
- Respect prefers-reduced-motion
- No flashing content

### Step 9: Create High-Fidelity Mockups

**Priority Screens to Design:**
1. Landing/home page
2. Login/signup
3. Main dashboard or primary view
4. Key feature screen
5. Settings page
6. Empty states
7. Error states
8. Mobile versions of above

**Mockup Requirements:**
- Use actual design system values
- Show real content (not lorem ipsum)
- Include all states
- Show responsive variations

### Step 10: Document Everything

**Design System Document Should Include:**
- Color palette with hex codes and usage
- Typography scale with all properties
- Spacing scale and guidelines
- Component specifications with all variants/states
- Icon specifications
- Animation/transition specifications
- Accessibility guidelines

---

## ✅ QUALITY GATE

Before proceeding to Phase 06, verify:

- [ ] Color palette defined (including dark mode if applicable)
- [ ] Typography scale defined
- [ ] Spacing system defined
- [ ] All core components specified
- [ ] All component states defined
- [ ] Shadows/elevation defined
- [ ] Micro-interactions specified
- [ ] Responsive breakpoints defined
- [ ] Accessibility requirements documented
- [ ] High-fidelity mockups for key screens
- [ ] Design system document created
- [ ] User has approved visual direction
- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

- `.harness/knowledge/UI_UX_MASTERY.md` - Design principles and tokens
- `.harness/knowledge/FRONTEND_MASTERY.md` - Component implementation

---

## ⚠️ COMMON MISTAKES

### Mistake 1: No Design System
Ad-hoc styling leads to inconsistency. Define system first.

### Mistake 2: Ignoring States
Designing only the "happy path" appearance.

### Mistake 3: Accessibility as Afterthought
Color contrast must be designed in, not fixed later.

### Mistake 4: Not Testing with Real Content
Designs break with long names, missing images, etc.

### Mistake 5: Over-Designing
Keep it simple. Complexity is easy; simplicity is hard.

---

## 💡 TIPS

1. **Start with constraints**: Limit to 2-3 colors, 4-5 font sizes

2. **Design the hard cases**: Long text, error states, empty states

3. **Test on real devices**: Colors look different on different screens

4. **Use a design tool**: Figma, Sketch, or similar for consistency

5. **Build a token file**: CSS variables or design tokens for handoff

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 06: API Contract.**
