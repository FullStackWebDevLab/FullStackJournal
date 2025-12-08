# `<tbody>`

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

The `<tbody>` (table body) element groups one or more rows that contain the primary data content of an HTML table. It represents the main body of tabular data, separating the data rows from header rows (`<thead>`) and footer rows (`<tfoot>`), providing semantic structure and enabling independent styling and scripting of the table's core content.

---

## Syntax and Variants

+ **Standard syntax**: `<tbody>...</tbody>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps one or more `<tr>` elements containing `<td>` and `<th>` cells
+ **No self-closing variant**: Must contain table rows
+ **Table section**: Part of table's structural grouping with `<thead>` and `<tfoot>`

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies on semantic role within table structure
+ **Commonly used**: `class`, `id` for styling and scripting

---

## Content Model

+ **Permitted content**: Zero or more `<tr>` elements
+ **Required children**: At least one `<tr>` for meaningful data content
+ **Row restrictions**: Only `<tr>` elements allowed as direct children
+ **Mixed cells**: `<tr>` elements typically contain `<td>` data cells and optionally `<th>` row headers

---

## Context

+ **Required parent**: Must be a direct child of `<table>` element
+ **Position requirements**:
  - Must appear after `<caption>`, `<colgroup>`, and `<thead>` if present
  - Can appear before or after `<tfoot>` (but `<tfoot>` renders after `<tbody>`)
  - Multiple `<tbody>` elements allowed for grouping related data
+ **Sibling relationships**:
  - Optional `<thead>` and `<tfoot>` elements
  - Multiple `<tbody>` elements can be used for data grouping

---

## Behavior and Semantics

+ **Default display**: Table-row-group element
+ **Default styling**:
  - `display: table-row-group`
  - No inherent visual styling differences from regular rows
  - Inherits table's border and spacing properties
+ **Functional behavior**:
  - Contains the primary data content of the table
  - Can be styled independently from `<thead>` and `<tfoot>`
  - Supports scrolling independently in some implementations
+ **Semantic meaning**:
  - Represents the main data section of a table
  - Screen readers announce as table body section
  - Groups data rows for better accessibility and styling
+ **Accessibility**: Helps screen reader users distinguish between header and data content

---

## Examples

**Basic table with tbody:**
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

**Multiple tbody elements for data grouping:**
```html
<table>
  <thead>
    <tr>
      <th scope="col">Product</th>
      <th scope="col">Category</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody class="audio-products">
    <tr>
      <td>Wireless Headphones</td>
      <td>Audio</td>
      <td>$199.99</td>
    </tr>
    <tr>
      <td>Bluetooth Speaker</td>
      <td>Audio</td>
      <td>$89.99</td>
    </tr>
  </tbody>
  <tbody class="tech-products">
    <tr>
      <td>Smart Watch</td>
      <td>Wearables</td>
      <td>$299.99</td>
    </tr>
    <tr>
      <td>Tablet</td>
      <td>Computing</td>
      <td>$499.99</td>
    </tr>
  </tbody>
</table>
```

**Styled tbody with zebra striping:**
```html
<table class="styled-table">
  <thead>
    <tr>
      <th scope="col">Employee ID</th>
      <th scope="col">Name</th>
      <th scope="col">Position</th>
      <th scope="col">Salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>EMP001</td>
      <td>John Smith</td>
      <td>Senior Developer</td>
      <td>$95,000</td>
    </tr>
    <tr>
      <td>EMP002</td>
      <td>Sarah Johnson</td>
      <td>Marketing Manager</td>
      <td>$85,000</td>
    </tr>
    <tr>
      <td>EMP003</td>
      <td>Mike Chen</td>
      <td>Product Designer</td>
      <td>$90,000</td>
    </tr>
  </tbody>
</table>

<style>
.styled-table tbody tr:nth-child(odd) {
  background-color: #f8f9fa;
}

.styled-table tbody tr:nth-child(even) {
  background-color: #ffffff;
}

