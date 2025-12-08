# `<ol>`

## Key Topics

+ [Definition and Purpose](#definition-and-purpose)
+ [Syntax and Variants](#syntax-and-variants)
+ [Attributes](#attributes)
+ [Content Model](#content-model)
+ [Context](#context)
+ [Behavior and Semantics](#behavior-and-semantics)
+ [Examples](#examples)
+ [Notes](#notes)

---

## Definition and Purpose

The `<ol>` (ordered list) element represents a collection of items where the sequence or order of items is meaningful. It groups items that follow a specific order, progression, or hierarchy, typically displayed with sequential numbering, making it ideal for step-by-step instructions, rankings, prioritized items, or any content where the position conveys importance or sequence.

---

## Syntax and Variants

+ **Standard syntax**: `<ol>...</ol>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps one or more `<li>` (list item) elements
+ **No self-closing variant**: Must contain list items
+ **List family**: Part of HTML list elements with `<ul>` and `<dl>`

---

## Attributes

+ **Core attributes**:
  - `reversed` (optional): Indicates list order is reversed (boolean)
  - `start` (optional): Starting value for list numbering (integer)
  - `type` (optional): Numbering type (`1`, `a`, `A`, `i`, `I`)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Deprecated attributes**:
  - `compact` (use CSS instead)

---

## Content Model

+ **Permitted content**: Zero or more `<li>` elements
+ **Required children**: At least one `<li>` for meaningful lists
+ **List item restriction**: Only `<li>` elements are valid direct children
+ **Nesting capability**: `<li>` elements can contain other lists for nested structures

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<article>`, `<section>` for procedural content
  - In tutorials, recipes, and instructional content
  - For rankings, priorities, and sequential processes
  - Within `<div>` containers for structured content
+ **Flow content**: Treated as block-level element in document flow

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - `margin-top: 1em`
  - `margin-bottom: 1em`
  - `margin-left: 0`
  - `margin-right: 0`
  - `padding-left: 40px`
  - `list-style-type: decimal`
+ **Numbering behavior**:
  - Automatically numbers items sequentially
  - Respects `start`, `reversed`, and `type` attributes
  - Handles nested numbering for hierarchical content
+ **Semantic meaning**:
  - Represents an ordered list of items
  - Screen readers announce as "list" with item count and order significance
  - Conveys that item sequence is meaningful
+ **Accessibility**: Proper ordered list structure helps screen reader users understand sequence-dependent content

---

## Examples

**Basic ordered list:**
```html
<ol>
  <li>Preheat oven to 350°F (175°C)</li>
  <li>Mix dry ingredients in a large bowl</li>
  <li>Add wet ingredients and stir until combined</li>
  <li>Pour batter into greased pan</li>
  <li>Bake for 30-35 minutes</li>
</ol>
```

**Ordered list with custom start value:**
```html
<ol start="10">
  <li>Tenth item</li>
  <li>Eleventh item</li>
  <li>Twelfth item</li>
</ol>
```

**Reversed ordered list:**
```html
<ol reversed>
  <li>Fourth item (displays as 4)</li>
  <li>Third item (displays as 3)</li>
  <li>Second item (displays as 2)</li>
  <li>First item (displays as 1)</li>
</ol>
```

**Different numbering types:**
```html
<!-- Decimal numbers (default) -->
<ol type="1">
  <li>First item</li>
  <li>Second item</li>
</ol>

<!-- Lowercase letters -->
<ol type="a">
  <li>First item</li>
  <li>Second item</li>
</ol>

<!-- Uppercase letters -->
<ol type="A">
  <li>First item</li>
  <li>Second item</li>
</ol>

<!-- Lowercase Roman numerals -->
<ol type="i">
  <li>First item</li>
  <li>Second item</li>
</ol>

<!-- Uppercase Roman numerals -->
<ol type="I">
  <li>First item</li>
  <li>Second item</li>
</ol>
```

**Nested ordered lists with different types:**
```html
<ol>
  <li>
    Preparation
    <ol type="a">
      <li>Gather ingredients</li>
      <li>Prepare equipment</li>
      <li>Set up workspace</li>
    </ol>
  </li>
  <li>
    Execution
    <ol type="a">
      <li>Follow step-by-step process</li>
      <li>Monitor progress</li>
      <li>Make adjustments as needed</li>
    </ol>
  </li>
  <li>
    Completion
    <ol type="a">
      <li>Verify results</li>
      <li>Clean up</li>
      <li>Document outcomes</li>
    </ol>
  </li>
</ol>
```

**Complex ordered list with rich content:**
```html
<ol class="tutorial-steps">
  <li>
    <h3>Set Up Development Environment</h3>
    <p>Install the necessary tools and configure your workspace.</p>
    <pre><code>npm install -g create-react-app</code></pre>
    <div class="note">Note: Ensure you have Node.js version 14 or higher.</div>
  </li>
  <li>
    <h3>Create New Project</h3>
    <p>Initialize a new React application using the CLI tool.</p>
    <pre><code>create-react-app my-project
cd my-project</code></pre>
  </li>
  <li>
    <h3>Start Development Server</h3>
    <p>Launch the application in development mode.</p>
    <pre><code>npm start</code></pre>
    <p>The application will open in your browser at <code>http://localhost:3000</code></p>
  </li>
</ol>
```

**Ordered list with value attributes on items:**
```html
<ol>
  <li value="5">Fifth item (starts numbering from 5)</li>
  <li>Sixth item (continues automatically)</li>
  <li value="10">Tenth item (jumps to 10)</li>
  <li>Eleventh item (continues from 10)</li>
  <li value="1">First item (restarts at 1)</li>
  <li>Second item (continues from 1)</li>
</ol>
```

**Accessible ordered list with ARIA attributes:**
```html
<ol aria-labelledby="instructions-heading" role="list">
  <li role="listitem">
    <span class="step-number" aria-hidden="true">1.</span>
    <span class="step-text">Connect the device to power source</span>
  </li>
  <li role="listitem">
    <span class="step-number" aria-hidden="true">2.</span>
    <span class="step-text">Press and hold the power button for 3 seconds</span>
  </li>
  <li role="listitem">
    <span class="step-number" aria-hidden="true">3.</span>
    <span class="step-text">Wait for the status light to turn green</span>
  </li>
</ol>
```

**Mixed nested lists:**
```html
<ol>
  <li>
    Planning Phase
    <ul>
      <li>Define project scope</li>
      <li>Identify stakeholders</li>
      <li>Set timeline and milestones</li>
    </ul>
  </li>
  <li>
    Execution Phase
    <ol type="a">
      <li>
        Development
        <ul>
          <li>Frontend implementation</li>
          <li>Backend development</li>
          <li>Database design</li>
        </ul>
      </li>
      <li>
        Testing
        <ul>
          <li>Unit testing</li>
          <li>Integration testing</li>
          <li>User acceptance testing</li>
        </ul>
      </li>
    </ol>
  </li>
  <li>
    Deployment Phase
    <ul>
      <li>Production deployment</li>
      <li>Monitoring setup</li>
      <li>Documentation completion</li>
    </ul>
  </li>
</ol>
```

**Responsive ordered list with custom counters:**
```html
<ol class="responsive-steps">
  <li class="step">
    <div class="step-content">
      <h4>Requirements Gathering</h4>
      <p>Collect and analyze business requirements from stakeholders.</p>
    </div>
  </li>
  <li class="step">
    <div class="step-content">
      <h4>System Design</h4>
      <p>Create architectural diagrams and system specifications.</p>
    </div>
  </li>
  <li class="step">
    <div class="step-content">
      <h4>Implementation</h4>
      <p>Develop the system according to design specifications.</p>
    </div>
  </li>
</ol>

<style>
.responsive-steps {
  list-style: none;
  counter-reset: step-counter;
  padding-left: 0;
}

.step {
  counter-increment: step-counter;
  margin-bottom: 2rem;
  position: relative;
  padding-left: 4rem;
}

.step::before {
  content: counter(step-counter);
  position: absolute;
  left: 0;
  top: 0;
  width: 3rem;
  height: 3rem;
  background: #007acc;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}
</style>
```

---

## Notes

* **Semantic importance**: Use `<ol>` when item order matters; use `<ul>` when sequence is not meaningful
* **Numbering systems**: Support for decimal, alphabetic, and Roman numeral systems
* **Accessibility benefits**: Screen readers announce list structure, item count, and current position
* **CSS customization**:
  - `list-style-type`: decimal, decimal-leading-zero, lower-alpha, upper-alpha, lower-roman, upper-roman
  - Custom counters with `counter-reset` and `counter-increment`
  - Full control over numbering appearance
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using `<ol>` for non-sequential content
  - Overusing complex numbering when simple lists would suffice
  - Not maintaining proper nesting hierarchy
  - Confusing `start` attribute with `value` on `<li>` elements
* **Value attribute on `<li>`**: Overrides automatic numbering for specific items
* **Reversed attribute**: Changes display order but not DOM order
* **SEO impact**: Proper ordered list structure helps search engines understand procedural content
* **Internationalization**: Numbering adapts to different languages and writing systems
* **Print considerations**: Ordered lists work well in print media for instructions and procedures

---
