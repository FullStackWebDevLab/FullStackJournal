# `<tr>`

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

The `<tr>` (table row) element defines a row of cells in a table. It serves as a container for table cells (`<td>`) and header cells (`<th>`), organizing data horizontally across the table structure. Each `<tr>` represents one complete set of related data points that form a logical unit within the tabular data.

---

## Syntax & Variants

+ **Standard syntax**: `<tr>...</tr>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps table cell elements
+ **No self-closing variant**: Must contain table cells
+ **Closing tag optional**: Technically optional in HTML but recommended

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **Commonly used**: `class`, `id` for styling and scripting
+ **Deprecated attributes**:
  - `align` (use CSS `text-align` instead)
  - `bgcolor` (use CSS `background-color` instead)
  - `valign` (use CSS `vertical-align` instead)

---

## Content Model

+ **Permitted content**:
  - Zero or more `<td>` elements (data cells)
  - Zero or more `<th>` elements (header cells)
  - Mix of `<td>` and `<th>` elements
+ **Required children**: At least one `<td>` or `<th>` for meaningful rows
+ **Cell restrictions**: Only table cell elements allowed as direct children
+ **No nested tables**: Cannot contain other `<table>` elements directly

---

## Context

+ **Required parent**: Must be a direct child of:
  - `<table>` (directly)
  - `<thead>`, `<tbody>`, or `<tfoot>` (within table sections)
+ **Sibling relationships**: Multiple `<tr>` elements form the table rows
+ **Order significance**: Row order typically reflects data relationships
+ **Section context**: Behavior may vary based on parent section (`thead`, `tbody`, `tfoot`)

---

## Behavior and Semantics

+ **Default display**: Table-row element
+ **Default styling**:
  - `display: table-row`
  - No inherent borders, colors, or spacing
  - Inherits table's border-collapse behavior
+ **Layout behavior**:
  - Creates horizontal alignment of cells
  - Cells within row share same height
  - Participates in table's automatic column width calculation
+ **Semantic meaning**:
  - Represents a row of related data in a table
  - Screen readers announce row context and cell relationships
  - Groups cells that belong to the same data record
+ **Accessibility**: Helps screen reader users understand data relationships within rows

---

## Examples

**Basic table row with data cells:**
```html
<table>
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
</table>
```

**Table row with mixed header and data cells:**
```html
<table>
  <tr>
    <th>Product</th>
    <th>Price</th>
    <th>In Stock</th>
  </tr>
  <tr>
    <td>Wireless Headphones</td>
    <td>$199.99</td>
    <td>Yes</td>
  </tr>
  <tr>
    <td>Smart Watch</td>
    <td>$299.99</td>
    <td>No</td>
  </tr>
</table>
```

**Styled table rows with classes:**
```html
<table class="financial-data">
  <tr class="header-row">
    <th>Quarter</th>
    <th>Revenue</th>
    <th>Expenses</th>
    <th>Profit</th>
  </tr>
  <tr class="data-row highlighted">
    <td>Q1 2024</td>
    <td>$125,000</td>
    <td>$89,000</td>
    <td>$36,000</td>
  </tr>
  <tr class="data-row">
    <td>Q2 2024</td>
    <td>$138,000</td>
    <td>$92,000</td>
    <td>$46,000</td>
  </tr>
  <tr class="total-row">
    <td>Total</td>
    <td>$263,000</td>
    <td>$181,000</td>
    <td>$82,000</td>
  </tr>
</table>
```

**Table rows within table sections:**
```html
<table>
  <caption>Employee Schedule</caption>
  <thead>
    <tr>
      <th scope="col">Employee</th>
      <th scope="col">Monday</th>
      <th scope="col">Tuesday</th>
      <th scope="col">Wednesday</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">John Smith</th>
      <td>9:00-17:00</td>
      <td>8:00-16:00</td>
      <td>10:00-18:00</td>
    </tr>
    <tr>
      <th scope="row">Sarah Johnson</th>
      <td>8:00-16:00</td>
      <td>9:00-17:00</td>
      <td>8:00-16:00</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="4">Schedule subject to change</td>
    </tr>
  </tfoot>
</table>
```

**Interactive table rows with JavaScript:**
```html
<table id="user-table">
  <thead>
    <tr>
      <th>Name</th>
      <th>Email</th>
      <th>Status</th>
      <th>Actions</th>
    </tr>
  </thead>
  <tbody>
    <tr data-user-id="1" class="user-row">
      <td>John Smith</td>
      <td>john@example.com</td>
      <td class="status-active">Active</td>
      <td>
        <button class="edit-btn" onclick="editUser(1)">Edit</button>
        <button class="delete-btn" onclick="deleteUser(1)">Delete</button>
      </td>
    </tr>
    <tr data-user-id="2" class="user-row">
      <td>Sarah Johnson</td>
      <td>sarah@example.com</td>
      <td class="status-inactive">Inactive</td>
      <td>
        <button class="edit-btn" onclick="editUser(2)">Edit</button>
        <button class="delete-btn" onclick="deleteUser(2)">Delete</button>
      </td>
    </tr>
  </tbody>
</table>

<script>
function editUser(userId) {
  const row = document.querySelector(`[data-user-id="${userId}"]`);
  // Enable editing for this row
  row.classList.add('editing');
}

