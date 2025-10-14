# `<thead>`

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

The `<thead>` (table head) element defines a block of header rows in an HTML table. It groups one or more rows that contain column headers, providing semantic structure and enabling browsers to render table headers separately from the body content, especially useful for printing and scrolling large tables.

---

## Syntax and Variants

+ **Standard syntax**: `<thead>...</thead>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps one or more `<tr>` elements containing `<th>` cells
+ **No self-closing variant**: Must contain table rows
+ **Table section**: Part of table's structural grouping with `<tbody>` and `<tfoot>`

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies on semantic role within table structure
+ **Commonly used**: `class`, `id` for styling and scripting

---

## Content Model

+ **Permitted content**: Zero or more `<tr>` elements
+ **Required children**: At least one `<tr>` for meaningful header content
+ **Row restrictions**: Only `<tr>` elements allowed as direct children
+ **Header cells**: `<tr>` elements should typically contain `<th>` cells, not `<td>`

---

## Context

+ **Required parent**: Must be a direct child of `<table>` element
+ **Position requirements**: 
  - Must appear before `<tbody>` and after `<caption>`/`<colgroup>` if present
  - Can appear before or after `<tfoot>` (but only one `<thead>` per table)
+ **Sibling relationships**: 
  - Optional `<tbody>` and `<tfoot>` elements
  - Multiple `<tbody>` elements can follow
+ **Single instance**: Only one `<thead>` allowed per `<table>`

---

## Behavior and Semantics

+ **Default display**: Table-header-group element
+ **Default styling**:
  - `display: table-header-group`
  - No inherent visual styling differences from regular rows
  - Inherits table's border and spacing properties
+ **Functional behavior**:
  - Headers may repeat on each printed page for long tables
  - Can be kept visible during vertical scrolling in some contexts
  - Provides semantic grouping for assistive technologies
+ **Semantic meaning**:
  - Represents the header section of a table
  - Screen readers announce as table header section
  - Groups column headers for better accessibility
+ **Accessibility**: Helps screen reader users understand table structure and header relationships

---

## Examples

**Basic table with thead:**
```html
<table>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Age</th>
      <th scope="col">Department</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John Smith</td>
      <td>32</td>
      <td>Engineering</td>
    </tr>
    <tr>
      <td>Sarah Johnson</td>
      <td>28</td>
      <td>Marketing</td>
    </tr>
  </tbody>
</table>
```

**Styled thead with CSS:**
```html
<table class="styled-table">
  <thead class="table-header">
    <tr>
      <th scope="col">Product</th>
      <th scope="col">Price</th>
      <th scope="col">Stock</th>
      <th scope="col">Category</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Wireless Headphones</td>
      <td>$199.99</td>
      <td>In Stock</td>
      <td>Audio</td>
    </tr>
  </tbody>
</table>

<style>
.styled-table .table-header {
  background-color: #2c3e50;
  color: white;
}

.styled-table .table-header th {
  padding: 12px 15px;
  text-align: left;
  font-weight: 600;
  border-bottom: 2px solid #34495e;
}
</style>
```

**Multiple header rows in thead:**
```html
<table>
  <thead>
    <tr>
      <th scope="col" colspan="2">Personal Information</th>
      <th scope="col" colspan="3">Employment Details</th>
    </tr>
    <tr>
      <th scope="col">First Name</th>
      <th scope="col">Last Name</th>
      <th scope="col">Department</th>
      <th scope="col">Position</th>
      <th scope="col">Salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John</td>
      <td>Smith</td>
      <td>Engineering</td>
      <td>Senior Developer</td>
      <td>$95,000</td>
    </tr>
  </tbody>
</table>
```

**Complex table structure with all sections:**
```html
<table>
  <caption>Quarterly Financial Report 2024</caption>
  <thead>
    <tr>
      <th scope="col">Category</th>
      <th scope="col">Q1</th>
      <th scope="col">Q2</th>
      <th scope="col">Q3</th>
      <th scope="col">Q4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Revenue</th>
      <td>$125,000</td>
      <td>$138,000</td>
      <td>$142,000</td>
      <td>$156,000</td>
    </tr>
    <tr>
      <th scope="row">Expenses</th>
      <td>$89,000</td>
      <td>$92,000</td>
      <td>$95,000</td>
      <td>$98,000</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row">Net Profit</th>
      <td>$36,000</td>
      <td>$46,000</td>
      <td>$47,000</td>
      <td>$58,000</td>
    </tr>
  </tfoot>
</table>
```

**Accessible thead with ARIA attributes:**
```html
<table role="grid" aria-labelledby="sales-title">
  <caption id="sales-title">Monthly Sales Performance</caption>
  <thead role="rowgroup">
    <tr role="row">
      <th role="columnheader" scope="col">Salesperson</th>
      <th role="columnheader" scope="col">Region</th>
      <th role="columnheader" scope="col">Q1 Sales</th>
      <th role="columnheader" scope="col">Q2 Sales</th>
    </tr>
  </thead>
  <tbody role="rowgroup">
    <tr role="row">
      <td role="gridcell">John Smith</td>
      <td role="gridcell">North America</td>
      <td role="gridcell">$45,000</td>
      <td role="gridcell">$52,000</td>
    </tr>
  </tbody>
