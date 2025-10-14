# `<th>`

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

The `<th>` (table header) element defines a header cell in an HTML table. It represents a column or row header that provides context and description for the data cells in its corresponding column or row. Header cells are essential for accessibility and semantic structure, helping users understand the relationships and meaning of tabular data.

---

## Syntax & Variants

+ **Standard syntax**: `<th>...</th>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain various content types
+ **No self-closing variant**: Must contain content or be empty
+ **Closing tag optional**: Technically optional in HTML but recommended

---

## Attributes

+ **Core attributes**:
  - `scope` (optional): Defines the cells the header applies to (`col`, `row`, `colgroup`, `rowgroup`)
  - `colspan` (optional): Number of columns the header spans (positive integer)
  - `rowspan` (optional): Number of rows the header spans (positive integer)
  - `headers` (optional): Space-separated list of header cell IDs (for complex tables)
  - `abbr` (optional): Abbreviated version of header content

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Deprecated attributes**:
  - `align` (use CSS `text-align` instead)
  - `bgcolor` (use CSS `background-color` instead)
  - `height` (use CSS `height` instead)
  - `width` (use CSS `width` instead)
  - `valign` (use CSS `vertical-align` instead)
  - `nowrap` (use CSS `white-space: nowrap` instead)
  - `axis` (use `scope` instead)

---

## Content Model

+ **Permitted content**: Flow content, but with no `<header>`, `<footer>`, sectioning content, or heading content descendants
+ **Allowed content**:
  - Text and phrasing content
  - Links, spans, emphasis elements
  - Images and other inline elements
+ **Restricted content**: Cannot contain block-level elements like `<div>`, `<p>`, or heading elements
+ **Header focus**: Primarily intended for header labels, not complex content

---

## Context

+ **Required parent**: Must be a direct child of `<tr>` element
+ **Sibling relationships**:
  - Can be mixed with `<td>` elements in the same row
  - Multiple `<th>` elements can form header rows or columns
+ **Position significance**:
  - In `<thead>`: Typically column headers
  - In `<tbody>`: Typically row headers
  - First cell in row: Often a row header

---

## Behavior and Semantics

+ **Default display**: Table-cell element
+ **Default styling**:
  - `display: table-cell`
  - `font-weight: bold` (typically)
  - `text-align: center` (typically)
  - `padding: 1px` (varies by browser)
  - Inherits table's border and spacing properties
+ **Semantic meaning**:
  - Represents a header for table data
  - Screen readers announce as header and associate with data cells
  - Provides context and meaning for tabular data
+ **Accessibility**: Critical for screen reader users to understand table structure and relationships

---

## Examples

**Basic column headers:**
```html
<table>
  <tr>
    <th scope="col">Name</th>
    <th scope="col">Age</th>
    <th scope="col">Department</th>
  </tr>
  <tr>
    <td>John Smith</td>
    <td>32</td>
    <td>Engineering</td>
  </tr>
</table>
```

**Row headers in table body:**
```html
<table>
  <tr>
    <th scope="row">Revenue</th>
    <td>$125,000</td>
    <td>$138,000</td>
  </tr>
  <tr>
    <th scope="row">Expenses</th>
    <td>$89,000</td>
    <td>$92,000</td>
  </tr>
</table>
```

**Headers with colspan and rowspan:**
```html
<table>
  <tr>
    <th colspan="2" scope="colgroup">Personal Information</th>
    <th scope="col">Employment</th>
  </tr>
  <tr>
    <th scope="col">First Name</th>
    <th scope="col">Last Name</th>
    <th scope="col">Department</th>
  </tr>
  <tr>
    <td>John</td>
    <td>Smith</td>
    <td>Engineering</td>
  </tr>
</table>
```

**Styled header cells:**
```html
<table class="financial-table">
  <thead>
    <tr>
      <th scope="col" class="main-header">Financial Report</th>
      <th scope="col" class="quarter-header">Q1 2024</th>
      <th scope="col" class="quarter-header">Q2 2024</th>
      <th scope="col" class="quarter-header">Q3 2024</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row" class="metric-header">Revenue</th>
      <td class="amount">$125,000</td>
      <td class="amount">$138,000</td>
      <td class="amount">$142,000</td>
    </tr>
  </tbody>
</table>

