# `<details>`

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

The `<details>` element creates a disclosure widget that reveals or conceals additional content when activated by the user. It provides a native, accessible way to implement collapsible sections without JavaScript, offering an interactive interface for content that can be expanded or collapsed on demand. This element is particularly useful for FAQ sections, documentation, and any interface where space conservation and progressive disclosure are beneficial.

---

## Syntax and Variants

+ **Standard syntax**: `<details>...</details>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Contains both the summary and collapsible content
+ **No self-closing variant**: Must have proper opening and closing tags
+ **Optional summary**: Can function without `<summary>` element (browser provides default)

---

## Attributes

+ **Core attributes**:
  - `open` (optional): Boolean attribute that specifies the details should be visible to the user

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No deprecated attributes**: All original attributes remain supported

---

## Content Model

+ **Permitted content**: One `<summary>` element followed by flow content
+ **Required structure**:
  - First child: Optional `<summary>` element (if omitted, browser provides default)
  - Remaining content: Any flow content (paragraphs, lists, images, etc.)
+ **Allowed content**:
  - Text content and phrasing elements
  - Block-level elements: `<p>`, `<div>`, `<ul>`, `<ol>`, `<table>`, etc.
  - Other interactive elements (with caution)
  - Nested `<details>` elements
+ **Content restrictions**: No specific restrictions beyond normal flow content rules

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<main>` content areas
  - In `<aside>` sections for supplementary content
  - Inside `<article>` elements for expandable content blocks
  - Within `<form>` elements for optional form sections
+ **No usage limits**: Multiple details elements can be used within a document
+ **Nesting**: Details elements can be nested within other details elements

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - Border and padding (browser-dependent)
  - Triangular marker indicating expand/collapse state
  - Summary typically appears bold or with distinct styling
+ **Interactive behavior**:
  - Clicking toggles between expanded and collapsed states
  - Keyboard accessible (Enter or Space to toggle)
  - Smooth opening/closing animation in most browsers
  - Maintains state during page navigation if not reloaded
+ **Semantic meaning**:
  - Represents a disclosure widget with interactive show/hide functionality
  - Screen readers announce as expandable/collapsible region
  - Provides native accessibility without ARIA requirements
+ **Accessibility**:
  - Built-in keyboard navigation and screen reader support
  - Automatic ARIA attributes management
  - Focus management handled by browser

---

## Examples

**Basic details element:**
```html
<details>
  <summary>How does this work?</summary>
  <p>When you click the summary, the content below becomes visible. 
  Click it again to hide the content.</p>
</details>
```

**Pre-opened details:**
```html
<details open>
  <summary>Important Instructions (Expanded by Default)</summary>
  <p>These instructions are visible by default because the 
  <code>open</code> attribute is present.</p>
</details>
```

**Multiple details in FAQ format:**
```html
<h2>Frequently Asked Questions</h2>

<details>
  <summary>What is your return policy?</summary>
  <p>We offer a 30-day return policy for all unused items in original 
  packaging. Returns must be initiated within 30 days of purchase.</p>
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

**Styled details with CSS:**
```html
<details class="custom-details">
  <summary class="custom-summary">Styled Details Element</summary>
  <div class="details-content">
    <p>This details element has custom styling applied through CSS.</p>
    <ul>
      <li>Custom borders and colors</li>
      <li>Animated transitions</li>
      <li>Enhanced visual feedback</li>
    </ul>
  </div>
</details>

<style>
.custom-details {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  margin: 16px 0;
  overflow: hidden;
}

.custom-summary {
  background-color: #f5f5f5;
  padding: 12px 16px;
  cursor: pointer;
  font-weight: 600;
  list-style: none; /* Remove default triangle */
  position: relative;
}

.custom-summary::-webkit-details-marker {
  display: none; /* Remove default triangle in WebKit */
}

.custom-summary::after {
  content: "▶";
  position: absolute;
  right: 16px;
  transition: transform 0.2s ease;
}

.custom-details[open] .custom-summary::after {
  transform: rotate(90deg);
}

