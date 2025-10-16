# CSS Roadmap

## Table of Contents

1. Fundamentals
2. Styling & Visuals
3. Layout Techniques
4. Responsive & Adaptive Design
5. Advanced Visual Effects & Animation
6. CSS Architecture & Tooling
7. Integration, Performance & Compatibility
8. Real-World Projects & Patterns

---

## 1. Fundamentals

### 1.1 What is CSS?

* The role of CSS in web development (separation of content and presentation)
* CSS syntax: selector + declaration block (property: value)
* The cascade, inheritance, and how CSS rules “win” (specificity, order, importance)

### 1.2 How to include CSS in HTML

* Inline styles
* Internal styles (in a `<style>` tag)
* External stylesheets (`<link rel="stylesheet" href="…">`)
* Media attributes in `<link>` (e.g. `media="print"`)

### 1.3 Selectors & Specificity

* Basic selectors: element, class, ID
* Combinators: descendant (` `), child (`>`), adjacent sibling (`+`), general sibling (`~`)
* Attribute selectors (e.g. `[attr=value]`, `[attr^=value]`)
* Pseudo-classes (e.g. `:hover`, `:focus`, `:nth-child`, `:not`)
* Pseudo-elements (e.g. `::before`, `::after`, `::first-line`)
* Specificity rules & tie-breakers
* `!important` (when to use, when to avoid)
* Inheritance: which properties inherit and which don’t

### 1.4 The Box Model & Sizing

* Content, padding, border, margin
* `width`, `height`, `min-width`, `max-width`, `min-height`, `max-height`
* `box-sizing` (content-box vs border-box)
* `overflow` and handling overflow (scroll, hidden, auto)
* Margin collapse rules

### 1.5 Units, Values & Colors

* Absolute units: `px`, `pt`, `cm`, etc.
* Relative units: `em`, `rem`, `%`, `vw`, `vh`, `vmin`, `vmax`
* `auto`, `inherit`, `initial`, `unset`
* `calc()` function
* Color formats: named colors, hex, `rgb()` / `rgba()`, `hsl()` / `hsla()`

---

## 2. Styling & Visuals

### 2.1 Typography & Text

* `font-family`, `font-size`, `font-weight`, `font-style`, `font-variant`
* Line height, letter spacing, word spacing
* `text-align`, `text-decoration`, `text-transform`
* `white-space`, `text-overflow`, wrapping / truncation
* Web fonts: `@font-face`, integrating Google Fonts / Adobe Fonts

### 2.2 Backgrounds, Borders & Shadows

* Background color, image, gradient, layering (multiple backgrounds)
* Background controlling: `background-repeat`, `background-position`, `background-size`, `background-attachment`
* Borders: `border-style`, `border-width`, `border-color`, `border-radius`, `border-image`
* Shadows: `box-shadow`, `text-shadow`

### 2.3 Spacing & Display

* Margin, padding, border (revisited)
* The different `display` types: `block`, `inline`, `inline-block`, `inline-flex`, `none`
* Visibility vs display
* CSS `position`: `static`, `relative`, `absolute`, `fixed`, `sticky`
* Offsets: `top`, `left`, `right`, `bottom`
* Stacking context & `z-index`

### 2.4 Styling Common Elements

* Lists (bullets, nested lists)
* Tables (`border-collapse`, `cellspacing` / `cellpadding`, captions)
* Form elements: input, select, textarea, button styling, placeholder styling
* Default browser styles & resetting / normalizing

---

## 3. Layout Techniques

### 3.1 Legacy Techniques & Why They Matter

* Floats & float clearing (e.g. clearfix)
* Inline-block layout quirks
* Positioning hacks for layout

### 3.2 Modern Layout — Flexbox

* Defining a flex container / flex items
* Main axis / cross axis
* `flex-direction`, `flex-wrap`
* `justify-content`, `align-items`, `align-content`
* Flex item settings: `flex-grow`, `flex-shrink`, `flex-basis`
* Ordering, alignment overrides, baseline alignment

### 3.3 Modern Layout — CSS Grid

* Grid container / grid item
* Defining grids: `grid-template-columns`, `grid-template-rows`, `grid-template-areas`
* Grid sizing: `auto`, `auto-fill` / `auto-fit`, `minmax()`
* Gaps: `row-gap`, `column-gap`
* Implicit vs explicit grid tracks
* Placement: `grid-column`, `grid-row`, named lines / span
* Alignment inside grid: `justify-items`, `align-items`, `justify-content`, `align-content`
* Nested grids & subgrid (browser support)

### 3.4 Combining Layouts

* Mixing Flexbox and Grid for complex UIs
* CSS logical properties (margin-block, padding-inline, etc.)
* CSS multi-column layout (less common, but useful)

---

## 4. Responsive & Adaptive Design

### 4.1 Responsive Design Principles

* Mobile-first vs desktop-first
* Fluid layouts vs fixed layouts
* Flexible images / media (`max-width: 100%`, `height: auto`)

### 4.2 Media Queries

