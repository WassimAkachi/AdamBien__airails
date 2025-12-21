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
- use CSS custom properties (variables) for theming and reusable values
- prefer CSS Grid for two-dimensional layouts
- prefer Flexbox for one-dimensional layouts
- use container queries (`@container`) for component-responsive design
- use `:has()` selector for parent-based styling
- use CSS nesting for related selectors
- responsive design: prefer container queries over media queries for components; use media queries for page-level layout
- use logical properties (`inline-start`, `block-end`) over physical properties (`left`, `bottom`)
- prefer `rem` and `em` over `px` for accessibility
- use `prefers-color-scheme` and `prefers-reduced-motion` for user preferences
- maintain styles in dedicated `.css` files; no inline styles
- use `:valid`, `:invalid`, `:required`, `:optional` for form styling

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
