# CSS Custom Properties: Complete Reference Guide

## Introduction

CSS Custom Properties, commonly called CSS variables, are entities that store values for reuse throughout a document. They enable dynamic styling, reduce code repetition, and improve maintainability. Unlike preprocessor variables (such as those in Sass or Less), custom properties are native to CSS and participate in the cascade and inheritance.

## Basic Syntax and Declaration

### Declaring Custom Properties

Custom properties are declared using two dashes (`--`) followed by a property name. They must be declared within a selector.

```css
:root {
  --primary-color: #3498db;
  --spacing-unit: 16px;
  --font-main: 'Helvetica', sans-serif;
}
```

**Naming Rules:**
- Must begin with `--`
- Can contain letters, numbers, hyphens, and underscores
- Case-sensitive (e.g., `--myColor` and `--mycolor` are different properties)
- Cannot contain whitespace, path separators (`/` or `\`), or quotes

### Using Custom Properties

Custom properties are accessed using the `var()` function:

```css
.button {
  background-color: var(--primary-color);
  padding: var(--spacing-unit);
  font-family: var(--font-main);
}
```

### Fallback Values

The `var()` function accepts a second parameter as a fallback value, used when the custom property is undefined or invalid:

```css
color: var(--text-color, black);
background: var(--bg-color, var(--default-bg, white));
```

**Important:** Fallback values do not address browser compatibility issues. They only handle cases where a custom property is undefined or has an invalid value in browsers that support custom properties.

## Scope and Inheritance

### Global Scope

Properties declared on `:root` are globally accessible throughout the document:

```css
:root {
  --global-color: blue;
}
```

### Local Scope

Properties can be scoped to specific selectors, making them available only to that element and its descendants:

```css
.card {
  --card-padding: 20px;
  padding: var(--card-padding);
}

.card-content {
  padding: var(--card-padding); /* Inherits from parent .card */
}
```

### Inheritance Behavior

By default, custom properties defined with the `--` syntax inherit values from their parent elements. This means child elements can access custom properties set on ancestors. Properties follow standard CSS cascade and specificity rules.

## The @property At-Rule

The `@property` at-rule provides enhanced control over custom properties by allowing type specification, default values, and inheritance control.

### Syntax

```css
@property --property-name {
  syntax: '<type>';
  inherits: true | false;
  initial-value: value;
}
```

### Required Descriptors

**1. syntax**: Defines the type of value the property accepts

Available types include:
- `<color>`: Color values
- `<length>`: Length values (px, em, rem, etc.)
- `<number>`: Numeric values
- `<percentage>`: Percentage values
- `<integer>`: Integer values
- `<angle>`: Angle values
- `<time>`: Time values
- `<image>`: Image values
- `<custom-ident>`: Custom identifier
- `*`: Universal syntax (any valid CSS value)

**2. inherits**: Controls inheritance behavior
- `true`: Property inherits from parent
- `false`: Property does not inherit (uses initial value)

**3. initial-value**: Default value when property is not set
- Required unless `syntax` is `*`
- Must be computationally independent (cannot depend on other values like `em` which depends on font-size)

### Example

```css
@property --box-color {
  syntax: '<color>';
  inherits: false;
  initial-value: teal;
}

.box {
  background-color: var(--box-color);
}
```

### Multiple Types

You can combine types using operators:
- `|`: OR operator (e.g., `<length> | <percentage>`)
- `+`: Space-separated list (e.g., `<color>+`)
- `#`: Comma-separated list (e.g., `<color>#`)

```css
@property --spacing {
  syntax: '<length> | <percentage>';
  inherits: true;
  initial-value: 16px;
}
```

## JavaScript Integration

### Reading Custom Properties

```javascript
const element = document.querySelector('.button');
const value = getComputedStyle(element).getPropertyValue('--primary-color');
```

### Setting Custom Properties

```javascript
// Set on specific element
element.style.setProperty('--primary-color', '#e74c3c');

// Set on document root
document.documentElement.style.setProperty('--primary-color', '#e74c3c');
```

### Registering Properties via JavaScript

Custom properties can also be registered using the JavaScript API:

```javascript
CSS.registerProperty({
  name: '--my-color',
  syntax: '<color>',
  inherits: false,
  initialValue: '#c0ffee'
});
```

## Using Custom Properties with calc()

Custom properties work seamlessly with the `calc()` function for mathematical operations:

```css
:root {
  --base-spacing: 8px;
}

.container {
  padding: calc(var(--base-spacing) * 2);  /* 16px */
  margin: calc(var(--base-spacing) * 3);   /* 24px */
}
```

### Combining Multiple Properties

```css
:root {
  --width-base: 100%;
  --sidebar-width: 250px;
  --gap: 20px;
}

.content {
  width: calc(var(--width-base) - var(--sidebar-width) - var(--gap));
}
```

### Deferred Calculation

You can store mathematical expressions in custom properties and defer the `calc()` evaluation:

```css
body {
  --base-font-size: 16px;
  --modifier: 2;
  --font-size: var(--base-font-size) * var(--modifier);
  
  /* The calc() is evaluated here */
  font-size: calc(var(--font-size));
}
```

### Operator Rules

- **Addition and Subtraction** (`+`, `-`): Must be surrounded by whitespace
- **Multiplication and Division** (`*`, `/`): Whitespace not required but recommended
- Only one operand can have units in multiplication
- Both operands can have units in division (results in unitless number)

```css
/* Correct */
width: calc(100% - 20px);
height: calc(2em * 3);

/* Incorrect - missing whitespace */
width: calc(100%-20px);
```

## Advanced Techniques

### Partial Values

Custom properties can hold parts of values, useful for color manipulation:

```css
:root {
  --h: 200;
  --s: 50%;
  --l: 50%;
}

.element {
  background: hsl(var(--h) var(--s) var(--l));
}

.element:hover {
  --l: 70%; /* Lighten on hover */
}
```

### Dynamic Theming

```css
:root {
  --theme-bg: white;
  --theme-text: black;
}

[data-theme="dark"] {
  --theme-bg: black;
  --theme-text: white;
}

body {
  background-color: var(--theme-bg);
  color: var(--theme-text);
}
```

### Responsive Design

Custom properties can be updated in media queries:

```css
:root {
  --container-width: 1200px;
}

@media (max-width: 768px) {
  :root {
    --container-width: 100%;
  }
}

.container {
  max-width: var(--container-width);
}
```

### Animation and Transitions

Properties registered with `@property` can be animated:

```css
@property --gradient-angle {
  syntax: '<angle>';
  inherits: false;
  initial-value: 0deg;
}

.box {
  background: linear-gradient(var(--gradient-angle), blue, red);
  transition: --gradient-angle 1s;
}

.box:hover {
  --gradient-angle: 180deg;
}
```

## Valid at Computed Time

When a custom property contains an invalid value for its usage context, the browser cannot detect this until computation time. This leads to the concept of "valid at computed time."

### Invalid Substitution Behavior

When an invalid `var()` substitution occurs:
1. The browser checks if the property inherits
2. If yes and a parent has a valid value, use the inherited value
3. Otherwise, use the initial value

```css
:root {
  --text-color: 16px; /* Invalid for color property */
}

p {
  color: var(--text-color); /* Results in initial value: black */
}
```

### Prevention with @property

The `@property` rule prevents invalid values by enforcing type constraints:

```css
@property --text-color {
  syntax: '<color>';
  inherits: false;
  initial-value: teal;
}

:root {
  --text-color: 16px; /* Invalid, will use initial-value: teal */
}
```

## Limitations and Restrictions

### Cannot Be Used In

1. **Media Queries**: Custom properties cannot be used inside `@media` or `@container` queries
```css
/* This does NOT work */
@media (min-width: var(--breakpoint)) { }
```

2. **Property Names**: Cannot be used as property names or selectors
```css
/* This does NOT work */
var(--property-name): value;
```

3. **Selector Names**: Cannot construct selectors
```css
/* This does NOT work */
var(--selector) { }
```

### Dependency Cycles

Custom properties cannot reference themselves in their own definition:

```css
/* This creates a dependency cycle and fails */
.container {
  --radius: calc(var(--radius) - 10px);
}
```

### No Direct Animation

Standard custom properties (without `@property`) cannot be animated or transitioned because the browser has no type information.

## Browser Support

### Custom Properties (-- syntax)
- **Support Level**: Widely available
- **Available Since**: April 2017
- **Compatibility Score**: ~92%
- **Supported In**: All modern browsers (Chrome, Firefox, Safari, Edge)
- **Not Supported**: Internet Explorer 11 and earlier

### @property At-Rule
- **Support Level**: Baseline (Newly available as of July 2024)
- **Supported In**: All modern browsers
- **Compatibility Score**: ~93%

### Feature Detection

CSS:
```css
@supports (--custom: property) {
  /* Code for browsers that support custom properties */
}

@supports not (--custom: property) {
  /* Fallback for browsers without support */
}
```

JavaScript:
```javascript
if (CSS.supports('--custom', 'property')) {
  // Custom properties supported
}
```

## Best Practices

### 1. Use Semantic Names

```css
/* Good */
--primary-color: blue;
--spacing-large: 32px;

/* Avoid */
--blue: blue;
--s-l: 32px;
```

### 2. Organize with Prefixes

```css
:root {
  /* Colors */
  --color-primary: #3498db;
  --color-secondary: #2ecc71;
  
  /* Spacing */
  --space-sm: 8px;
  --space-md: 16px;
  --space-lg: 32px;
  
  /* Typography */
  --font-size-base: 16px;
  --font-weight-bold: 700;
}
```

### 3. Define Global Defaults on :root

```css
:root {
  --default-padding: 20px;
  --default-margin: 10px;
}
```

### 4. Use Fallback Values for Safety

```css
.element {
  color: var(--user-color, var(--default-color, black));
}
```

### 5. Leverage @property for Type Safety

```css
@property --critical-size {
  syntax: '<length>';
  inherits: true;
  initial-value: 16px;
}
```

### 6. Combine with Preprocessors

You can use preprocessor variables to set custom properties:

```scss
// Sass
$brand-color: red;

:root {
  --brand-color: #{$brand-color};
}
```

### 7. Document Your Custom Properties

```css
/**
 * Design System Variables
 * 
 * --color-primary: Main brand color
 * --color-secondary: Accent color
 * --spacing-unit: Base spacing value (all spacing is multiples of this)
 */
:root {
  --color-primary: #0066cc;
  --color-secondary: #ff6600;
  --spacing-unit: 8px;
}
```

## Common Use Cases

### Design Systems and Tokens

```css
:root {
  /* Base tokens */
  --token-color-brand: #0066cc;
  --token-space-base: 8px;
  --token-font-size-base: 16px;
  
  /* Semantic tokens */
  --button-bg: var(--token-color-brand);
  --button-padding: calc(var(--token-space-base) * 2);
}
```

### Component-Level Customization

```css
.button {
  --button-color: blue;
  --button-padding: 10px;
  
  background-color: var(--button-color);
  padding: var(--button-padding);
}

.button--large {
  --button-padding: 20px;
}
```

### Web Components (Shadow DOM)

Custom properties penetrate Shadow DOM boundaries, making them ideal for styling Web Components:

```css
/* Outside component */
custom-element {
  --component-color: red;
}

/* Inside Shadow DOM */
.internal-element {
  color: var(--component-color);
}
```

### Dark Mode Implementation

```css
:root {
  --bg-color: white;
  --text-color: black;
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg-color: black;
    --text-color: white;
  }
}

body {
  background-color: var(--bg-color);
  color: var(--text-color);
}
```

## Differences from Preprocessor Variables

| Feature | Custom Properties | Preprocessor Variables |
|---------|------------------|----------------------|
| Evaluation | Runtime (dynamic) | Compile-time (static) |
| Scope | Follows cascade/inheritance | File/block scope |
| JavaScript Access | Yes | No |
| Modifiable at Runtime | Yes | No |
| Browser Support Required | Yes | No (compiled away) |
| Can Use in Media Queries | No | Yes |
| Type System | With @property | Limited |
| Cascade Participation | Yes | No |

---
