# Static Web Pages

Static web pages without external dependencies or build systems. Only W3C and WHATWG web standards allowed.

## Core Principles
- no external dependencies, frameworks, libraries, or build tools
- progressive enhancement: HTML first, CSS second, JavaScript last
- avoid JavaScript. It is optional enhancement, not required for core functionality. Ask before use.
- prefer native browser features over custom implementations

## HTML Standards (WHATWG)
- use semantic HTML elements over generic divs and spans
- prefer native elements: `<dialog>`, `<details>`, `<search>`, `<nav>`, `<main>`, `<article>`, `<aside>`, `<header>`, `<footer>`
- use `<dialog>` with `showModal()` for modals; use `popover` attribute for non-modal overlays
- use `<details>` and `<summary>` for accordions and disclosure widgets
- headings must follow logical hierarchy (h1 > h2 > h3)
- forms must use native validation attributes: `required`, `pattern`, `min`, `max`, `minlength`, `maxlength`, `type`
- use Constraint Validation API for custom validation messages
- do not use deprecated elements or attributes

## CSS Standards (W3C)
- no CSS frameworks, preprocessors, or build tools
- maintain styles in dedicated `.css` files; no inline styles

### Custom Properties & Cascade
- use CSS custom properties for theming, spacing, and reusable values
- use `@layer` to manage cascade priority: `@layer reset, base, components, utilities`
- use `@scope` for component-scoped styles without class naming conventions

### Layout
- prefer CSS Grid for two-dimensional layouts; use `subgrid` for nested grid alignment
- prefer Flexbox for one-dimensional layouts
- use `gap` instead of margin hacks for spacing

### Selectors
- use CSS nesting for related selectors
- use `:has()` for parent-based and previous-sibling styling
- use `:is()` to group selectors and reduce specificity
- use `:where()` for zero-specificity selector grouping

### Responsive Design
- prefer container queries (`@container`) over media queries for components
- use media queries for page-level layout only
- use `clamp()` for fluid typography and spacing: `font-size: clamp(1rem, 2vw + 0.5rem, 1.5rem)`

### Colors
- use `oklch()` or `oklab()` for perceptually uniform colors
- use `color-mix()` for color variations: `color-mix(in oklch, var(--primary) 80%, white)`
- use `light-dark()` with `color-scheme` for theme-aware colors

### Units & Sizing
- use logical properties (`inline-start`, `block-end`) over physical properties (`left`, `bottom`)
- prefer `rem` and `em` over `px` for accessibility
- use `dvh`, `svh`, `lvh` for viewport-relative heights on mobile

### User Preferences
- use `prefers-color-scheme` for light/dark themes
- use `prefers-reduced-motion` to disable animations
- use `prefers-contrast` for high-contrast adjustments

### Forms & Interactivity
- use `:valid`, `:invalid`, `:required`, `:optional`, `:user-valid`, `:user-invalid` for form styling
- use `accent-color` to theme native form controls
- use `scroll-snap-type` and `scroll-snap-align` for scroll snapping

## Accessibility (WCAG 2.2)
- the first rule of ARIA: do not use ARIA if a native HTML element provides the semantics
- use ARIA only when creating custom widgets without HTML equivalents
- all interactive elements must be keyboard accessible
- maintain visible focus indicators
- images must have meaningful `alt` text or `alt=""` for decorative images
- form inputs must have associated `<label>` elements
- use landmark elements: `<main>`, `<nav>`, `<header>`, `<footer>`, `<aside>`
- color must not be the only means of conveying information
- ensure sufficient color contrast (4.5:1 for normal text, 3:1 for large text)
- interactive targets should be at least 24x24 CSS pixels

## File Organization
- `index.html` as entry point
- styles in `styles/` directory
- scripts in `scripts/` directory
- images in `images/` directory
- prefer fewer, well-organized files over many small files

## Performance
- inline critical CSS in `<head>` only if measurably beneficial
- use `loading="lazy"` for below-the-fold images
- use `srcset` and `sizes` for responsive images
- use `<picture>` for art direction
- prefer SVG for icons and simple graphics
- minimize HTTP requests through reasonable file consolidation
- use `rel="preload"` sparingly for critical resources

## Forms
- always include `<label>` elements with `for` attribute
- group related inputs with `<fieldset>` and `<legend>`
- use appropriate input types: `email`, `tel`, `url`, `number`, `date`, `time`, `search`
- provide clear error messages using Constraint Validation API
- use `autocomplete` attribute for common fields
- submit buttons must use `<button type="submit">` or `<input type="submit">`

## Links and Navigation
- links must have descriptive text; avoid "click here"
- use `<nav>` for navigation regions
- skip links for keyboard users: link to `#main-content`
- external links should indicate they open in new context if using `target="_blank"`
- use `rel="noopener"` with `target="_blank"`

## Testing
- validate HTML with W3C Markup Validation Service
- validate CSS with W3C CSS Validation Service
- test keyboard navigation manually
- test with browser developer tools accessibility audits
- test without JavaScript enabled
- test across viewport sizes without device-specific breakpoints
