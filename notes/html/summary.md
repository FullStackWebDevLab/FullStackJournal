# `<summary>`

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

The `<summary>` element specifies a summary, caption, or legend for a `<details>` element's disclosure box. It provides a visible heading that users can interact with to toggle the visibility of the additional content contained within the parent `<details>` element. This creates an accessible, native HTML disclosure widget without requiring JavaScript.

---

## Syntax and Variants

+ **Standard syntax**: `<summary>...</summary>`
+ **Not void**: Requires both opening and closing tags
+ **Mandatory pairing**: Must be the first child of a `<details>` element
+ **No self-closing variant**: Must contain content
+ **Single instance**: Only one `<summary>` element per `<details>` element

---

## Attributes

+ **No specific attributes**: The `<summary>` element has no attributes specific to its function
+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **Event attributes**: `onclick`, `onkeypress`, etc. for custom interaction handling
+ **No deprecated attributes**: All original functionality remains supported

---

## Content Model

+ **Permitted content**: Phrasing content or heading content
+ **Allowed content**:
  - Text and character references
  - Phrasing elements: `<strong>`, `<em>`, `<span>`, `<img>`, etc.
  - Heading elements: `<h1>`-`<h6>`, although typically not recommended
+ **Restricted content**: Cannot contain interactive content descendants
+ **Common patterns**: Typically contains brief text describing the disclosure content

---

## Context

+ **Required parent**: Must be a direct child of a `<details>` element
+ **Position requirement**: Must be the first child of its parent `<details>` element
+ **Sibling relationships**: Followed by the disclosure content (any flow content)
+ **Invalid contexts**: Cannot be used outside of a `<details>` element
+ **Nesting prohibition**: Cannot contain another `<details>` or `<summary>` element

---

## Behavior and Semantics

+ **Default display**: Block-level element (as first child of `<details>`)
+ **Default styling**:
  - `display: list-item` (creates a triangle marker in most browsers)
  - Standard text styling inherited from parent
  - Clickable cursor (`cursor: pointer` in many browsers)
+ **Interactive behavior**:
  - Clicking toggles the parent `<details>` element's open state
  - Supports keyboard navigation (Enter or Space to activate)
  - Manages `aria-expanded` state automatically in supporting browsers
+ **Semantic meaning**:
  - Represents a summary or label for a disclosure widget
  - Provides accessible name for the `<details>` element
  - Screen readers announce the element as a disclosure button
+ **Accessibility role**: Serves as the interactive control for the disclosure widget

---

## Examples

**Basic details/summary structure:**
```html
<details>
  <summary>Frequently Asked Questions</summary>
  <p>Here are answers to common questions about our service...</p>
</details>
```

**Simple disclosure widget:**
```html
<details>
  <summary>Click to learn more about our company</summary>
  <div>
    <h3>Our Story</h3>
    <p>Founded in 2010, we've been serving customers worldwide...</p>
  </div>
</details>
```

**FAQ section with multiple details:**
```html
<h2>Frequently Asked Questions</h2>

<details>
  <summary>What is your return policy?</summary>
  <p>We offer a 30-day money-back guarantee on all products. 
     Items must be returned in original condition with tags attached.</p>
</details>

<details>
  <summary>How long does shipping take?</summary>
  <p>Standard shipping takes 3-5 business days. Express shipping 
     is available for next-day delivery in most areas.</p>
</details>

<details>
  <summary>Do you ship internationally?</summary>
  <p>Yes, we ship to over 50 countries worldwide. International 
     shipping typically takes 7-14 business days.</p>
</details>
```

**Styled summary with custom marker:**
```html
<details class="custom-details">
  <summary class="custom-summary">
    Advanced Settings
  </summary>
  <div class="details-content">
    <label>
      <input type="checkbox" name="expert-mode"> Expert Mode
    </label>
    <label>
      <input type="checkbox" name="debug-logging"> Debug Logging
    </label>
  </div>
</details>

<style>
.custom-details {
  border: 1px solid #ddd;
  border-radius: 4px;
  margin-bottom: 1rem;
}

.custom-summary {
  padding: 12px 16px;
  background: #f5f5f5;
  cursor: pointer;
  font-weight: 600;
  list-style: none; /* Remove default triangle */
  position: relative;
}

.custom-summary::-webkit-details-marker {
  display: none; /* Remove default triangle in WebKit */
}

.custom-summary::before {
  content: "▶";
  margin-right: 8px;
  display: inline-block;
  transition: transform 0.2s;
}

.custom-details[open] .custom-summary::before {
  transform: rotate(90deg);
}

.details-content {
  padding: 16px;
  background: white;
  border-top: 1px solid #eee;
}
</style>
```