function deleteUser(userId) {
  const row = document.querySelector(`[data-user-id="${userId}"]`);
  row.remove();
}
</script>
```

**Table rows with rowspan and colspan:**
```html
<table class="complex-schedule">
  <tr>
    <th>Time</th>
    <th>Monday</th>
    <th>Tuesday</th>
    <th>Wednesday</th>
  </tr>
  <tr>
    <td>9:00-10:30</td>
    <td rowspan="2">Mathematics</td>
    <td>Physics</td>
    <td rowspan="2">Mathematics</td>
  </tr>
  <tr>
    <td>10:45-12:15</td>
    <td>English</td>
  </tr>
  <tr>
    <td>13:00-14:30</td>
    <td colspan="3" style="text-align: center;">Lunch Break</td>
  </tr>
</table>
```

**Accessible table rows with ARIA:**
```html
<table role="grid" aria-labelledby="projects-title">
  <caption id="projects-title">Current Projects Status</caption>
  <thead>
    <tr role="row">
      <th role="columnheader" scope="col">Project</th>
      <th role="columnheader" scope="col">Deadline</th>
      <th role="columnheader" scope="col">Status</th>
      <th role="columnheader" scope="col">Team Lead</th>
    </tr>
  </thead>
  <tbody>
    <tr role="row" aria-selected="false">
      <td role="gridcell">Website Redesign</td>
      <td role="gridcell">2024-06-15</td>
      <td role="gridcell">
        <span aria-label="In progress" class="status-in-progress">⟳</span>
      </td>
      <td role="gridcell">John Smith</td>
    </tr>
    <tr role="row" aria-selected="true">
      <td role="gridcell">Mobile App Launch</td>
      <td role="gridcell">2024-05-30</td>
      <td role="gridcell">
        <span aria-label="Completed" class="status-completed">✓</span>
      </td>
      <td role="gridcell">Sarah Johnson</td>
    </tr>
  </tbody>
</table>
```

**Table rows with complex cell content:**
```html
<table class="product-comparison">
  <tr class="feature-header">
    <th>Feature</th>
    <th>Basic Plan</th>
    <th>Pro Plan</th>
    <th>Enterprise Plan</th>
  </tr>
  <tr class="feature-row">
    <td class="feature-name">Storage Space</td>
    <td class="basic-feature">
      <span class="storage-amount">10 GB</span>
      <span class="feature-desc">Basic storage for essential files</span>
    </td>
    <td class="pro-feature">
      <span class="storage-amount">100 GB</span>
      <span class="feature-desc">Ample space for growing businesses</span>
    </td>
    <td class="enterprise-feature">
      <span class="storage-amount">1 TB</span>
      <span class="feature-desc">Unlimited storage with advanced management</span>
    </td>
  </tr>
  <tr class="feature-row">
    <td class="feature-name">User Accounts</td>
    <td class="basic-feature">
      <span class="user-count">1 user</span>
    </td>
    <td class="pro-feature">
      <span class="user-count">5 users</span>
      <span class="feature-desc">Perfect for small teams</span>
    </td>
    <td class="enterprise-feature">
      <span class="user-count">Unlimited users</span>
      <span class="feature-desc">Scale with your organization</span>
    </td>
  </tr>
</table>
```

**Responsive table row design:**
```html
<table class="responsive-data">
  <thead>
    <tr>
      <th>Product</th>
      <th>Category</th>
      <th>Price</th>
      <th>Rating</th>
      <th>Actions</th>
    </tr>
  </thead>
  <tbody>
    <tr data-product-id="101">
      <td data-label="Product">
        <div class="product-info">
          <img src="headphones.jpg" alt="Wireless Headphones" class="product-image">
          <div class="product-details">
            <strong>Wireless Headphones Pro</strong>
            <span class="sku">SKU: WHP-2024</span>
          </div>
        </div>
      </td>
      <td data-label="Category">Audio</td>
      <td data-label="Price">$199.99</td>
      <td data-label="Rating">
        <span class="stars">★★★★☆</span>
        <span class="rating-text">4.2/5</span>
      </td>
      <td data-label="Actions">
        <button class="btn-primary">Add to Cart</button>
        <button class="btn-secondary">Save</button>
      </td>
    </tr>
  </tbody>
</table>

<style>
@media (max-width: 768px) {
  .responsive-data tr {
    display: block;
    border: 1px solid #ddd;
    margin-bottom: 1rem;
  }
  
  .responsive-data td {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid #eee;
  }
  
  .responsive-data td::before {
    content: attr(data-label);
    font-weight: bold;
    margin-right: 1rem;
  }
}
</style>
```

---

## Notes

* **Semantic role**: Represents a complete set of related data points in tabular form
* **Cell consistency**: All rows should typically have the same number of cells (accounting for rowspan/colspan)
* **Accessibility considerations**:
  - Ensure proper header-cell relationships with `scope` attributes
  - Maintain consistent row structure for predictable navigation
  - Use ARIA roles carefully as native semantics are usually sufficient
* **CSS styling**:
  - Style with `background-color`, `border`, and hover effects
  - Use `:nth-child()` selectors for zebra striping
  - Consider `vertical-align` for cell content alignment
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using for layout purposes instead of tabular data
  - Mixing different numbers of cells across rows inconsistently
  - Forgetting to include required `<td>` or `<th>` elements
  - Overusing complex rowspan/colspan making tables difficult to maintain
* **JavaScript interaction**: Commonly used as event targets for row-level actions
* **Performance**: Large numbers of rows can impact rendering performance; consider virtualization
* **Print considerations**: Rows may break across pages; use CSS `page-break-inside: avoid` for important rows

---
