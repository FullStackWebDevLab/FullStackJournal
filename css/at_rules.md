# CSS At-Rules Reference

## Introduction

At-rules are CSS statements that instruct CSS how to behave. They begin with an at-sign (@) followed by an identifier and include everything from the at-keyword up to the next semicolon or the next CSS block.

At-rules are used to group and structure style rules, declare style information not directly associated with selected content, and manage syntactic constructs such as imports and namespaces.

---

## Types of At-Rules

CSS at-rules come in two main forms based on their syntax and purpose.

### Statement At-Rules

Statement at-rules end with a semicolon. They provide instructions or declarations that do not contain nested rules.

**General Syntax:**

```css
@identifier (RULE);
```

### Block At-Rules

Block at-rules end with a curly brace block that contains nested rules, other at-rules, or property declarations.

**General Syntax:**

```css
@identifier (RULE) {
  /* styles */
}
```

---

## Statement At-Rules

### @charset

Specifies the character encoding of the stylesheet. This at-rule must be the first element in the stylesheet and must not be preceded by any characters, not even comments.

**Syntax:**

```css
@charset "UTF-8";
```

**Example:**

```css
@charset "UTF-8";
body {
  background: yellow;
}
h1 {
  color: #ff0000;
}
```

**Important Rules:**

- Must be the first element in the stylesheet
- Cannot be preceded by any characters
- Only one @charset rule may appear per stylesheet
- Must use double quotes, not single quotes
- Should not be used in embedded stylesheets

---

### @import

Imports style rules from other stylesheets. The rule must be defined at the top of the stylesheet, after @charset but before other at-rules and style declarations.

**Syntax:**

```css
@import url;
@import url layer(layer-name);
@import url list-of-media-queries;
```

**Examples:**

```css
@import "navigation.css";
@import url("navigation.css");
@import "printstyle.css" print;
@import "mobile.css" screen and (max-width: 768px);
```

**Important Rules:**

- Must come after @charset and @layer but before other rules
- Creates a separate HTTP request for the imported file
- Can include media queries for conditional imports
- Cannot be used inside conditional group at-rules

---

### @namespace

Defines a default namespace or namespace prefix for a stylesheet. This is useful when working with documents containing multiple namespaces such as HTML with inline SVG or MathML.

**Syntax:**

```css
@namespace url("namespace-URL");
@namespace prefix url("namespace-URL");
```

**Examples:**

```css
@namespace url("http://www.w3.org/1999/xhtml");
@namespace svg url("http://www.w3.org/2000/svg");

/* Matches all XHTML <a> elements */
a {
  color: blue;
}

/* Matches all SVG <a> elements */
svg|a {
  fill: red;
}
```

**Important Rules:**

- Must follow @charset and @import rules
- Must precede all other at-rules and style declarations
- Default namespace only applies to type and universal selectors

---

### @layer (Statement Form)

Defines the order of precedence for cascade layers. This statement form declares layer order without defining styles.

**Syntax:**

```css
@layer layer-name;
@layer layer-name, layer-name, layer-name;
```

**Example:**

```css
@layer base, components, utilities;
```

---

## Block At-Rules

### @media

Applies styles conditionally based on media queries. This is one of the most commonly used at-rules for creating responsive designs.

**Syntax:**

```css
@media media-query {
  /* styles */
}
```

**Examples:**

```css
@media screen and (min-width: 768px) {
  .container {
    width: 750px;
  }
}

@media print {
  body {
    color: black;
  }
}

@media (prefers-color-scheme: dark) {
  body {
    background: black;
    color: white;
  }
}
```

**Common Media Features:**

- `width`, `min-width`, `max-width`
- `height`, `min-height`, `max-height`
- `orientation` (portrait or landscape)
- `prefers-color-scheme` (light or dark)
- `prefers-reduced-motion`
- `hover` (hover or none)
- `aspect-ratio`

---

### @supports

Tests whether the browser supports specific CSS features. Applies styles only if the condition is met.

**Syntax:**

```css
@supports (property: value) {
  /* styles */
}
```

**Examples:**

```css
@supports (display: grid) {
  .container {
    display: grid;
  }
}

@supports not (display: grid) {
  .container {
    display: flex;
  }
}

@supports (display: flex) and (gap: 1rem) {
  .container {
    display: flex;
    gap: 1rem;
  }
}
```

**Logical Operators:**

- `not` - Negates the condition
- `and` - Combines multiple conditions (all must be true)
- `or` - Checks if any condition is true

---

### @keyframes

Defines animations by specifying CSS styles for intermediate steps in an animation sequence.

**Syntax:**

```css
@keyframes animation-name {
  /* keyframes */
}
```

**Examples:**

```css
@keyframes slide-in {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0);
  }
}

@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-30px);
  }
  60% {
    transform: translateY(-15px);
  }
}

/* Using the animation */
.element {
  animation: slide-in 1s ease-in-out;
}
```

**Keyframe Selectors:**

- `from` or `0%` - Starting point
- `to` or `100%` - Ending point
- Any percentage value between 0% and 100%

