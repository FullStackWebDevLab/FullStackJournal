# `<li>`

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

The `<li>` (list item) element represents a single item in a list. It is used within ordered lists (`<ol>`), unordered lists (`<ul>`), and menu lists (`<menu>`) to define individual list entries. Each `<li>` encapsulates one discrete item in a collection, providing structure and semantic meaning to list content.

---

## Syntax and Variants

+ **Standard syntax**: `<li>...</li>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain various content types
+ **Closing tag optional**: In HTML, the closing tag is technically optional but recommended
+ **List member**: Always used within parent list elements

---

## Attributes

+ **Core attributes**:
  - `value` (for `<ol>` only): Sets the ordinal value for ordered lists (integer)
  - `type` (deprecated): Bullet or numbering style (use CSS instead)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No required attributes**: All attributes are optional

---

## Content Model

+ **Permitted content**: Flow content
+ **Allowed content**:
  - Text and phrasing content
  - Paragraphs, headings, links, images
  - Other lists (for nested structures)
  - Interactive elements and form controls
+ **Rich content**: Can contain complex HTML structures
+ **Nesting support**: Can contain `<ul>`, `<ol>`, or `<menu>` for sub-lists

---

## Context

+ **Required parent**: Must be a direct child of `<ul>`, `<ol>`, or `<menu>`
+ **Sibling relationships**: Multiple `<li>` elements form the list items
+ **Valid locations**:
  - Within `<ul>` for unordered/bulleted lists
  - Within `<ol>` for ordered/numbered lists  
  - Within `<menu>` for menu lists
+ **No standalone use**: Must always be contained within a list element

---

## Behavior and Semantics

+ **Default display**: Block-level element (within list context)
+ **Default styling**:
  - `display: list-item`
  - Inherits list marker from parent list
  - Typically has left padding/margin for marker positioning
+ **Semantic meaning**:
  - Represents an item in a list
  - Screen readers announce as "list item" within list context
  - Conveys membership in a collection
+ **Accessibility**: Helps screen reader users understand list structure and item relationships

---

## Examples

**Basic list items in unordered list:**
```html
<ul>
  <li>Milk</li>
  <li>Eggs</li>
  <li>Bread</li>
  <li>Butter</li>
</ul>
```

**List items with value attributes in ordered list:**
```html
<ol>
  <li value="10">Tenth item</li>
  <li>Eleventh item (automatically continues from 10)</li>
  <li value="50">Fiftieth item</li>
  <li>Fifty-first item</li>
</ol>
```

**Complex list items with rich content:**
```html
<ul class="article-list">
  <li>
    <h3><a href="/articles/web-accessibility">Web Accessibility Fundamentals</a></h3>
    <p>Learn the core principles of making websites accessible to all users.</p>
    <span class="meta">Published: March 15, 2024</span>
  </li>
  <li>
    <h3><a href="/articles/css-grid">Mastering CSS Grid Layout</a></h3>
    <p>Complete guide to creating modern layouts with CSS Grid.</p>
    <span class="meta">Published: March 10, 2024</span>
  </li>
  <li>
    <h3><a href="/articles/javascript-performance">JavaScript Performance Optimization</a></h3>
    <p>Techniques for writing efficient and fast JavaScript code.</p>
    <span class="meta">Published: March 5, 2024</span>
  </li>
</ul>
```

**Nested list items:**
```html
<ul>
  <li>
    Frontend Technologies
    <ul>
      <li>HTML5</li>
      <li>CSS3</li>
      <li>
        JavaScript
        <ul>
          <li>Vanilla JS</li>
          <li>React</li>
          <li>Vue</li>
        </ul>
      </li>
    </ul>
  </li>
  <li>
    Backend Technologies
    <ul>
      <li>Node.js</li>
      <li>Python</li>
      <li>Java</li>
    </ul>
  </li>
