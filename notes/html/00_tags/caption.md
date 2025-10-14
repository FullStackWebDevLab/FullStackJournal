# `<caption>`

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

The `<caption>` element provides a title or explanatory text for a table. It serves as a visible label that describes the table's content, purpose, or context, making the table more accessible and understandable for all users, including those using screen readers. The caption is typically displayed above the table but can be positioned elsewhere with CSS.

---

## Syntax and Variants

+ **Standard syntax**: `<caption>...</caption>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain text and inline elements
+ **No self-closing variant**: Must contain content
+ **Table association**: Always used as the first child of a `<table>` element

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies on semantic role within table structure
+ **Commonly used**: `class`, `id` for styling and scripting

---

## Content Model

+ **Permitted content**: Flow content, but typically phrasing content
+ **Allowed content**:
  - Text and character references
  - Phrasing elements: `<strong>`, `<em>`, `<span>`, `<a>`, etc.
  - Some interactive elements in appropriate contexts
+ **Not recommended**: Block-level elements (though technically allowed in flow content)
+ **Text focus**: Primarily intended for descriptive text content

---

## Context

+ **Required parent**: Must be a direct child of `<table>` element
+ **Position requirements**: 
  - Must be the first child of the `<table>` element
  - Should appear before `<colgroup>`, `<thead>`, `<tbody>`, `<tfoot>`, or `<tr>`
+ **Single instance**: Only one `<caption>` allowed per `<table>`
+ **Table relationship**: Describes the entire table, not specific sections

---

## Behavior and Semantics

+ **Default display**: Table-caption element
+ **Default styling**:
  - `display: table-caption`
  - `text-align: center`
  - Typically appears above the table
  - Inherits font properties from parent
+ **Semantic meaning**:
  - Provides a title or description for the table
  - Screen readers announce the caption before reading table content
  - Establishes context for the tabular data
+ **Accessibility**: Essential for screen reader users to understand table purpose and content

---

## Examples

**Basic table caption:**
```html
<table>
  <caption>Employee Directory</caption>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Department</th>
      <th scope="col">Email</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John Smith</td>
      <td>Engineering</td>
      <td>john@example.com</td>
    </tr>
  </tbody>
</table>
```

**Styled caption with CSS:**
```html
<table class="financial-table">
  <caption class="table-caption">Quarterly Financial Report 2024</caption>
  <thead>
    <tr>
      <th scope="col">Category</th>
      <th scope="col">Q1</th>
      <th scope="col">Q2</th>
      <th scope="col">Q3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Revenue</th>
      <td>$125,000</td>
      <td>$138,000</td>
      <td>$142,000</td>
    </tr>
  </tbody>
</table>

<style>
.table-caption {
  font-size: 1.2em;
  font-weight: bold;
  color: #2c3e50;
  padding: 10px;
  background-color: #f8f9fa;
  border-bottom: 2px solid #3498db;
  margin-bottom: 10px;
  text-align: left;
}
</style>
```

**Caption with inline formatting:**
```html
<table>
  <caption>
    <strong>Monthly Sales Performance</strong> 
    - <em>All figures in thousands of USD</em>
  </caption>
  <thead>
    <tr>
      <th scope="col">Salesperson</th>
      <th scope="col">Region</th>
      <th scope="col">Sales</th>
      <th scope="col">Target</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John Smith</td>
      <td>North America</td>
      <td>45</td>
      <td>40</td>
    </tr>
  </tbody>
</table>
```

**Caption with positioning using CSS:**
```html
<table class="captioned-table">
  <caption class="caption-bottom">Table 1: Product Inventory Summary</caption>
  <thead>
    <tr>
      <th scope="col">Product</th>
      <th scope="col">Category</th>
      <th scope="col">Stock</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Wireless Headphones</td>
      <td>Audio</td>
      <td>45</td>
      <td>$199.99</td>
    </tr>
  </tbody>
</table>

<style>
.captioned-table {
  caption-side: bottom;
  border-collapse: collapse;
}

.caption-bottom {
  padding: 10px;
  background-color: #f8f9fa;
  border-top: 2px solid #dee2e6;
  font-style: italic;
  margin-top: 10px;
}
</style>
```

**Accessible caption with ARIA attributes:**
```html
<table aria-describedby="table-desc">
  <caption id="table-title">Project Timeline and Milestones</caption>
  <thead>
    <tr>
      <th scope="col">Phase</th>
      <th scope="col">Start Date</th>
      <th scope="col">End Date</th>
      <th scope="col">Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Planning</td>
      <td>2024-01-15</td>
      <td>2024-02-28</td>
      <td>Completed</td>
    </tr>
  </tbody>
</table>
<div id="table-desc" class="visually-hidden">
  This table shows the project timeline with start dates, end dates, and current status for each phase.
</div>
```

**Caption with numbering for multiple tables:**
```html
<table>
  <caption>Table 1: Demographic Information of Survey Participants</caption>
  <thead>
    <tr>
      <th scope="col">Age Group</th>
      <th scope="col">Count</th>
      <th scope="col">Percentage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>18-25</td>
      <td>150</td>
      <td>30%</td>
    </tr>
  </tbody>
</table>

