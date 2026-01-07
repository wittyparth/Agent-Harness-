# 🎨 UI/UX MASTERY

> **Deep expertise for creating beautiful, usable, and accessible interfaces.**
> **Reference this document during Phases 04, 05, 08.**

---

## 🎯 UI/UX EXCELLENCE STANDARDS

A production-grade interface must achieve:
- **Visual Polish**: Looks like it was designed by professionals
- **Usability**: Users accomplish goals without frustration
- **Accessibility**: WCAG 2.1 AA compliant minimum
- **Responsiveness**: Perfect on 320px to 4K screens
- **Performance**: FCP < 1.8s, CLS < 0.1
- **Consistency**: Design system enforced throughout

---

## 🎨 COLOR SYSTEM

### Color Palette Structure

```css
/* Use OKLCH for perceptual uniformity */
:root {
  /* Primary - Brand color */
  --primary-50: oklch(97% 0.01 250);
  --primary-100: oklch(94% 0.02 250);
  --primary-200: oklch(88% 0.04 250);
  --primary-300: oklch(80% 0.08 250);
  --primary-400: oklch(70% 0.12 250);
  --primary-500: oklch(60% 0.15 250);  /* Main */
  --primary-600: oklch(50% 0.15 250);
  --primary-700: oklch(40% 0.12 250);
  --primary-800: oklch(30% 0.08 250);
  --primary-900: oklch(20% 0.06 250);
  --primary-950: oklch(12% 0.04 250);
  
  /* Semantic Colors */
  --success-500: oklch(65% 0.18 145);
  --warning-500: oklch(75% 0.15 85);
  --error-500: oklch(60% 0.22 25);
  --info-500: oklch(60% 0.15 250);
  
  /* Neutrals (for text, borders, backgrounds) */
  --neutral-50: oklch(98% 0.005 250);
  --neutral-100: oklch(96% 0.005 250);
  --neutral-200: oklch(92% 0.005 250);
  --neutral-300: oklch(87% 0.008 250);
  --neutral-400: oklch(70% 0.01 250);
  --neutral-500: oklch(55% 0.01 250);
  --neutral-600: oklch(45% 0.01 250);
  --neutral-700: oklch(35% 0.01 250);
  --neutral-800: oklch(25% 0.01 250);
  --neutral-900: oklch(15% 0.01 250);
  --neutral-950: oklch(10% 0.01 250);
}

/* Semantic tokens - what to actually use */
:root {
  --background: var(--neutral-50);
  --foreground: var(--neutral-900);
  --muted: var(--neutral-100);
  --muted-foreground: var(--neutral-500);
  --border: var(--neutral-200);
  --ring: var(--primary-500);
}

.dark {
  --background: var(--neutral-950);
  --foreground: var(--neutral-50);
  --muted: var(--neutral-900);
  --muted-foreground: var(--neutral-400);
  --border: var(--neutral-800);
}
```

### Contrast Requirements

| Text Type | Minimum Contrast | Target |
|-----------|-----------------|--------|
| Body text | 4.5:1 | 7:1 |
| Large text (18px+) | 3:1 | 4.5:1 |
| UI elements | 3:1 | 4.5:1 |
| Decorative | None required | - |

**Always verify with a contrast checker!**

---

## 📐 TYPOGRAPHY SYSTEM

### Type Scale (1.25 ratio - Major Third)

```css
:root {
  /* Font Families */
  --font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --font-mono: 'JetBrains Mono', 'Fira Code', monospace;
  
  /* Font Sizes (using clamp for fluid typography) */
  --text-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.8rem);     /* 12-13px */
  --text-sm: clamp(0.875rem, 0.8rem + 0.35vw, 0.95rem);   /* 14-15px */
  --text-base: clamp(1rem, 0.9rem + 0.5vw, 1.125rem);     /* 16-18px */
  --text-lg: clamp(1.125rem, 1rem + 0.6vw, 1.25rem);      /* 18-20px */
  --text-xl: clamp(1.25rem, 1.1rem + 0.75vw, 1.5rem);     /* 20-24px */
  --text-2xl: clamp(1.5rem, 1.3rem + 1vw, 1.875rem);      /* 24-30px */
  --text-3xl: clamp(1.875rem, 1.5rem + 1.5vw, 2.5rem);    /* 30-40px */
  --text-4xl: clamp(2.25rem, 1.8rem + 2vw, 3rem);         /* 36-48px */
  --text-5xl: clamp(3rem, 2.2rem + 3vw, 4rem);            /* 48-64px */
  
  /* Font Weights */
  --font-normal: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;
  
  /* Line Heights */
  --leading-none: 1;
  --leading-tight: 1.25;
  --leading-snug: 1.375;
  --leading-normal: 1.5;
  --leading-relaxed: 1.625;
  --leading-loose: 2;
  
  /* Letter Spacing */
  --tracking-tight: -0.025em;
  --tracking-normal: 0;
  --tracking-wide: 0.025em;
}
```