</table>
```

**Thead with sorting functionality:**
```html
<table id="sortable-table">
  <thead>
    <tr>
      <th scope="col" data-sort="string" class="sortable">
        Name 
        <span class="sort-indicator">↕</span>
      </th>
      <th scope="col" data-sort="number" class="sortable">
        Age
        <span class="sort-indicator">↕</span>
      </th>
      <th scope="col" data-sort="string" class="sortable">
        Department
        <span class="sort-indicator">↕</span>
      </th>
      <th scope="col" class="non-sortable">
        Actions
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John Smith</td>
      <td>32</td>
      <td>Engineering</td>
      <td>
        <button>Edit</button>
        <button>Delete</button>
      </td>
    </tr>
  </tbody>
</table>

<script>
document.querySelectorAll('.sortable').forEach(header => {
  header.addEventListener('click', function() {
    const sortType = this.dataset.sort;
    const columnIndex = Array.from(this.parentNode.children).indexOf(this);
    
    // Implement sorting logic
    sortTable(columnIndex, sortType);
    
    // Update sort indicators
    updateSortIndicators(this);
  });
});
</script>
```

**Fixed header with scrolling tbody:**
```html
<div class="table-container">
  <table class="scrollable-table">
    <thead class="fixed-header">
      <tr>
        <th scope="col">Product ID</th>
        <th scope="col">Product Name</th>
        <th scope="col">Category</th>
        <th scope="col">Price</th>
        <th scope="col">Stock</th>
      </tr>
    </thead>
    <tbody class="scrollable-body">
      <tr>
        <td>P001</td>
        <td>Wireless Headphones Pro</td>
        <td>Audio</td>
        <td>$199.99</td>
        <td>45</td>
      </tr>
      <!-- Many more rows -->
    </tbody>
  </table>
</div>

<style>
.table-container {
  height: 400px;
  overflow: auto;
  border: 1px solid #ddd;
}

.scrollable-table {
  width: 100%;
  border-collapse: collapse;
}

.fixed-header {
  position: sticky;
  top: 0;
  background-color: #f8f9fa;
  z-index: 10;
}

.scrollable-body {
  display: block;
  max-height: 350px;
  overflow-y: auto;
}
</style>
```

**Thead with responsive design:**
```html
<table class="responsive-table">
  <thead>
    <tr>
      <th scope="col" data-label="Product">Product Information</th>
      <th scope="col" data-label="Price">Pricing</th>
      <th scope="col" data-label="Stock">Inventory</th>
      <th scope="col" data-label="Actions">Management</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td data-label="Product">
        <strong>Wireless Headphones Pro</strong>
        <br>
        <span class="sku">SKU: WHP-2024</span>
      </td>
      <td data-label="Price">$199.99</td>
      <td data-label="Stock">
        <span class="stock-status in-stock">In Stock (45)</span>
      </td>
      <td data-label="Actions">
        <button class="btn-small">Edit</button>
        <button class="btn-small">Restock</button>
      </td>
    </tr>
  </tbody>
</table>

<style>
@media (max-width: 768px) {
  .responsive-table thead {
    display: none;
  }
  
  .responsive-table tr {
    display: block;
    margin-bottom: 1rem;
    border: 1px solid #ddd;
  }
  
  .responsive-table td {
    display: block;
    text-align: right;
    border-bottom: 1px solid #eee;
  }
  
  .responsive-table td::before {
    content: attr(data-label);
    float: left;
    font-weight: bold;
  }
}
</style>
```

**Thead with complex column grouping:**
```html
<table>
  <thead>
    <tr>
      <th scope="col" rowspan="2">Employee</th>
      <th scope="colgroup" colspan="3">Q1 2024</th>
      <th scope="colgroup" colspan="3">Q2 2024</th>
    </tr>
    <tr>
      <th scope="col">Sales</th>
      <th scope="col">Target</th>
      <th scope="col">% Achieved</th>
      <th scope="col">Sales</th>
      <th scope="col">Target</th>
      <th scope="col">% Achieved</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">John Smith</th>
      <td>$45,000</td>
      <td>$40,000</td>
      <td>112%</td>
      <td>$52,000</td>
      <td>$45,000</td>
      <td>115%</td>
    </tr>
    <tr>
      <th scope="row">Sarah Johnson</th>
      <td>$38,000</td>
      <td>$35,000</td>
      <td>108%</td>
      <td>$42,000</td>
      <td>$40,000</td>
      <td>105%</td>
    </tr>
  </tbody>
</table>
```

---

## Notes

* **Semantic importance**: Provides structural meaning to table headers beyond visual styling
* **Print behavior**: Browsers may repeat `<thead>` content on each printed page for long tables
* **Accessibility benefits**:
  - Screen readers can distinguish header rows from data rows
  - Helps users understand table structure and navigation
  - Provides context for data cells in the table body
* **CSS styling**:
  - Often styled differently from `<tbody>` for visual hierarchy
  - Can be made sticky for scrolling tables
  - Use `background-color`, `font-weight`, and `border` for visual distinction
* **Browser support**: Well-supported in all modern browsers
* **Common mistakes**:
  - Using `<td>` instead of `<th>` in `<thead>`
  - Placing `<thead>` after `<tbody>` in the HTML
  - Using multiple `<thead>` elements (only one allowed)
  - Forgetting `scope` attributes on `<th>` elements
  - Putting data rows in `<thead>` instead of `<tbody>`
* **Performance**: Fixed headers with scrolling bodies can improve performance for large datasets
* **Responsive considerations**:
  - May need to hide `<thead>` on mobile and use data attributes instead
  - Consider alternative layouts for very small screens
  - Ensure header text remains readable at all screen sizes
* **SEO benefits**: Proper table structure helps search engines understand data relationships

---