.details-content {
  padding: 16px;
  background-color: white;
  border-top: 1px solid #e0e0e0;
}

.custom-details[open] .custom-summary {
  background-color: #007bff;
  color: white;
}
</style>
```

**Details with complex content:**
```html
<details>
  <summary>Product Specifications</summary>
  <div class="specs-grid">
    <div class="spec-item">
      <strong>Dimensions:</strong> 10" × 8" × 2"
    </div>
    <div class="spec-item">
      <strong>Weight:</strong> 1.5 lbs
    </div>
    <div class="spec-item">
      <strong>Material:</strong> ABS Plastic
    </div>
    <div class="spec-item">
      <strong>Warranty:</strong> 2 Years
    </div>
  </div>
  <table>
    <caption>Technical Details</caption>
    <tr><th>Feature</th><th>Specification</th></tr>
    <tr><td>Power Input</td><td>100-240V AC</td></tr>
    <tr><td>Output</td><td>12V DC, 2A</td></tr>
  </table>
</details>

<style>
.specs-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px;
  margin-bottom: 16px;
}

.spec-item {
  padding: 8px;
  background-color: #f8f9fa;
  border-radius: 4px;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}

th {
  background-color: #f8f9fa;
}
</style>
```

**Nested details elements:**
```html
<details>
  <summary>Advanced Settings</summary>
  
  <details>
    <summary>Network Configuration</summary>
    <form>
      <label>IP Address: <input type="text" name="ip"></label>
      <label>Subnet Mask: <input type="text" name="subnet"></label>
    </form>
  </details>
  
  <details>
    <summary>Security Settings</summary>
    <form>
      <label>Firewall: <input type="checkbox" name="firewall"></label>
      <label>Encryption: 
        <select name="encryption">
          <option>AES-128</option>
          <option>AES-256</option>
        </select>
      </label>
    </form>
  </details>
</details>
```

**Details with JavaScript interaction:**
```html
<details id="interactive-details">
  <summary>Interactive Details</summary>
  <p>This details element has JavaScript enhancements.</p>
  <button onclick="closeDetails()">Close This Section</button>
</details>

<script>
const details = document.getElementById('interactive-details');

details.addEventListener('toggle', function() {
  if (this.open) {
    console.log('Details opened');
    // Perform actions when details opens
  } else {
    console.log('Details closed');
    // Perform actions when details closes
  }
});

function closeDetails() {
  details.open = false;
}
</script>
```

**Accordion pattern with multiple details:**
```html
<div class="accordion">
  <details>
    <summary>Section 1: Introduction</summary>
    <p>Welcome to the first section. This content is hidden by default.</p>
  </details>
  
  <details>
    <summary>Section 2: Getting Started</summary>
    <p>This section covers the basics of getting started with our product.</p>
    <ul>
      <li>Installation guide</li>
      <li>Configuration steps</li>
      <li>First-time setup</li>
    </ul>
  </details>
  
  <details>
    <summary>Section 3: Advanced Features</summary>
    <p>Explore the advanced capabilities of our platform.</p>
  </details>
</div>

<style>
.accordion details {
  border: 1px solid #ddd;
  border-bottom: none;
}

.accordion details:last-child {
  border-bottom: 1px solid #ddd;
}

.accordion summary {
  padding: 12px 16px;
  background-color: #f8f9fa;
  cursor: pointer;
  font-weight: 600;
}

.accordion details[open] summary {
  background-color: #007bff;
  color: white;
}

.accordion .details-content {
  padding: 16px;
  background-color: white;
}
</style>
```

**Details in a form for optional sections:**
```html
<form>
  <fieldset>
    <legend>Basic Information</legend>
    <label>Name: <input type="text" name="name" required></label>
    <label>Email: <input type="email" name="email" required></label>
  </fieldset>
  
  <details>
    <summary>Additional Information (Optional)</summary>
    <div class="form-group">
      <label>Company: <input type="text" name="company"></label>
      <label>Job Title: <input type="text" name="title"></label>
      <label>Phone: <input type="tel" name="phone"></label>
    </div>
  </details>
  
  <details>
    <summary>Preferences (Optional)</summary>
    <div class="form-group">
      <label>
        <input type="checkbox" name="newsletter"> Subscribe to newsletter
      </label>
      <label>
        <input type="checkbox" name="notifications"> Enable notifications
      </label>
    </div>
  </details>
  
  <button type="submit">Submit</button>