### Typography Best Practices

```css
/* Headings */
h1, h2, h3, h4, h5, h6 {
  font-weight: var(--font-semibold);
  line-height: var(--leading-tight);
  letter-spacing: var(--tracking-tight);
}

h1 { font-size: var(--text-4xl); }
h2 { font-size: var(--text-3xl); }
h3 { font-size: var(--text-2xl); }
h4 { font-size: var(--text-xl); }
h5 { font-size: var(--text-lg); }
h6 { font-size: var(--text-base); }

/* Body text */
body {
  font-family: var(--font-sans);
  font-size: var(--text-base);
  font-weight: var(--font-normal);
  line-height: var(--leading-normal);
  color: var(--foreground);
}

/* Paragraph */
p {
  margin-bottom: 1em;
  max-width: 65ch; /* Optimal reading width */
}

/* Small text / captions */
.text-sm {
  font-size: var(--text-sm);
  line-height: var(--leading-normal);
}

.text-muted {
  color: var(--muted-foreground);
}
```

---

## 📏 SPACING SYSTEM

### 8-Point Grid

```css
:root {
  --space-0: 0;
  --space-0-5: 0.125rem;  /* 2px */
  --space-1: 0.25rem;     /* 4px */
  --space-1-5: 0.375rem;  /* 6px */
  --space-2: 0.5rem;      /* 8px */
  --space-2-5: 0.625rem;  /* 10px */
  --space-3: 0.75rem;     /* 12px */
  --space-3-5: 0.875rem;  /* 14px */
  --space-4: 1rem;        /* 16px */
  --space-5: 1.25rem;     /* 20px */
  --space-6: 1.5rem;      /* 24px */
  --space-7: 1.75rem;     /* 28px */
  --space-8: 2rem;        /* 32px */
  --space-9: 2.25rem;     /* 36px */
  --space-10: 2.5rem;     /* 40px */
  --space-11: 2.75rem;    /* 44px */
  --space-12: 3rem;       /* 48px */
  --space-14: 3.5rem;     /* 56px */
  --space-16: 4rem;       /* 64px */
  --space-20: 5rem;       /* 80px */
  --space-24: 6rem;       /* 96px */
  --space-32: 8rem;       /* 128px */
}
```

### Spacing Usage Guidelines

| Context | Spacing |
|---------|---------|
| Micro spacing (icon-text) | 4-8px |
| Related elements | 8-12px |
| Card padding | 16-24px |
| Section padding | 48-96px |
| Page margins | 16-64px (responsive) |

---

## 🔲 SHADOWS & ELEVATION

### Shadow Scale

```css
:root {
  --shadow-xs: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-sm: 0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
  --shadow-2xl: 0 25px 50px -12px rgb(0 0 0 / 0.25);
  --shadow-inner: inset 0 2px 4px 0 rgb(0 0 0 / 0.05);
}
```

### Elevation Levels

| Level | Shadow | Use Case |
|-------|--------|----------|
| 0 | None | Flat elements |
| 1 | shadow-xs | Subtle raised elements |
| 2 | shadow-sm | Cards, buttons |
| 3 | shadow-md | Dropdowns, popovers |
| 4 | shadow-lg | Modals, dialogs |
| 5 | shadow-xl | Floating elements |

---

## ✨ MICRO-INTERACTIONS

### Animation Timing

```css
:root {
  /* Duration */
  --duration-instant: 50ms;
  --duration-fast: 100ms;
  --duration-normal: 150ms;
  --duration-moderate: 200ms;
  --duration-slow: 300ms;
  --duration-slower: 500ms;
  
  /* Easing */
  --ease-linear: linear;
  --ease-in: cubic-bezier(0.4, 0, 1, 1);
  --ease-out: cubic-bezier(0, 0, 0.2, 1);
  --ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
  --ease-bounce: cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
```

### Standard Interactions