</ul>
```

**Interactive list items for navigation:**
```html
<nav aria-label="User menu">
  <ul class="user-menu">
    <li>
      <a href="/profile" class="menu-item">
        <svg class="menu-icon" aria-hidden="true">...</svg>
        Profile Settings
      </a>
    </li>
    <li>
      <a href="/orders" class="menu-item">
        <svg class="menu-icon" aria-hidden="true">...</svg>
        Order History
      </a>
    </li>
    <li>
      <a href="/billing" class="menu-item">
        <svg class="menu-icon" aria-hidden="true">...</svg>
        Billing Information
      </a>
    </li>
    <li role="separator"></li>
    <li>
      <button class="menu-item" onclick="logout()">
        <svg class="menu-icon" aria-hidden="true">...</svg>
        Log Out
      </button>
    </li>
  </ul>
</nav>
```

**List items with custom data attributes:**
```html
<ul class="product-list">
  <li class="product-item" 
      data-product-id="12345" 
      data-category="electronics" 
      data-price="299.99">
    <img src="laptop.jpg" alt="Gaming Laptop">
    <h4>Gaming Laptop Pro</h4>
    <p>High-performance laptop for gaming and creative work.</p>
    <span class="price">$299.99</span>
    <button class="add-to-cart">Add to Cart</button>
  </li>
  <li class="product-item" 
      data-product-id="12346" 
      data-category="electronics" 
      data-price="199.99">
    <img src="tablet.jpg" alt="Drawing Tablet">
    <h4>Drawing Tablet</h4>
    <p>Professional drawing tablet with pressure sensitivity.</p>
    <span class="price">$199.99</span>
    <button class="add-to-cart">Add to Cart</button>
  </li>
</ul>
```

**Accessible list items with ARIA roles:**
```html
<ul role="list" aria-labelledby="todo-heading">
  <li role="listitem" aria-checked="false">
    <label>
      <input type="checkbox" onchange="toggleTask(this)">
      Buy groceries for the week
    </label>
  </li>
  <li role="listitem" aria-checked="true">
    <label>
      <input type="checkbox" checked onchange="toggleTask(this)">
      Finish project proposal
    </label>
  </li>
  <li role="listitem" aria-checked="false">
    <label>
      <input type="checkbox" onchange="toggleTask(this)">
      Schedule team meeting
    </label>
  </li>
</ul>
```

**Mixed content list items:**
```html
<ol class="instructions">
  <li>
    <strong>Prepare the workspace</strong>
    <p>Clear a large, flat surface and gather all necessary tools.</p>
    <ul>
      <li>Screwdrivers (Phillips and flathead)</li>
      <li>Pliers</li>
      <li>Safety glasses</li>
    </ul>
  </li>
  <li>
    <strong>Assemble the frame</strong>
    <p>Connect the side panels to the base using the provided screws.</p>
    <img src="frame-assembly.jpg" alt="Frame assembly diagram">
  </li>
  <li>
    <strong>Install components</strong>
    <p>Mount the internal components according to the wiring diagram.</p>
    <div class="warning">
      <strong>Warning:</strong> Ensure power is disconnected before proceeding.
    </div>
  </li>
</ol>
```

---

## Notes

* **Closing tag rules**: In HTML, the closing `</li>` tag is optional but strongly recommended for clarity
* **Value attribute**: Only meaningful in `<ol>` elements; ignored in `<ul>`
* **CSS counters**: Can be used with CSS counters for custom numbering beyond `value` attribute
* **Accessibility considerations**:
  - Ensure list items are properly contained within parent list
  - Use ARIA roles carefully (usually redundant with native semantics)
  - Provide adequate text alternatives for non-text content
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using `<li>` outside of list containers
  - Forgetting to close list items in complex markup
  - Overusing complex markup when simple text would suffice
  - Not maintaining proper list structure in dynamic content
* **Styling flexibility**: Can be extensively styled with CSS while maintaining semantic value
* **JavaScript interaction**: Commonly used as targets for dynamic content and event handling
* **SEO benefits**: Proper list structure helps search engines understand content relationships
* **Mobile usability**: Ensure adequate touch target size for interactive list items

---
