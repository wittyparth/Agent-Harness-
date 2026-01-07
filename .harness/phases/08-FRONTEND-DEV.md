# 💻 PHASE 08: FRONTEND DEVELOPMENT

> **Build the user interface. Components, pages, and interactions.**

---

## 🎯 PURPOSE

Implement the complete frontend:
- Design system implementation
- Component library
- All pages and views
- State management
- API integration
- Responsive layouts

**Time Investment**: 8-24 hours (depending on complexity)
**Skip Risk**: N/A - This is a core development phase

---

## 📥 INPUTS REQUIRED

1. API Contract (Phase 06) - What endpoints to call
2. UX Design (Phase 04) - User flows
3. UI Design (Phase 05) - Visual specifications
4. Type definitions from `.harness/sync/TYPES.md`

---

## 📤 EXPECTED OUTPUTS

1. **Working Frontend**
   - All pages functional
   - All components built
   - Responsive on all breakpoints

2. **Component Library**
   - All UI components
   - All component states

3. **Tests**
   - Component tests
   - E2E tests for critical paths

---

## 🔄 PROCESS

### Step 1: Project Setup

**Initialize Project:**
- Create project with appropriate framework
- Configure linting and formatting
- Set up testing framework
- Configure path aliases
- Set up environment variables

**Directory Structure:**
```
src/
├── app/              # Pages/routes
├── components/
│   ├── ui/           # Design system components
│   ├── layout/       # Layout components
│   └── features/     # Feature-specific components
├── hooks/            # Custom hooks
├── lib/              # Utilities
│   ├── api/          # API client
│   └── utils/        # Helper functions
├── stores/           # State management
├── types/            # TypeScript types
└── styles/           # Global styles
```

### Step 2: Design System Implementation

**Implement in Order:**

1. **CSS Tokens/Variables**
   - Colors (all from design system)
   - Typography (all sizes, weights, line heights)
   - Spacing scale
   - Shadows
   - Border radius
   - Transitions
   - Breakpoints

2. **Base Styles**
   - CSS reset/normalize
   - Base typography
   - Link styles
   - Focus styles

3. **Utility Classes** (if using)
   - Spacing utilities
   - Typography utilities
   - Display utilities

**Reference:** `.harness/knowledge/UI_UX_MASTERY.md`

### Step 3: Component Library

**Build in Order:**

**Level 1: Primitives**
- Button (all variants, sizes, states)
- Input (text, email, password, etc.)
- Select/Dropdown
- Checkbox
- Radio
- Switch/Toggle
- Label
- Icon component

**Level 2: Form Components**
- Form wrapper
- FormField (label + input + error)
- Form validation integration

**Level 3: Feedback Components**
- Loading spinner
- Skeleton loader
- Toast/Notification
- Alert/Banner
- Progress indicator

**Level 4: Layout Components**
- Card
- Modal/Dialog
- Drawer/Panel
- Tabs
- Accordion
- Stack (vertical/horizontal spacing)
- Container

**Level 5: Navigation Components**
- Header
- Sidebar
- Breadcrumbs
- Pagination

**For Each Component, Implement:**
- All variants from design system
- All states (default, hover, focus, active, disabled, loading, error)
- Accessibility (keyboard navigation, ARIA)
- Responsive behavior
- TypeScript props interface

### Step 4: API Client Setup

1. **Create API Client**
   - Base URL configuration
   - Authentication header injection
   - Request/response interceptors
   - Error handling
   - Type-safe methods

2. **Define API Hooks**
   - Query hooks (GET requests)
   - Mutation hooks (POST/PUT/DELETE)
   - Optimistic updates
   - Cache invalidation
   - Error handling

3. **Match API Contract**
   - Import types from sync folder
   - Ensure all endpoints covered

**Reference:** `.harness/knowledge/FRONTEND_MASTERY.md` - Data Fetching section

### Step 5: State Management Setup

1. **Server State**
   - Use server state library (React Query, SWR, etc.)
   - Configure global settings
   - Set up devtools

2. **Client State**
   - Set up global state (if needed)
   - Define stores for:
     - Auth state (current user)
     - UI state (theme, sidebar)

3. **Form State**
   - Form library setup
   - Validation schema integration

**Reference:** `.harness/knowledge/FRONTEND_MASTERY.md` - State Management section

### Step 6: Authentication UI

**Implement in Order:**

1. **Login Page**
   - Email/password form
   - Validation
   - Error handling
   - Success redirect
   - "Remember me" option
   - Link to forgot password
   - Link to signup

2. **Registration Page**
   - All required fields
   - Password requirements shown
   - Validation
   - Terms acceptance (if needed)
   - Success confirmation
   - Email verification notice

3. **Forgot Password Page**
   - Email input
   - Success message (same for found/not found)
   - Link back to login

4. **Reset Password Page**
   - Token validation
   - New password form
   - Password requirements
   - Success redirect to login

5. **Email Verification**
   - Token validation
   - Success/failure UI
   - Resend option

6. **OAuth Buttons** (if applicable)
   - Google, GitHub, etc.
   - Redirect handling
   - Error handling

7. **Protected Route Wrapper**
   - Redirect unauthenticated to login
   - Store intended destination
   - Redirect back after login

### Step 7: Layout Implementation

1. **App Shell**
   - Header (with auth state)
   - Navigation (with active states)
   - Sidebar (if applicable)
   - Footer
   - Mobile navigation