---

### @font-face

Defines custom fonts by specifying font resource locations and style characteristics.

**Syntax:**

```css
@font-face {
  font-family: name;
  src: url(path);
  font-weight: value;
  font-style: value;
}
```

**Example:**

```css
@font-face {
  font-family: "CustomFont";
  src: url("font.woff2") format("woff2"),
       url("font.woff") format("woff");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "CustomFont";
  src: url("font-bold.woff2") format("woff2");
  font-weight: bold;
}

/* Using the custom font */
body {
  font-family: "CustomFont", Arial, sans-serif;
}
```

**Common Descriptors:**

- `font-family` - Name of the font (required)
- `src` - Font file location (required)
- `font-weight` - Font weight (normal, bold, 100-900)
- `font-style` - Font style (normal, italic, oblique)
- `font-display` - How the font is displayed while loading (auto, swap, block, fallback, optional)
- `unicode-range` - Range of characters the font supports

---

### @page

Specifies aspects of printed pages such as dimensions, orientation, and margins.

**Syntax:**

```css
@page {
  /* page properties */
}
```

**Examples:**

```css
@page {
  size: A4;
  margin: 2cm;
}

@page :first {
  margin-top: 5cm;
}

@page :left {
  margin-left: 3cm;
  margin-right: 2cm;
}

@page :right {
  margin-left: 2cm;
  margin-right: 3cm;
}
```

**Common Properties:**

- `size` - Page dimensions (A4, letter, landscape, etc.)
- `margin` - Page margins
- `marks` - Crop and registration marks
- `bleed` - Bleed area for printing

---

### @container

Applies styles based on the size of a container element rather than the viewport. This enables component-based responsive design.

**Syntax:**

```css
@container container-name (query) {
  /* styles */
}
```

**Examples:**

```css
.container {
  container-type: inline-size;
  container-name: card;
}

@container card (min-width: 400px) {
  .card-content {
    display: grid;
    grid-template-columns: 1fr 2fr;
  }
}

@container (min-width: 600px) {
  .element {
    font-size: 1.5rem;
  }
}
```

**Container Types:**

- `size` - Query both width and height
- `inline-size` - Query inline dimension (width in horizontal writing mode)
- `normal` - Element is not a query container

---

### @layer (Block Form)

Creates a named cascade layer and defines styles within that layer. Layers provide control over specificity and cascade order.

**Syntax:**

```css
@layer layer-name {
  /* styles */
}
```

**Examples:**

```css
@layer base {
  h1 {
    color: black;
  }
}

@layer components {
  .button {
    background: blue;
    color: white;
  }
}

@layer utilities {
  .text-center {
    text-align: center;
  }
}

/* Nested layers */
@layer framework {
  @layer base {
    /* base styles */
  }
  
  @layer components {
    /* component styles */
  }
}
```

**Layer Order:**

Styles in later-defined layers override styles in earlier-defined layers, regardless of specificity.

```css
@layer base, components, utilities;

@layer base {
  button {
    background: gray;
  }
}

@layer components {
  button {
    background: blue; /* This wins even with lower specificity */
  }
}
```

---

### @property

Defines CSS custom properties with type checking, default values, and inheritance behavior.

**Syntax:**

```css
@property --property-name {
  syntax: "<type>";
  inherits: true | false;
  initial-value: value;
}
```

**Examples:**

```css
@property --theme-color {
  syntax: "<color>";
  inherits: true;
  initial-value: blue;
}

@property --spacing {
  syntax: "<length>";
  inherits: false;
  initial-value: 1rem;
}

@property --rotation {
  syntax: "<angle>";
  inherits: false;
  initial-value: 0deg;
}

/* Using the custom property */
.element {
  color: var(--theme-color);
  padding: var(--spacing);
  transform: rotate(var(--rotation));
}
```

**Syntax Types:**

- `<length>` - Length values (px, em, rem, etc.)
- `<number>` - Numeric values
- `<percentage>` - Percentage values
- `<color>` - Color values
- `<angle>` - Angle values (deg, rad, turn)
- `<time>` - Time values (s, ms)
- `*` - Any value

---

### @counter-style

Defines custom counter styles for list numbering and extends predefined list styles.

**Syntax:**

```css
@counter-style counter-name {
  system: type;
  symbols: values;
  /* other descriptors */
}
```

**Examples:**

```css
@counter-style custom-numbers {
  system: cyclic;
  symbols: "①" "②" "③" "④" "⑤";
}

@counter-style thumbs {
  system: cyclic;
  symbols: "👍" "👎";
  suffix: " ";
}

@counter-style roman-upper {
  system: additive;
  additive-symbols: 1000 M, 900 CM, 500 D, 400 CD, 100 C, 90 XC, 50 L, 40 XL, 10 X, 9 IX, 5 V, 4 IV, 1 I;
}

/* Using the custom counter style */
ol {
  list-style-type: custom-numbers;
}
```

**System Types:**