```css
/* Button hover */
.button {
  transition: 
    background-color var(--duration-fast) var(--ease-out),
    transform var(--duration-fast) var(--ease-out),
    box-shadow var(--duration-fast) var(--ease-out);
}

.button:hover {
  transform: translateY(-1px);
  box-shadow: var(--shadow-md);
}

.button:active {
  transform: translateY(0);
  box-shadow: var(--shadow-sm);
}

/* Card hover */
.card {
  transition: 
    transform var(--duration-moderate) var(--ease-out),
    box-shadow var(--duration-moderate) var(--ease-out);
}

.card:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-lg);
}

/* Link underline animation */
.link {
  position: relative;
}

.link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: currentColor;
  transform: scaleX(0);
  transform-origin: right;
  transition: transform var(--duration-normal) var(--ease-out);
}

.link:hover::after {
  transform: scaleX(1);
  transform-origin: left;
}

/* Focus ring */
.focusable:focus-visible {
  outline: 2px solid var(--ring);
  outline-offset: 2px;
}

/* Loading skeleton shimmer */
@keyframes shimmer {
  0% {
    background-position: -200% 0;
  }
  100% {
    background-position: 200% 0;
  }
}

.skeleton {
  background: linear-gradient(
    90deg,
    var(--muted) 0%,
    var(--neutral-200) 50%,
    var(--muted) 100%
  );
  background-size: 200% 100%;
  animation: shimmer 1.5s infinite;
}

/* Fade in */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in {
  animation: fadeIn var(--duration-moderate) var(--ease-out);
}

/* Success checkmark draw */
@keyframes checkmark {
  0% {
    stroke-dashoffset: 100;
  }
  100% {
    stroke-dashoffset: 0;
  }
}

.checkmark path {
  stroke-dasharray: 100;
  stroke-dashoffset: 100;
  animation: checkmark var(--duration-slow) var(--ease-out) forwards;
}

/* Error shake */
@keyframes shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-4px); }
  75% { transform: translateX(4px); }
}

.shake {
  animation: shake var(--duration-normal) var(--ease-out);
}
```

### Reduced Motion Support

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## 📱 RESPONSIVE DESIGN

### Breakpoints

```css
/* Mobile-first breakpoints */
:root {
  --breakpoint-sm: 640px;   /* Small tablets */
  --breakpoint-md: 768px;   /* Tablets */
  --breakpoint-lg: 1024px;  /* Small laptops */
  --breakpoint-xl: 1280px;  /* Desktops */
  --breakpoint-2xl: 1536px; /* Large screens */
}

/* Usage with Tailwind-style media queries */
@media (min-width: 640px) { /* sm */ }
@media (min-width: 768px) { /* md */ }
@media (min-width: 1024px) { /* lg */ }
@media (min-width: 1280px) { /* xl */ }
@media (min-width: 1536px) { /* 2xl */ }
```

### Responsive Patterns

```css
/* Container with responsive padding */
.container {
  width: 100%;
  margin-inline: auto;
  padding-inline: var(--space-4);
}

@media (min-width: 640px) {
  .container { padding-inline: var(--space-6); }
}

@media (min-width: 1024px) {
  .container { 
    padding-inline: var(--space-8);
    max-width: 1280px; 
  }
}

/* Responsive grid */
.grid {
  display: grid;
  gap: var(--space-4);
  grid-template-columns: repeat(1, 1fr);
}

@media (min-width: 640px) {
  .grid { grid-template-columns: repeat(2, 1fr); }
}

@media (min-width: 1024px) {
  .grid { grid-template-columns: repeat(3, 1fr); }
}

@media (min-width: 1280px) {
  .grid { grid-template-columns: repeat(4, 1fr); }
}

/* Responsive typography */
.hero-title {
  font-size: var(--text-2xl);
}

@media (min-width: 768px) {
  .hero-title { font-size: var(--text-4xl); }
}

@media (min-width: 1024px) {
  .hero-title { font-size: var(--text-5xl); }
}
```

### Touch-Friendly Design

```css
/* Minimum touch target size */
.touch-target {
  min-height: 44px;
  min-width: 44px;
  padding: var(--space-2);
}

/* Larger spacing on touch devices */
@media (pointer: coarse) {
  .button {
    min-height: 48px;
    padding: var(--space-3) var(--space-4);
  }
  
  .nav-link {
    padding: var(--space-3);
  }
}
```

---

## 🔲 COMPONENT STATES

### Every Interactive Component Needs:

| State | Description | Visual Treatment |
|-------|-------------|------------------|
| Default | Normal state | Base styling |
| Hover | Mouse over | Slight highlight/lift |
| Focus | Keyboard focus | Focus ring |
| Active | Being pressed | Slight depression |
| Disabled | Can't interact | Reduced opacity, no cursor |
| Loading | Processing | Spinner, skeleton |
| Error | Validation failed | Red border, error message |
| Success | Action completed | Green indicator |

### State Styling Example