.styled-table tbody tr:hover {
  background-color: #e3f2fd;
}
</style>
```

**Tbody with row headers and complex data:**
```html
<table>
  <thead>
    <tr>
      <th scope="col">Metric</th>
      <th scope="col">Q1 2024</th>
      <th scope="col">Q2 2024</th>
      <th scope="col">Q3 2024</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Revenue</th>
      <td>$125,000</td>
      <td>$138,000</td>
      <td>$142,000</td>
    </tr>
    <tr>
      <th scope="row">Expenses</th>
      <td>$89,000</td>
      <td>$92,000</td>
      <td>$95,000</td>
    </tr>
    <tr>
      <th scope="row">Net Profit</th>
      <td>$36,000</td>
      <td>$46,000</td>
      <td>$47,000</td>
    </tr>
  </tbody>
</table>
```

**Interactive tbody with JavaScript:**
```html
<table id="user-table">
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Email</th>
      <th scope="col">Status</th>
      <th scope="col">Actions</th>
    </tr>
  </thead>
  <tbody id="user-data">
    <tr data-user-id="1">
      <td>John Smith</td>
      <td>john@example.com</td>
      <td class="status-active">Active</td>
      <td>
        <button onclick="editUser(1)">Edit</button>
        <button onclick="deleteUser(1)">Delete</button>
      </td>
    </tr>
    <tr data-user-id="2">
      <td>Sarah Johnson</td>
      <td>sarah@example.com</td>
      <td class="status-inactive">Inactive</td>
      <td>
        <button onclick="editUser(2)">Edit</button>
        <button onclick="deleteUser(2)">Delete</button>
      </td>
    </tr>
  </tbody>
</table>

<script>
function deleteUser(userId) {
  const row = document.querySelector(`[data-user-id="${userId}"]`);
  if (confirm('Are you sure you want to delete this user?')) {
    row.remove();
  }
}

function addUser(name, email) {
  const tbody = document.getElementById('user-data');
  const newRow = document.createElement('tr');
  newRow.innerHTML = `
    <td>${name}</td>
    <td>${email}</td>
    <td class="status-active">Active</td>
    <td>
      <button onclick="editUser(${Date.now()})">Edit</button>
      <button onclick="deleteUser(${Date.now()})">Delete</button>
    </td>
  `;
  tbody.appendChild(newRow);
}
</script>
```

**Scrollable tbody with fixed header:**
```html
<div class="table-container">
  <table class="scrollable-table">
    <thead>
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
      <tr>
        <td>P002</td>
        <td>Smart Watch Series 5</td>
        <td>Wearables</td>
        <td>$299.99</td>
        <td>32</td>
      </tr>
      <!-- Many more rows -->
    </tbody>
  </table>
</div>

<style>
.table-container {
  height: 300px;
  border: 1px solid #ddd;
  overflow: hidden;
}

.scrollable-table {
  width: 100%;
  border-collapse: collapse;
}

.scrollable-table thead {
  background-color: #f8f9fa;
  position: sticky;
  top: 0;
}

.scrollable-body {
  display: block;
  height: 250px;
  overflow-y: auto;
}

.scrollable-table tbody tr {
  display: table;
  width: 100%;
  table-layout: fixed;
}
</style>
```

**Tbody with form elements and validation:**
```html
<table id="order-table">
  <thead>
    <tr>
      <th scope="col">Product</th>
      <th scope="col">Quantity</th>
      <th scope="col">Price</th>
      <th scope="col">Total</th>
      <th scope="col">Actions</th>
    </tr>
  </thead>
  <tbody>
    <tr class="order-row">
      <td>
        <select name="product[]" required>
          <option value="">Select Product</option>
          <option value="headphones">Wireless Headphones</option>
          <option value="speaker">Bluetooth Speaker</option>
        </select>
      </td>
      <td>
        <input type="number" name="quantity[]" min="1" value="1" required>
      </td>
      <td>
        <span class="price-display">$0.00</span>
      </td>
      <td>
        <span class="total-display">$0.00</span>
      </td>
      <td>
        <button type="button" onclick="removeRow(this)">Remove</button>
      </td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3"><strong>Grand Total</strong></td>
      <td><strong id="grand-total">$0.00</strong></td>
      <td>
        <button type="button" onclick="addRow()">Add Item</button>
      </td>
    </tr>
  </tfoot>