</form>

<style>
.form-group {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-top: 12px;
}

label {
  display: block;
}
</style>
```

**Details with animated transitions:**
```html
<details class="animated-details">
  <summary>Smooth Animated Section</summary>
  <div class="animated-content">
    <p>This content animates smoothly when expanding and collapsing.</p>
    <p>The animation is achieved using CSS transitions and the 
    <code>::before</code> pseudo-element for the marker.</p>
  </div>
</details>

<style>
.animated-details {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  margin: 16px 0;
}

.animated-details summary {
  padding: 16px;
  cursor: pointer;
  font-weight: 600;
  list-style: none;
  position: relative;
  transition: background-color 0.3s ease;
}

.animated-details summary:hover {
  background-color: #f8f9fa;
}

.animated-details summary::before {
  content: "▶";
  position: absolute;
  right: 16px;
  transition: transform 0.3s ease;
}

.animated-details[open] summary::before {
  transform: rotate(90deg);
}

.animated-content {
  padding: 0 16px;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease, padding 0.3s ease;
}

.animated-details[open] .animated-content {
  padding: 16px;
  max-height: 500px; /* Adjust based on content */
}
</style>
```

**Details for code examples:**
```html
<details class="code-example">
  <summary>View JavaScript Implementation</summary>
  <pre><code class="language-javascript">
function toggleDetails(detailsId) {
  const details = document.getElementById(detailsId);
  details.open = !details.open;
}

// Event listener for details toggle
document.querySelectorAll('details').forEach(details => {
  details.addEventListener('toggle', function(event) {
    console.log('Details state changed:', this.open);
  });
});
  </code></pre>
</details>

<style>
.code-example {
  border: 1px solid #e1e4e8;
  border-radius: 6px;
  margin: 16px 0;
}

.code-example summary {
  background-color: #f6f8fa;
  padding: 12px 16px;
  cursor: pointer;
  font-family: monospace;
  font-weight: 600;
  border-bottom: 1px solid #e1e4e8;
}

.code-example pre {
  margin: 0;
  padding: 16px;
  background-color: white;
  overflow-x: auto;
}

.code-example code {
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 14px;
}
</style>
```

**Details with custom open/close indicators:**
```html
<details class="custom-indicator">
  <summary>
    <span class="indicator" aria-hidden="true">+</span>
    <span class="summary-text">Click to expand</span>
  </summary>
  <div class="details-content">
    <p>This details element uses custom indicators instead of 
    the default triangle marker.</p>
    <p>The indicator changes from "+" to "−" when opened.</p>
  </div>
</details>