* Syntax: `@media (min-width: …)`, `@media (max-width: …)`, combining conditions
* Breakpoints — common practices
* Responsive utilities (e.g. show/hide at breakpoints)

### 4.3 Responsive Units & Techniques

* Using `%`, `vw`, `vh`, `vmin`, `vmax`
* `clamp()`, `min()`, `max()` (modern CSS functions)
* Relative typography scaling (fluid type)
* Container queries (if browser support / polyfills)

### 4.4 Responsive Images & Media

* `srcset`, `sizes` for `<img>`
* `<picture>` element
* Responsive background images (via CSS)

---

## 5. Advanced Visual Effects & Animation

### 5.1 Transforms & Transitions

* 2D transforms: `translate()`, `rotate()`, `scale()`, `skew()`
* 3D transforms & perspective
* Transition properties: `transition-property`, `transition-duration`, `transition-timing-function`, `transition-delay`
* Easing functions (ease, linear, cubic-bezier)

### 5.2 Animations

* `@keyframes` definition
* Animation properties: `animation-name`, `animation-duration`, `animation-iteration-count`, `animation-direction`, `animation-timing-function`, `animation-delay`, `animation-fill-mode`
* Chaining / sequencing animations
* Performance considerations (transform / opacity vs layout)
* Using CSS for scroll or hover-triggered animations

### 5.3 Filters, Blend Modes & Effects

* CSS filters: `blur()`, `grayscale()`, `sepia()`, `drop-shadow()`, etc.
* `mix-blend-mode`, `background-blend-mode`
* Backdrop filters (glass / blur effects)
* Clip and mask: `clip-path`, `mask-image`
* Shapes & text wrapping (`shape-outside`, `shape-margin`)

### 5.4 Pseudo-Elements & Content Insertion

* Using `::before` and `::after` for decorative or semantic content
* `content` property (strings, counters, images)
* Styling generated content
* Advanced text-wrapping & flow around shapes

---

## 6. CSS Architecture & Tooling

### 6.1 Organization & Naming Conventions

* CSS methodologies: BEM (Block-Element-Modifier), SMACSS, OOCSS
* Modular CSS & component-based styling
* Scoped / namespaced styling

### 6.2 CSS Custom Properties (Variables)

* Defining and using `--custom-variable`
* Cascading of variables, fallback values (`var(--foo, fallback)`)
* Dynamic theming (light / dark mode)

### 6.3 Preprocessors & CSS Extensions

* Sass / SCSS (nesting, variables, mixins, functions, partials)
* Less, Stylus (comparative)
* PostCSS, Autoprefixer, CSS-in-JS

### 6.4 Build Tools & Pipelines

* Integrating CSS in bundlers (Webpack, Rollup, Vite)
* Minification, autoprefixing, tree-shaking
* Post-processing plugins (e.g. CSSNano)

### 6.5 CSS Modules & Scoped Styling (in frameworks)

* CSS Modules (in React, Vue, etc.)
* Shadow DOM / web components styling encapsulation

### 6.6 Testing & Debugging CSS

* Using browser devtools (inspection, layout tools, CSS rules panel)
* Visual regression testing
* Linting (stylelint, CSSLint)
* Design consistency tools & style guides

---

## 7. Integration, Performance & Compatibility

### 7.1 CSS & JavaScript Interaction

* Changing classes / properties via JS
* CSS-in-JS libraries & inline styling strategies
* Animation coordination (CSS vs JS)

### 7.2 Performance & Optimization

* Critical CSS / above-the-fold optimization
* Reducing CSS size (dead code elimination, modular CSS)
* Minimizing reflow and repaint (prefer transform & opacity)
* Lazy loading CSS

### 7.3 Browser Support & Feature Detection

* Vendor prefixes & when to use them
* Using `@supports` (feature queries)
* Graceful degradation vs progressive enhancement
* Polyfills & fallback strategies

### 7.4 Accessibility & CSS

* Ensuring readable contrast, font size, line spacing
* Avoiding CSS techniques that break accessibility (e.g. hidden text not accessible)
* Focus states, keyboard navigation, reduced motion preferences (`prefers-reduced-motion`)

---

## 8. Real-World Projects & Patterns

### 8.1 Build Mini Projects

* Landing page with hero, features section, footer
* Blog / magazine layout
* Dashboard / admin panel with sidebar + content area
* Photo gallery / masonry layout

### 8.2 Pattern Libraries & Design Systems

* Create a design tokens system (colors, spacing, fonts)
* Build reusable components (buttons, cards, forms, modals)
* Theming support (dark / light themes)

### 8.3 Advanced Patterns & Tricks

* CSS scroll snapping
* Parallax effects (pure CSS)
* Sticky elements & container sticky
* CSS for print styles (print media queries)
* Complex responsive layout patterns (e.g. magazine layouts, overlapping cards)

### 8.4 Continuous Learning & Resources

* Reading specs (W3C / CSS WG)
* Following CSS-oriented blogs, communities
* Experimenting with CSS challenges (e.g. CSSBattle)
* Contributing to open source CSS systems

---