<table>
  <caption>Table 2: Survey Responses by Category</caption>
  <thead>
    <tr>
      <th scope="col">Category</th>
      <th scope="col">Positive</th>
      <th scope="col">Neutral</th>
      <th scope="col">Negative</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Product Quality</td>
      <td>85%</td>
      <td>10%</td>
      <td>5%</td>
    </tr>
  </tbody>
</table>
```

**Caption with source attribution:**
```html
<table>
  <caption>
    Annual Rainfall Data (2019-2023)
    <br>
    <small>Source: National Weather Service, Climate Data Division</small>
  </caption>
  <thead>
    <tr>
      <th scope="col">Year</th>
      <th scope="col">Rainfall (inches)</th>
      <th scope="col">Deviation from Average</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2023</td>
      <td>42.5</td>
      <td>+2.3</td>
    </tr>
  </tbody>
</table>
```

**Interactive caption with JavaScript:**
```html
<table id="data-table">
  <caption>
    <span>User Activity Log</span>
    <button id="toggle-view" class="caption-button">Show/Hide Details</button>
  </caption>
  <thead>
    <tr>
      <th scope="col">User</th>
      <th scope="col">Action</th>
      <th scope="col" class="detail-column">Details</th>
      <th scope="col">Timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>john@example.com</td>
      <td>Login</td>
      <td class="detail-column">Successful authentication</td>
      <td>2024-03-15 09:30:00</td>
    </tr>
  </tbody>
</table>

<style>
.caption-button {
  margin-left: 20px;
  padding: 2px 8px;
  font-size: 0.8em;
}

.detail-column {
  display: table-cell;
}
</style>

<script>
document.getElementById('toggle-view').addEventListener('click', function() {
  const detailColumns = document.querySelectorAll('.detail-column');
  detailColumns.forEach(col => {
    col.style.display = col.style.display === 'none' ? 'table-cell' : 'none';
  });
});
</script>
```

**Caption in a complex table structure:**
```html
<table class="complex-data">
  <caption>
    <strong>Comparative Analysis: Market Share by Region (2020-2024)</strong>
    <br>
    <span class="caption-subtitle">Data represents percentage of total market captured by leading competitors</span>
  </caption>
  <colgroup>
    <col span="1" style="background-color:#f8f9fa">
    <col span="4" style="background-color:#ffffff">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Company</th>
      <th scope="col">2020</th>
      <th scope="col">2021</th>
      <th scope="col">2022</th>
      <th scope="col">2023</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Company A</th>
      <td>25%</td>
      <td>28%</td>
      <td>30%</td>
      <td>32%</td>
    </tr>
    <tr>
      <th scope="row">Company B</th>
      <td>30%</td>
      <td>28%</td>
      <td>26%</td>
      <td>24%</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row">Market Total</th>
      <td colspan="4">Remaining percentage distributed among smaller competitors</td>
    </tr>
  </tfoot>
</table>

<style>
.complex-data caption {
  text-align: center;
  padding: 15px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  font-size: 1.3em;
  margin-bottom: 0;
}

.caption-subtitle {
  font-size: 0.8em;
  opacity: 0.9;
  font-weight: normal;
}
</style>
```

**Responsive caption design:**
```html
<table class="responsive-table">
  <caption class="responsive-caption">
    Product Feature Comparison Across Different Plans
    <span class="caption-context">(Updated March 2024)</span>
  </caption>
  <thead>
    <tr>
      <th scope="col">Feature</th>
      <th scope="col">Basic</th>
      <th scope="col">Pro</th>
      <th scope="col">Enterprise</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td data-label="Feature">Storage</td>
      <td data-label="Basic">10GB</td>
      <td data-label="Pro">100GB</td>
      <td data-label="Enterprise">1TB</td>
    </tr>
  </tbody>
</table>

<style>
.responsive-caption {
  font-size: 1.1em;
  font-weight: 600;
  padding: 12px;
  background-color: #f8f9fa;
  border-bottom: 1px solid #dee2e6;
}

.caption-context {
  font-size: 0.9em;
  font-weight: normal;
  color: #6c757d;
}

@media (max-width: 768px) {
  .responsive-caption {
    font-size: 1em;
    padding: 8px;
    text-align: left;
  }
  
  .caption-context {
    display: block;
    margin-top: 4px;
  }
}
</style>
```

---

## Notes

* **Position requirement**: Must be the first child of the `<table>` element for valid HTML
* **Accessibility importance**: 
  - Screen readers read captions before table content
  - Provides essential context for understanding tabular data
  - Required for WCAG compliance in many cases
* **CSS positioning**: 
  - Default: `caption-side: top`
  - Can be changed to `caption-side: bottom`
  - Full CSS styling capabilities available
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Placing `<caption>` after other table elements
  - Using multiple `<caption>` elements (only one allowed)
  - Using for non-table content
  - Making captions too long or complex
  - Forgetting to include captions for data tables
* **SEO benefits**: Helps search engines understand table content and context
* **Print considerations**: Captions maintain their position when tables break across pages
* **Internationalization**: Works well with different languages and writing systems
* **Best practices**:
  - Keep captions concise but descriptive
  - Use numbering for multiple tables in documents
  - Include source attributions when appropriate
  - Ensure adequate contrast for readability
  - Test with screen readers for accessibility

---