```css
.input {
  border: 1px solid var(--border);
  background: var(--background);
  transition: border-color var(--duration-fast) var(--ease-out),
              box-shadow var(--duration-fast) var(--ease-out);
}

.input:hover {
  border-color: var(--neutral-400);
}

.input:focus {
  border-color: var(--primary-500);
  box-shadow: 0 0 0 3px rgb(var(--primary-500) / 0.2);
  outline: none;
}

.input:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  background: var(--muted);
}

.input[aria-invalid="true"] {
  border-color: var(--error-500);
}

.input[aria-invalid="true"]:focus {
  box-shadow: 0 0 0 3px rgb(var(--error-500) / 0.2);
}
```

---

## 🎯 EMPTY & LOADING STATES

### Empty State Design

```tsx
function EmptyState({ 
  icon: Icon, 
  title, 
  description, 
  action 
}: EmptyStateProps) {
  return (
    <div className="flex flex-col items-center justify-center py-16 text-center">
      <div className="rounded-full bg-muted p-4 mb-4">
        <Icon className="h-8 w-8 text-muted-foreground" />
      </div>
      <h3 className="text-lg font-semibold mb-2">{title}</h3>
      <p className="text-muted-foreground max-w-sm mb-6">{description}</p>
      {action && (
        <Button onClick={action.onClick}>
          {action.label}
        </Button>
      )}
    </div>
  );
}

// Usage
<EmptyState
  icon={InboxIcon}
  title="No messages yet"
  description="When you receive messages, they'll appear here."
  action={{ label: "Send a message", onClick: () => {} }}
/>
```

### Loading Skeleton

```tsx
function CardSkeleton() {
  return (
    <div className="rounded-lg border p-4 space-y-3">
      <Skeleton className="h-4 w-3/4" />
      <Skeleton className="h-4 w-1/2" />
      <div className="flex gap-2 pt-2">
        <Skeleton className="h-8 w-20" />
        <Skeleton className="h-8 w-20" />
      </div>
    </div>
  );
}

function Skeleton({ className }: { className?: string }) {
  return (
    <div 
      className={cn(
        "animate-pulse rounded-md bg-muted",
        className
      )} 
    />
  );
}
```

---

## ♿ ACCESSIBILITY ESSENTIALS

### Focus Management

```tsx
// Focus trap for modals
import { useEffect, useRef } from 'react';

function useFocusTrap(isActive: boolean) {
  const containerRef = useRef<HTMLDivElement>(null);
  
  useEffect(() => {
    if (!isActive) return;
    
    const container = containerRef.current;
    if (!container) return;
    
    const focusableElements = container.querySelectorAll(
      'button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])'
    );
    
    const firstElement = focusableElements[0] as HTMLElement;
    const lastElement = focusableElements[focusableElements.length - 1] as HTMLElement;
    
    firstElement?.focus();
    
    const handleKeyDown = (e: KeyboardEvent) => {
      if (e.key !== 'Tab') return;
      
      if (e.shiftKey && document.activeElement === firstElement) {
        e.preventDefault();
        lastElement?.focus();
      } else if (!e.shiftKey && document.activeElement === lastElement) {
        e.preventDefault();
        firstElement?.focus();
      }
    };
    
    container.addEventListener('keydown', handleKeyDown);
    return () => container.removeEventListener('keydown', handleKeyDown);
  }, [isActive]);
  
  return containerRef;
}
```

### Screen Reader Only Text

```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```

### Skip Link

```tsx
function SkipLink() {
  return (
    <a
      href="#main-content"
      className="sr-only focus:not-sr-only focus:fixed focus:top-4 focus:left-4 focus:z-50 focus:bg-background focus:px-4 focus:py-2 focus:rounded"
    >
      Skip to main content
    </a>
  );
}
```

---

## ✅ UI/UX QUALITY CHECKLIST

### Visual Design
- [ ] Colors follow established palette
- [ ] Typography hierarchy is clear
- [ ] Spacing is consistent (8pt grid)
- [ ] Shadows indicate correct elevation
- [ ] Dark mode works correctly
- [ ] Brand is consistently applied

### Component States
- [ ] All components have hover states
- [ ] Focus rings are visible
- [ ] Disabled states are clear
- [ ] Loading states use skeletons
- [ ] Error states show clear feedback
- [ ] Success states confirm actions

### Interactions
- [ ] Animations are smooth (60fps)
- [ ] Reduced motion respected
- [ ] Click/tap targets ≥ 44px
- [ ] Transitions feel natural
- [ ] No janky layout shifts

### Responsiveness
- [ ] Works at 320px width
- [ ] Works at 1920px width
- [ ] Touch-friendly on mobile
- [ ] Readable text at all sizes

### Accessibility
- [ ] Keyboard navigable
- [ ] Screen reader tested
- [ ] Contrast ratios pass
- [ ] Focus order is logical
- [ ] ARIA labels present
- [ ] Skip link works

---

**Reference this document when designing or implementing UI.**