**Summary with complex content:**
```html
<details>
  <summary class="complex-summary">
    <span class="summary-title">Project Specifications</span>
    <span class="summary-meta">Last updated: March 15, 2024</span>
  </summary>
  <div class="specs-content">
    <h3>Technical Requirements</h3>
    <ul>
      <li>HTML5 compliant markup</li>
      <li>CSS3 with Flexbox/Grid layout</li>
      <li>JavaScript ES6+ features</li>
    </ul>
  </div>
</details>

<style>
.complex-summary {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.summary-title {
  font-weight: 600;
}

.summary-meta {
  font-size: 0.875em;
  color: #666;
}

.specs-content {
  padding: 16px;
  background: #f9f9f9;
}
</style>
```

**Nested details elements:**
```html
<details>
  <summary>Main Category</summary>
  
  <details>
    <summary>Subcategory 1</summary>
    <p>Content for subcategory 1...</p>
  </details>
  
  <details>
    <summary>Subcategory 2</summary>
    <p>Content for subcategory 2...</p>
  </details>
</details>
```

**Summary with icon and styling:**
```html
<details class="feature-details">
  <summary class="feature-summary">
    <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
      <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-6h2v6zm0-8h-2V7h2v2z"/>
    </svg>
    Important Information
  </summary>
  <div class="feature-content">
    <p>This feature requires additional configuration. Please ensure 
       you have the necessary permissions before proceeding.</p>
  </div>
</details>

<style>
.feature-details {
  border-left: 4px solid #007bff;
  margin-bottom: 1rem;
}

.feature-summary {
  padding: 12px;
  background: #e3f2fd;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 8px;
  font-weight: 600;
  list-style: none;
}

.feature-summary::-webkit-details-marker {
  display: none;
}

.feature-content {
  padding: 12px;
  background: #f8fbff;
}
</style>
```

**Programmatically controlled details:**
```html
<details id="programmatic-details">
  <summary>Click me or use the button below</summary>
  <p>This content can be toggled multiple ways.</p>
</details>

<button onclick="toggleDetails()">Toggle Details Programmatically</button>

<script>
function toggleDetails() {
  const details = document.getElementById('programmatic-details');
  details.open = !details.open;
}

// Add keyboard support
document.getElementById('programmatic-details').addEventListener('keydown', (e) => {
  if (e.key === 'Enter' || e.key === ' ') {
    e.preventDefault();
    e.target.closest('details').open = !e.target.closest('details').open;
  }
});
</script>
```

**Accessible details with ARIA:**
```html
<details class="accessible-details">
  <summary class="accessible-summary" 
           aria-expanded="false" 
           role="button" 
           tabindex="0">
    Accessibility Features
    <span class="visually-hidden">(click to expand)</span>
  </summary>
  <div class="accessible-content">
    <h3>Screen Reader Support</h3>
    <p>All features are fully accessible to screen reader users.</p>
    <h3>Keyboard Navigation</h3>
    <p>Complete keyboard navigation support included.</p>
  </div>
</details>

<style>
.accessible-summary {
  padding: 12px;
  background: #333;
  color: white;
  cursor: pointer;
  border-radius: 4px;
}

.accessible-content {
  padding: 16px;
  border: 1px solid #ddd;
  border-top: none;
  border-radius: 0 0 4px 4px;
}

.visually-hidden {
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
</style>
```

**Form with collapsible sections:**
```html
<form class="multi-section-form">
  <details open>
    <summary class="form-section-summary">Personal Information</summary>
    
    <div class="form-fields">
      <label>
        Full Name:
        <input type="text" name="full_name" required>
      </label>
      <label>
        Email:
        <input type="email" name="email" required>
      </label>
    </div>
  </details>

  <details>
    <summary class="form-section-summary">Shipping Address</summary>
    
    <div class="form-fields">
      <label>
        Street Address:
        <input type="text" name="address" required>
      </label>
      <label>
        City:
        <input type="text" name="city" required>
      </label>
      <label>
        ZIP Code:
        <input type="text" name="zip" required>
      </label>
    </div>
  </details>

  <details>
    <summary class="form-section-summary">Payment Information</summary>
    
    <div class="form-fields">
      <label>
        Credit Card Number:
        <input type="text" name="card_number" required>
      </label>
      <label>
        Expiration Date:
        <input type="month" name="expiry" required>
      </label>
    </div>
  </details>
</form>

<style>
.multi-section-form {
  max-width: 500px;
}

.form-section-summary {
  background: #f8f9fa;
  padding: 16px;
  border: 1px solid #dee2e6;
  margin-bottom: 0;
  font-weight: 600;
  cursor: pointer;
}

.form-fields {
  padding: 20px;
  border: 1px solid #dee2e6;
  border-top: none;
  background: white;
}

.form-fields label {
  display: block;
  margin-bottom: 12px;
}

.form-fields input {
  display: block;
  width: 100%;
  padding: 8px;
  margin-top: 4px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
```