- `cyclic` - Cycles through symbols
- `numeric` - Interprets symbols as digits
- `alphabetic` - Interprets symbols as letters
- `symbolic` - Cycles and repeats symbols
- `additive` - Uses additive tuple system (like Roman numerals)
- `fixed` - Finite set of symbols

---

### @scope

Defines a scope for applying styles to selected elements within specific boundaries.

**Syntax:**

```css
@scope (scope-root) to (scope-limit) {
  /* styles */
}
```

**Examples:**

```css
@scope (.component) {
  h2 {
    color: blue;
  }
  
  p {
    font-size: 1rem;
  }
}

@scope (.card) to (.card-footer) {
  /* Styles apply to elements within .card but not within .card-footer */
  a {
    color: red;
  }
}
```

**Use Cases:**

- Component isolation
- Preventing style leakage
- Creating style boundaries in design systems

---

### @starting-style

Defines starting property values for elements to transition from when receiving their first style update.

**Syntax:**

```css
@starting-style {
  /* initial styles */
}
```

**Example:**

```css
@starting-style {
  .dialog {
    opacity: 0;
    transform: scale(0.9);
  }
}

.dialog {
  opacity: 1;
  transform: scale(1);
  transition: opacity 0.3s, transform 0.3s;
}
```

**Use Cases:**

- Animating elements when they first appear
- Transitioning from `display: none` to visible
- Entry animations for dynamic content

---

### @font-feature-values

Controls font display per font family by defining font-specific alternates for OpenType features.

**Syntax:**

```css
@font-feature-values font-family {
  @stylistic {
    name: index;
  }
}
```

**Example:**

```css
@font-feature-values "Custom Font" {
  @stylistic {
    fancy: 1;
    elegant: 2;
  }
  
  @swash {
    decorative: 1;
  }
}

.text {
  font-family: "Custom Font";
  font-variant-alternates: stylistic(fancy);
}
```

---

### @position-try

Defines custom position options for anchor-positioned elements with fallback positioning and alignment.

**Syntax:**

```css
@position-try --try-name {
  /* position properties */
}
```

**Example:**

```css
@position-try --fallback-position {
  top: anchor(bottom);
  left: anchor(left);
}

.tooltip {
  position: absolute;
  position-try-fallbacks: --fallback-position;
}
```

---

### @view-transition

Opts the current document into a view transition for smooth transitions between page states.

**Syntax:**

```css
@view-transition {
  navigation: auto;
}
```

**Example:**

```css
@view-transition {
  navigation: auto;
}

::view-transition-old(root) {
  animation: fade-out 0.3s;
}

::view-transition-new(root) {
  animation: fade-in 0.3s;
}
```

---

## Best Practices

Following these best practices will help you use at-rules effectively and avoid common errors.

### Order of At-Rules

At-rules must appear in a specific order in your stylesheet. The correct order is:

1. `@charset` (if present, must be first)
2. `@import` statements
3. `@namespace` declarations
4. All other at-rules and style declarations

**Example:**

```css
@charset "UTF-8";
@import "base.css";
@namespace svg url("http://www.w3.org/2000/svg");
@layer base, components;

/* Other styles follow */
```

### Performance Considerations

- Minimize use of `@import` as it creates additional HTTP requests
- Use `@supports` to provide fallbacks for unsupported features
- Combine media queries when possible to reduce code duplication
- Use `@layer` to manage specificity and reduce the need for `!important`
- Consider using CSS bundlers to inline imported files

### Browser Support

Always check browser support for newer at-rules before using them in production. Some at-rules like `@container`, `@scope`, and `@starting-style` are relatively new and may not be supported in older browsers.

**Checking Support:**

```css
@supports (container-type: inline-size) {
  /* Use container queries */
  @container (min-width: 400px) {
    /* styles */
  }
}
```

### Maintainability

- Use meaningful names for `@layer` and `@keyframes`
- Document custom `@property` definitions
- Keep `@media` queries organized by breakpoint
- Group related `@font-face` declarations together
- Use comments to explain complex `@counter-style` systems

---

## Quick Reference Table

The following table summarizes the most commonly used at-rules and their primary purposes.

| At-Rule | Type | Purpose |
|---------|------|---------|
| `@charset` | Statement | Specifies character encoding |
| `@import` | Statement | Imports external stylesheets |
| `@namespace` | Statement | Defines namespaces for XML elements |
| `@layer` | Both | Manages cascade layer precedence |
| `@media` | Block | Applies styles based on media queries |
| `@supports` | Block | Tests browser feature support |
| `@keyframes` | Block | Defines animation sequences |
| `@font-face` | Block | Defines custom fonts |
| `@page` | Block | Specifies print page properties |
| `@container` | Block | Applies styles based on container size |
| `@property` | Block | Defines custom CSS properties |
| `@counter-style` | Block | Defines custom list styles |
| `@scope` | Block | Creates scoped style boundaries |
| `@starting-style` | Block | Defines transition starting values |
| `@font-feature-values` | Block | Controls OpenType font features |
| `@position-try` | Block | Defines position fallback options |
| `@view-transition` | Block | Enables view transitions |

---