<style>
.main-header { background-color: #2c3e50; color: white; }
.quarter-header { background-color: #34495e; color: white; }
.metric-header { background-color: #ecf0f1; font-weight: bold; }
</style>
```

**Accessible headers with scope and abbr:**
```html
<table>
  <thead>
    <tr>
      <th scope="col" abbr="Emp ID">Employee Identification Number</th>
      <th scope="col" abbr="Name">Full Name of Employee</th>
      <th scope="col" abbr="Dept">Department Assignment</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">EMP-001</th>
      <td>John Smith</td>
      <td>Engineering</td>
    </tr>
  </tbody>
</table>
```

**Complex table with multiple header levels:**
```html
<table>
  <caption>Quarterly Sales Performance by Region</caption>
  <thead>
    <tr>
      <th scope="col" rowspan="2">Region</th>
      <th scope="colgroup" colspan="4">Quarterly Sales (in thousands)</th>
    </tr>
    <tr>
      <th scope="col">Q1</th>
      <th scope="col">Q2</th>
      <th scope="col">Q3</th>
      <th scope="col">Q4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">North America</th>
      <td>$450</td>
      <td>$520</td>
      <td>$480</td>
      <td>$550</td>
    </tr>
    <tr>
      <th scope="row">Europe</th>
      <td>$380</td>
      <td>$420</td>
      <td>$410</td>
      <td>$460</td>
    </tr>
  </tbody>
</table>
```

**Headers with sorting functionality:**
```html
<table id="sortable-table">
  <thead>
    <tr>
      <th scope="col" data-sort="string">
        Name 
        <span class="sort-indicator">↕</span>
      </th>
      <th scope="col" data-sort="number">
        Age
        <span class="sort-indicator">↕</span>
      </th>
      <th scope="col" data-sort="string">
        Department
        <span class="sort-indicator">↕</span>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John Smith</td>
      <td>32</td>
      <td>Engineering</td>
    </tr>
  </tbody>
</table>

<script>
document.querySelectorAll('#sortable-table th').forEach(header => {
  header.addEventListener('click', () => {
    const sortType = header.dataset.sort;
    // Implement sorting logic
    console.log(`Sorting by ${header.textContent} as ${sortType}`);
  });
});
</script>
```

**Responsive header design:**
```html
<table class="responsive-table">
  <thead>
    <tr>
      <th scope="col" data-label="Product">Product Details</th>
      <th scope="col" data-label="Price">Price</th>
      <th scope="col" data-label="Stock">Stock Status</th>
      <th scope="col" data-label="Actions">Actions</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td data-label="Product">Wireless Headphones Pro</td>
      <td data-label="Price">$199.99</td>
      <td data-label="Stock">In Stock</td>
      <td data-label="Actions">
        <button>Add to Cart</button>
      </td>
    </tr>
  </tbody>
</table>

<style>
@media (max-width: 768px) {
  .responsive-table thead {
    display: none;
  }
  
  .responsive-table th[data-label]::before {
    content: attr(data-label);
    font-weight: bold;
    display: block;
  }
}
</style>
```

**Headers with icons and additional information:**
```html
<table class="feature-table">
  <thead>
    <tr>
      <th scope="col">
        <span class="header-content">
          <span class="header-icon">👤</span>
          User Management
        </span>
        <span class="header-info" title="Number of active users">(250 users)</span>
      </th>
      <th scope="col">
        <span class="header-content">
          <span class="header-icon">💰</span>
          Billing
        </span>
        <span class="header-info" title="Monthly recurring revenue">($15K MRR)</span>
      </th>
      <th scope="col">
        <span class="header-content">
          <span class="header-icon">📊</span>
          Analytics
        </span>
        <span class="header-info" title="Active metrics">(12 metrics)</span>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Active users: 250</td>
      <td>Monthly revenue: $15,000</td>
      <td>Reports generated: 45</td>
    </tr>
  </tbody>
</table>
```

**Accessible headers with ARIA attributes:**
```html
<table role="grid" aria-labelledby="projects-title">
  <caption id="projects-title">Project Status Dashboard</caption>
  <thead>
    <tr role="row">
      <th role="columnheader" scope="col" aria-sort="none">
        Project Name
      </th>
      <th role="columnheader" scope="col" aria-sort="none">
        Deadline
      </th>
      <th role="columnheader" scope="col" aria-sort="none">
        Status
      </th>
      <th role="columnheader" scope="col" aria-sort="none">
        Team Lead
      </th>
    </tr>
  </thead>
  <tbody>
    <tr role="row">
      <td role="gridcell">Website Redesign</td>
      <td role="gridcell">2024-06-15</td>
      <td role="gridcell">In Progress</td>
      <td role="gridcell">John Smith</td>
    </tr>
  </tbody>
</table>
```

---

## Notes

* **Semantic importance**: Differentiates header content from data content for accessibility
* **Scope attribute usage**:
  - `scope="col"`: Header for entire column
  - `scope="row"`: Header for entire row
  - `scope="colgroup"`: Header for group of columns
  - `scope="rowgroup"`: Header for group of rows
* **Accessibility requirements**:
  - Always use `scope` attribute for simple tables
  - Use `headers` attribute for complex tables with multiple header levels
  - Provide `abbr` for long header text when appropriate
  - Ensure header text is descriptive and concise
* **CSS styling**:
  - Typically styled with bold font weight
  - Often has different background colors from data cells
  - Use `text-align` consistent with data alignment
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using `<td>` instead of `<th>` for header content
  - Missing `scope` attributes in simple tables
  - Overusing complex content in header cells
  - Inconsistent header structure across similar tables
  - Not testing with screen readers
* **SEO benefits**: Proper header structure helps search engines understand table content
* **Mobile considerations**: Ensure header text remains readable on small screens
* **Print considerations**: Headers often repeat on each printed page for long tables

---