2. **Page Layouts**
   - Auth layout (login, signup)
   - Dashboard layout (authenticated pages)
   - Public layout (marketing pages)

3. **Responsive Behavior**
   - Mobile navigation pattern
   - Responsive sidebar
   - Adaptive layouts

### Step 8: Page Implementation

**For Each Page, Implement:**

1. **Route Setup**
   - Path configuration
   - Meta tags (title, description)
   - Auth requirements

2. **Data Fetching**
   - Load data on mount
   - Loading state (skeleton)
   - Error state (retry option)
   - Empty state

3. **Page Content**
   - Layout from wireframes
   - Components from library
   - Interactions from spec

4. **Page States**
   - Loading
   - Empty
   - Error
   - Success
   - Partial (some data loaded)

**Implementation Order:**
1. Authentication pages (login, signup, etc.)
2. Main dashboard/home
3. Core feature pages
4. Settings/profile
5. Secondary features
6. Error pages (404, 500)

### Step 9: Form Implementation

**For Each Form:**

1. **Setup**
   - Form library integration
   - Validation schema
   - Default values

2. **Fields**
   - Correct input types
   - Labels and helper text
   - Validation messages

3. **Submission**
   - Loading state on button
   - Disable during submission
   - Success handling
   - Error handling (server errors)

4. **UX**
   - Auto-focus first field
   - Submit on Enter
   - Preserve input on error
   - Focus first error field

**Reference:** `.harness/knowledge/FRONTEND_MASTERY.md` - Forms section

### Step 10: Error Handling

1. **Error Boundaries**
   - Wrap page routes
   - Fallback UI
   - Reset option

2. **API Errors**
   - Toast for transient errors
   - Inline for field errors
   - Full page for critical errors

3. **Network Errors**
   - Offline indicator
   - Retry options
   - Graceful degradation

**Reference:** `.harness/knowledge/FRONTEND_MASTERY.md` - Error Handling section

### Step 11: Performance Optimization

1. **Code Splitting**
   - Route-based splitting
   - Component lazy loading
   - Dynamic imports for heavy libraries

2. **Image Optimization**
   - Proper sizing
   - Modern formats (WebP)
   - Lazy loading

3. **Memoization**
   - Expensive computations
   - Callbacks for child components

**Reference:** `.harness/knowledge/FRONTEND_MASTERY.md` - Performance section

### Step 12: Accessibility Implementation

1. **Keyboard Navigation**
   - All interactive elements reachable
   - Focus management in modals
   - Skip link

2. **Screen Reader**
   - Semantic HTML
   - ARIA labels where needed
   - Live regions for dynamic content

3. **Visual**
   - Focus indicators
   - Color contrast
   - Reduced motion support

**Reference:** `.harness/knowledge/FRONTEND_MASTERY.md` - Accessibility section

### Step 13: Testing

1. **Component Tests**
   - Render correctly
   - Handle interactions
   - Show all states

2. **Integration Tests**
   - User flows
   - API integration
   - Form submission

3. **E2E Tests**
   - Critical user journeys
   - Authentication flow
   - Main feature flow

**Reference:** `.harness/knowledge/TESTING_MASTERY.md`

---

## ✅ QUALITY GATE

Before proceeding to Phase 09, verify:

### Functionality
- [ ] All pages implemented
- [ ] All forms work correctly
- [ ] Authentication flows complete
- [ ] Navigation works
- [ ] API integration working
- [ ] Error handling in place

### Visual
- [ ] Matches design system
- [ ] All component states implemented
- [ ] Consistent styling
- [ ] No visual bugs

### Responsiveness
- [ ] Works at 320px (mobile)
- [ ] Works at 768px (tablet)
- [ ] Works at 1024px+ (desktop)
- [ ] Touch-friendly on mobile

### Accessibility
- [ ] Keyboard navigable
- [ ] Focus indicators visible
- [ ] Screen reader tested
- [ ] Color contrast passes

### Performance
- [ ] Lighthouse score > 90
- [ ] No layout shifts
- [ ] Images optimized
- [ ] Bundle size reasonable

### Code Quality
- [ ] No linting errors
- [ ] No type errors
- [ ] No console errors
- [ ] Tests pass

- [ ] ACTIVE_PROJECT.md updated
- [ ] Git commit made

---

## 📚 KNOWLEDGE REFERENCES

- `.harness/knowledge/FRONTEND_MASTERY.md` - Complete frontend guide
- `.harness/knowledge/UI_UX_MASTERY.md` - Design implementation
- `.harness/knowledge/TESTING_MASTERY.md` - Testing strategy

---

## ⚠️ COMMON MISTAKES

### Mistake 1: Building Pages Before Components
Build the component library first. Pages compose components.

### Mistake 2: Ignoring Loading States
Every async operation needs a loading state.

### Mistake 3: Forgetting Error States
Every API call can fail. Handle it.

### Mistake 4: Desktop-Only Development
Test on mobile throughout, not at the end.

### Mistake 5: Skipping Accessibility
Build it in from the start.

---

## 💡 TIPS

1. **Component-first**: Build components in isolation before using in pages

2. **Use real data early**: Fake data hides problems

3. **Test on slow network**: Chrome DevTools throttling

4. **Check all states**: Loading, empty, error, success

5. **Mobile test often**: Use actual devices

---

**Phase Complete? Update ACTIVE_PROJECT.md and proceed to Phase 09: Integration.**