**Summary with animation:**
```html
<details class="animated-details">
  <summary class="animated-summary">
    Animated Section
    <span class="arrow">▼</span>
  </summary>
  <div class="animated-content">
    <p>This content slides in with a smooth animation when expanded.</p>
    <p>The animation is achieved using CSS transitions and the `details` element's open state.</p>
  </div>
</details>

<style>
.animated-details {
  overflow: hidden;
}

.animated-summary {
  padding: 16px;
  background: #007bff;
  color: white;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  list-style: none;
  transition: background-color 0.2s;
}

.animated-summary:hover {
  background: #0056b3;
}

.animated-summary::-webkit-details-marker {
  display: none;
}

.arrow {
  transition: transform 0.3s ease;
}

.animated-details[open] .arrow {
  transform: rotate(180deg);
}

.animated-content {
  padding: 0;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease, padding 0.3s ease;
}

.animated-details[open] .animated-content {
  padding: 16px;
  max-height: 200px; /* Adjust based on content */
}
</style>
```

**Table with expandable rows:**
```html
<table class="expandable-table">
  <thead>
    <tr>
      <th>Product</th>
      <th>Price</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td colspan="3" class="table-details-cell">
        <details>
          <summary class="table-summary">
            <span>Premium Widget</span>
            <span>$49.99</span>
            <span>In Stock</span>
          </summary>
          <div class="table-details-content">
            <p><strong>Description:</strong> High-quality widget with advanced features.</p>
            <p><strong>Features:</strong> Durable construction, 2-year warranty, free shipping</p>
          </div>
        </details>
      </td>
    </tr>
    <!-- Additional rows -->
  </tbody>
</table>

<style>
.expandable-table {
  width: 100%;
  border-collapse: collapse;
}

.table-details-cell {
  padding: 0;
}

.table-summary {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: 16px;
  padding: 12px;
  cursor: pointer;
  list-style: none;
  align-items: center;
}

.table-summary:hover {
  background: #f5f5f5;
}

.table-summary::-webkit-details-marker {
  display: none;
}

.table-details-content {
  padding: 16px;
  background: #f9f9f9;
  border-top: 1px solid #eee;
}
</style>
```

**Summary with badge counter:**
```html
<details class="notification-details">
  <summary class="notification-summary">
    Notifications
    <span class="badge">3</span>
  </summary>
  <div class="notification-list">
    <div class="notification-item">New message from John</div>
    <div class="notification-item">Your order has shipped</div>
    <div class="notification-item">System update available</div>
  </div>
</details>

<style>
.notification-details {
  width: 300px;
}

.notification-summary {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 16px;
  background: #f8f9fa;
  border: 1px solid #dee2e6;
  cursor: pointer;
  list-style: none;
  font-weight: 600;
}

.notification-summary::-webkit-details-marker {
  display: none;
}

.badge {
  background: #dc3545;
  color: white;
  padding: 2px 8px;
  border-radius: 12px;
  font-size: 0.875em;
  font-weight: normal;
}

.notification-list {
  border: 1px solid #dee2e6;
  border-top: none;
  background: white;
}

.notification-item {
  padding: 12px 16px;
  border-bottom: 1px solid #eee;
}

.notification-item:last-child {
  border-bottom: none;
}
</style>
```

---

## Notes

* **Browser support**: 
  - Well supported in all modern browsers
  - Internet Explorer does not support `<details>` or `<summary>`
  - Polyfills available for legacy browser support

* **Accessibility considerations**:
  - Native keyboard navigation (Enter/Space) supported in modern browsers
  - Screen readers properly announce the expandable nature
  - Automatic `aria-expanded` state management in supporting browsers
  - For maximum accessibility, ensure proper focus indicators

* **Common mistakes**:
  - Using `<summary>` outside of `<details>` element
  - Placing `<summary>` as not the first child of `<details>`
  - Using multiple `<summary>` elements within one `<details>`
  - Forgetting to style the default marker in WebKit browsers
  - Overriding accessibility features without proper alternatives

* **Styling considerations**:
  - Default triangle marker can be hidden with `list-style: none`
  - Custom markers can be added with pseudo-elements
  - The `[open]` attribute selector targets expanded state
  - WebKit requires `::-webkit-details-marker` for custom styling

* **JavaScript integration**:
  - `details.open` property controls expansion state
  - `toggle` event fires when state changes
  - Can be controlled programmatically while maintaining semantics
  - Useful for synchronized multiple disclosures

* **Best practices**:
  - Keep summary text concise and descriptive
  - Ensure adequate touch targets for mobile devices
  - Maintain visible focus indicators for keyboard users
  - Test with screen readers for accessibility compliance
  - Consider providing fallback for non-supporting browsers
  - Use consistent styling patterns throughout application

* **Polyfill options**:
  - Several JavaScript polyfills available for IE support
  - Typically add click handlers and ARIA attributes
  - Should degrade gracefully when JavaScript is disabled

* **SEO implications**:
  - Content within `<details>` is fully indexed by search engines
  - Can be used to organize content without hiding it from crawlers
  - Useful for FAQ pages and collapsible content sections

---