</table>
```

**Accessible tbody with ARIA attributes:**
```html
<table role="grid" aria-labelledby="projects-title">
  <caption id="projects-title">Current Projects</caption>
  <thead role="rowgroup">
    <tr role="row">
      <th role="columnheader" scope="col">Project Name</th>
      <th role="columnheader" scope="col">Deadline</th>
      <th role="columnheader" scope="col">Status</th>
      <th role="columnheader" scope="col">Team Lead</th>
    </tr>
  </thead>
  <tbody role="rowgroup">
    <tr role="row" aria-selected="false">
      <td role="gridcell">Website Redesign</td>
      <td role="gridcell">2024-06-15</td>
      <td role="gridcell">
        <span aria-label="In progress">⟳</span> In Progress
      </td>
      <td role="gridcell">John Smith</td>
    </tr>
    <tr role="row" aria-selected="true">
      <td role="gridcell">Mobile App Launch</td>
      <td role="gridcell">2024-05-30</td>
      <td role="gridcell">
        <span aria-label="Completed">✓</span> Completed
      </td>
      <td role="gridcell">Sarah Johnson</td>
    </tr>
  </tbody>
</table>
```

**Tbody with lazy loading for large datasets:**
```html
<table id="large-data-table">
  <thead>
    <tr>
      <th scope="col">ID</th>
      <th scope="col">Name</th>
      <th scope="col">Email</th>
      <th scope="col">Department</th>
    </tr>
  </thead>
  <tbody id="data-body">
    <!-- Initial rows loaded -->
    <tr>
      <td>1</td>
      <td>John Smith</td>
      <td>john@example.com</td>
      <td>Engineering</td>
    </tr>
    <!-- More rows will be loaded as user scrolls -->
  </tbody>
</table>

<script>
const tbody = document.getElementById('data-body');
let currentPage = 1;

function loadMoreData() {
  // Simulate API call
  fetch(`/api/users?page=${currentPage}`)
    .then(response => response.json())
    .then(users => {
      users.forEach(user => {
        const row = document.createElement('tr');
        row.innerHTML = `
          <td>${user.id}</td>
          <td>${user.name}</td>
          <td>${user.email}</td>
          <td>${user.department}</td>
        `;
        tbody.appendChild(row);
      });
      currentPage++;
    });
}

// Load more data when user scrolls near bottom
window.addEventListener('scroll', () => {
  if (window.innerHeight + window.scrollY >= document.body.offsetHeight - 500) {
    loadMoreData();
  }
});
</script>
```

---

## Notes

* **Semantic importance**: Provides structural meaning to table data beyond visual presentation
* **Multiple tbody usage**: Can use multiple `<tbody>` elements to group related data rows
* **Accessibility benefits**:
  - Screen readers can distinguish between header and data sections
  - Helps users navigate large tables more effectively
  - Provides context for data relationships
* **CSS styling**:
  - Can be styled independently from `<thead>` and `<tfoot>`
  - Commonly used with `:nth-child()` selectors for zebra striping
  - Supports hover effects and interactive states
* **Browser support**: Well-supported in all modern browsers
* **Common mistakes**:
  - Putting header rows (`<tr>` with `<th>`) in `<tbody>` instead of `<thead>`
  - Using `<tbody>` for layout purposes
  - Forgetting to include `<tbody>` when using `<thead>` or `<tfoot>`
  - Placing `<tbody>` before `<thead>` in the HTML
* **Performance considerations**:
  - Large `<tbody>` elements can impact rendering performance
  - Consider virtualization for very large datasets
  - Scrollable `<tbody>` can improve performance for long tables
* **JavaScript interaction**:
  - Commonly targeted for dynamic row manipulation
  - Event delegation can improve performance for interactive tables
  - Can be efficiently updated without affecting headers/footers
* **Print behavior**: `<tbody>` content flows naturally across printed pages
* **Responsive design**: May require alternative layouts on mobile devices

---