<style>
.custom-indicator summary {
  list-style: none;
  cursor: pointer;
  padding: 12px 16px;
  background-color: #f8f9fa;
  border-radius: 4px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.custom-indicator summary::-webkit-details-marker {
  display: none;
}

.custom-indicator .indicator {
  font-weight: bold;
  font-size: 18px;
  transition: transform 0.2s ease;
  width: 20px;
  text-align: center;
}

.custom-indicator[open] .indicator {
  content: "−";
}

.custom-indicator .summary-text {
  flex: 1;
}
</style>
```

**Details with state persistence:**
```html
<details id="persistent-details">
  <summary>Persistent Section (Remembers State)</summary>
  <p>This details element remembers whether it was open or closed 
  between page refreshes using localStorage.</p>
</details>

<script>
// Restore details state from localStorage
document.addEventListener('DOMContentLoaded', function() {
  const details = document.getElementById('persistent-details');
  const storedState = localStorage.getItem('persistentDetailsOpen');
  
  if (storedState === 'true') {
    details.open = true;
  }
  
  // Save state when changed
  details.addEventListener('toggle', function() {
    localStorage.setItem('persistentDetailsOpen', this.open);
  });
});
</script>
```

**Details in a responsive layout:**
```html
<div class="responsive-container">
  <div class="main-content">
    <h2>Main Article</h2>
    <p>This is the main content of the page...</p>
  </div>
  
  <aside class="sidebar">
    <details open>
      <summary>Related Links</summary>
      <nav>
        <ul>
          <li><a href="#section1">Section 1</a></li>
          <li><a href="#section2">Section 2</a></li>
          <li><a href="#section3">Section 3</a></li>
        </ul>
      </nav>
    </details>
    
    <details>
      <summary>Additional Resources</summary>
      <ul>
        <li><a href="#">Documentation</a></li>
        <li><a href="#">Support Forum</a></li>
        <li><a href="#">API Reference</a></li>
      </ul>
    </details>
  </aside>
</div>

<style>
.responsive-container {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 32px;
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.sidebar details {
  margin-bottom: 16px;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
}

.sidebar summary {
  padding: 12px 16px;
  background-color: #f8f9fa;
  cursor: pointer;
  font-weight: 600;
}

.sidebar .details-content {
  padding: 16px;
}

.sidebar ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.sidebar li {
  margin-bottom: 8px;
}

.sidebar a {
  text-decoration: none;
  color: #007bff;
}

.sidebar a:hover {
  text-decoration: underline;
}

@media (max-width: 768px) {
  .responsive-container {
    grid-template-columns: 1fr;
  }
}
</style>
```

**Details with print styles:**
```html
<details class="print-friendly">
  <summary>Additional Information</summary>
  <p>This content is hidden by default but will be visible when printed.</p>
  <p>Print styles ensure that all important information is available 
  in physical copies of the document.</p>
</details>

<style>
.print-friendly {
  border: 1px solid #ddd;
  margin: 16px 0;
}

.print-friendly summary {
  padding: 12px 16px;
  background-color: #f5f5f5;
  cursor: pointer;
}

@media print {
  .print-friendly {
    border: none;
  }
  
  .print-friendly summary {
    background-color: transparent;
    color: black;
    padding: 8px 0;
  }
  
  /* Force details to be open when printing */
  .print-friendly {
    display: block !important;
  }
  
  .print-friendly .details-content {
    display: block !important;
  }
  
  /* Hide the toggle indicator when printing */
  .print-friendly summary::before {
    display: none;
  }
}
</style>
```

---

## Notes

* **Browser compatibility**: Well supported in modern browsers, but always test fallback behavior
* **Progressive enhancement**: 
  - In non-supporting browsers, content is typically visible by default
  - Consider JavaScript polyfills for critical functionality in older browsers
* **Accessibility benefits**:
  - Native keyboard navigation (Tab, Enter/Space to toggle)
  - Automatic screen reader announcements
  - Built-in focus management
  - No additional ARIA attributes needed
* **JavaScript integration**:
  - `toggle` event fires when details state changes
  - `open` property can be manipulated programmatically
  - Can be controlled entirely via JavaScript if needed
* **Styling limitations**:
  - Default marker styling varies by browser
  - Custom markers require hiding the default with `list-style: none`
  - Animation capabilities depend on browser implementation
* **Common mistakes**:
  - Placing block-level elements inside `<summary>`
  - Forgetting to hide default markers when using custom indicators
  - Overusing nested details which can confuse users
  - Not providing adequate visual feedback for interactive states
* **SEO considerations**: 
  - Content inside details is typically indexed by search engines
  - Some search engines may treat collapsed content differently
* **Best practices**:
  - Use clear, descriptive text in summaries
  - Provide adequate spacing and visual hierarchy
  - Test keyboard navigation and screen reader compatibility
  - Consider print styles for important collapsed content
  - Use sparingly to avoid overwhelming users with too many interactive elements
* **Performance**: Generally lightweight, but complex content inside many details elements may impact initial page load

---
