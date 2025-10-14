# `<colgroup>`

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

The `<colgroup>` (column group) element defines a group of columns within a table for applying common styling and semantic properties. It serves as a container for `<col>` elements, allowing developers to target specific columns or column ranges with CSS styles, attributes, and structural definitions without repeating styles across multiple cells.

---

## Syntax and Variants

+ **Standard syntax**: `<colgroup>...</colgroup>`
+ **Container element**: Can contain `<col>` elements or be self-contained with `span` attribute
+ **Two usage forms**:
  - With child `<col>` elements: `<colgroup><col>...</colgroup>`
  - With `span` attribute: `<colgroup span="3">` (no children needed)
+ **No self-closing variant**: Must be properly structured

---

## Attributes

+ **Core attributes**:
  - `span` (optional): Number of consecutive columns the group spans (positive integer)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Deprecated attributes**:
  - `width` (use CSS `width` instead)
  - `align` (use CSS `text-align` instead)
  - `char`, `charoff` (obsolete alignment attributes)
  - `valign` (use CSS `vertical-align` instead)

---

## Content Model

+ **Permitted content**:
  - If `span` attribute is absent: Zero or more `<col>` elements
  - If `span` attribute is present: No content allowed (empty content model)
+ **Mixed usage**: Cannot mix `span` attribute with `<col>` child elements
+ **Column definition**: Each `<col>` or `span` value represents one or more table columns

---

## Context

+ **Required parent**: Must be a direct child of `<table>` element
+ **Position requirements**:
  - Must appear after optional `<caption>` element
  - Must appear before `<thead>`, `<tbody>`, `<tfoot>`, or `<tr>` elements
  - Multiple `<colgroup>` elements allowed
+ **Sibling relationships**:
  - Can have multiple `<colgroup>` elements for different column groups
  - Each `<colgroup>` applies to consecutive columns in table order

---

## Behavior and Semantics

+ **Default display**: Table-column-group element
+ **Default styling**:
  - `display: table-column-group`
  - No inherent visual styling
  - Serves as a structural hook for CSS styling
+ **Column assignment**:
  - Columns are assigned to groups in left-to-right order
  - Each group covers consecutive columns based on `span` or number of `<col>` children
  - Styles apply to all cells in assigned columns
+ **Semantic meaning**:
  - Groups columns for common styling and properties
  - Screen readers may use for column context
  - Provides structural organization for table columns
+ **Accessibility**: Can help convey column relationships and groupings

---

## Examples

**Basic colgroup for column styling:**
```html
<table>
  <colgroup>
    <col style="background-color: #f8f9fa">
    <col style="background-color: #e9ecef">
    <col style="background-color: #f8f9fa">
  </colgroup>
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
  </tbody>
</table>
```

**Colgroup with span attribute:**
```html
<table>
  <colgroup span="2" style="background-color: #f0f8ff"></colgroup>
  <colgroup span="1" style="background-color: #fff0f5"></colgroup>
  <thead>
    <tr>
      <th scope="col">First Name</th>
      <th scope="col">Last Name</th>
      <th scope="col">Salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John</td>
      <td>Smith</td>
      <td>$85,000</td>
    </tr>
  </tbody>
</table>
```

**Mixed colgroup with classes:**
```html
<table class="financial-table">
  <colgroup class="label-columns">
    <col class="category-col">
    <col class="metric-col">
  </colgroup>
  <colgroup class="data-columns" span="4">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Category</th>
      <th scope="col">Metric</th>
      <th scope="col">Q1</th>
      <th scope="col">Q2</th>
      <th scope="col">Q3</th>
      <th scope="col">Q4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row" rowspan="2">Financial</th>
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
</table>

<style>
.label-columns {
  background-color: #f8f9fa;
  width: 200px;
}

.data-columns {
  background-color: #ffffff;
}

.category-col {
  border-right: 2px solid #dee2e6;
}

.metric-col {
  font-style: italic;
}
</style>
```

**Complex table with multiple colgroups:**
```html
<table>
  <caption>Sales Performance by Region and Product</caption>
  <colgroup class="header-col"></colgroup>
  <colgroup class="q1-data" span="3"></colgroup>
  <colgroup class="q2-data" span="3"></colgroup>
  <colgroup class="summary-col"></colgroup>
  <thead>
    <tr>
      <th scope="col">Product</th>
      <th scope="colgroup" colspan="3">Q1 2024</th>
      <th scope="colgroup" colspan="3">Q2 2024</th>
      <th scope="col">YTD Total</th>
    </tr>
    <tr>
      <th scope="col"></th>
      <th scope="col">North</th>
      <th scope="col">South</th>
      <th scope="col">West</th>
      <th scope="col">North</th>
      <th scope="col">South</th>
      <th scope="col">West</th>
      <th scope="col">Total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Product A</th>
      <td>45</td>
      <td>38</td>
      <td>52</td>
      <td>48</td>
      <td>42</td>
      <td>58</td>
      <td>283</td>
    </tr>
  </tbody>
</table>

<style>
.header-col {
  background-color: #2c3e50;
  color: white;
}

.q1-data {
  background-color: #e8f4f8;
}

.q2-data {
  background-color: #f0f8e8;
}

.summary-col {
  background-color: #fff8e1;
  border-left: 2px solid #ffd54f;
}
</style>
```

**Colgroup for column width control:**
```html
<table class="fixed-width-table">
  <colgroup>
    <col style="width: 150px">
    <col style="width: 100px">
    <col style="width: 200px">
    <col style="width: 80px">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Description</th>
      <th scope="col">Category</th>
      <th scope="col">Notes</th>
      <th scope="col">Priority</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Implement user authentication</td>
      <td>Security</td>
      <td>Requires OAuth2 integration</td>
      <td>High</td>
    </tr>
    <tr>
      <td>Update documentation</td>
      <td>Documentation</td>
      <td>Add new API endpoints</td>
      <td>Medium</td>
    </tr>
  </tbody>
</table>
```

**Accessible colgroup with ARIA:**
```html
<table role="grid" aria-labelledby="budget-title">
  <caption id="budget-title">Department Budget Allocation</caption>
  <colgroup role="columnheader" aria-label="Department information">
    <col style="background-color: #f0f0f0">
  </colgroup>
  <colgroup role="columnheader" aria-label="Quarterly allocations" span="4">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Department</th>
      <th scope="col">Q1</th>
      <th scope="col">Q2</th>
      <th scope="col">Q3</th>
      <th scope="col">Q4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Engineering</th>
      <td>$200,000</td>
      <td>$220,000</td>
      <td>$240,000</td>
      <td>$260,000</td>
    </tr>
  </tbody>
</table>
```

**Colgroup for zebra striping columns:**
```html
<table class="zebra-columns">
  <colgroup>
    <col class="zebra-1">
    <col class="zebra-2">
    <col class="zebra-1">
    <col class="zebra-2">
    <col class="zebra-1">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Monday</th>
      <th scope="col">Tuesday</th>
      <th scope="col">Wednesday</th>
      <th scope="col">Thursday</th>
      <th scope="col">Friday</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>9:00 AM</td>
      <td>10:30 AM</td>
      <td>Team Meeting</td>
      <td>Project Review</td>
      <td>Code Review</td>
    </tr>
    <tr>
      <td>2:00 PM</td>
      <td>1:00 PM</td>
      <td>Client Call</td>
      <td>Training</td>
      <td>Sprint Planning</td>
    </tr>
  </tbody>
</table>

<style>
.zebra-1 {
  background-color: #ffffff;
}

.zebra-2 {
  background-color: #f8f9fa;
}

.zebra-columns tr:hover td {
  background-color: #e3f2fd;
}
</style>
```

**Colgroup with responsive design:**
```html
<table class="responsive-cols">
  <colgroup class="mobile-priority">
    <col class="essential-col">
    <col class="optional-col">
    <col class="hidden-mobile-col">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Product Name</th>
      <th scope="col">Price</th>
      <th scope="col">Technical Specs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Wireless Headphones Pro</td>
      <td>$199.99</td>
      <td>Frequency: 20Hz-20kHz, Battery: 30h</td>
    </tr>
    <tr>
      <td>Smart Watch Series 5</td>
      <td>$299.99</td>
      <td>Display: 1.7" AMOLED, GPS: Built-in</td>
    </tr>
  </tbody>
</table>

<style>
@media (max-width: 768px) {
  .hidden-mobile-col {
    display: none;
  }
  
  .essential-col {
    width: 60%;
  }
  
  .optional-col {
    width: 40%;
  }
}
</style>
```

**Colgroup for print styling:**
```html
<table class="print-optimized">
  <colgroup class="print-colgroup">
    <col class="print-col-1">
    <col class="print-col-2">
    <col class="print-col-3">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Invoice #</th>
      <th scope="col">Description</th>
      <th scope="col">Amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>INV-001</td>
      <td>Web Development Services</td>
      <td>$2,500.00</td>
    </tr>
    <tr>
      <td>INV-002</td>
      <td>Consulting Hours</td>
      <td>$1,200.00</td>
    </tr>
  </tbody>
</table>

<style>
@media print {
  .print-col-1 {
    width: 20%;
  }
  
  .print-col-2 {
    width: 60%;
  }
  
  .print-col-3 {
    width: 20%;
    text-align: right;
  }
  
  .print-optimized {
    font-size: 12pt;
  }
}
</style>
```

**Colgroup with JavaScript interaction:**
```html
<table id="interactive-table">
  <colgroup id="col-group-1">
    <col data-column="name" class="editable-col">
    <col data-column="email" class="editable-col">
    <col data-column="role" class="fixed-col">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Email</th>
      <th scope="col">Role</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td contenteditable="true">John Smith</td>
      <td contenteditable="true">john@example.com</td>
      <td>Administrator</td>
    </tr>
    <tr>
      <td contenteditable="true">Sarah Johnson</td>
      <td contenteditable="true">sarah@example.com</td>
      <td>User</td>
    </tr>
  </tbody>
</table>

<style>
.editable-col {
  background-color: #f0fff0;
  border: 1px dashed #ccc;
}

.fixed-col {
  background-color: #fff0f0;
}

.editable-col:focus {
  background-color: #e0ffe0;
  outline: 2px solid #4CAF50;
}
</style>

<script>
// Add click handlers to make entire columns editable
document.querySelectorAll('.editable-col').forEach(col => {
  col.addEventListener('click', function() {
    const columnIndex = Array.from(this.parentNode.children).indexOf(this);
    const rows = document.querySelectorAll('#interactive-table tbody tr');
    
    rows.forEach(row => {
      const cell = row.children[columnIndex];
      cell.setAttribute('contenteditable', 'true');
      cell.focus();
    });
  });
});
</script>
```

---

## Notes

* **Styling limitations**: Only a subset of CSS properties apply to columns (width, background, border, visibility)
* **Column assignment**: Columns are assigned in source order, left to right
* **Accessibility considerations**:
  - Screen readers have varying support for column group semantics
  - Use ARIA attributes for complex column relationships
  - Ensure color contrast and readability when using background colors
* **CSS properties that work**:
  - `width`, `min-width`, `max-width`
  - `background-color`, `background-image`
  - `border`, `visibility`
  - `display: none` (hides entire column)
* **Browser support**: Well-supported but some older browsers may have limitations
* **Common mistakes**:
  - Mixing `span` attribute with `<col>` child elements
  - Placing after `<thead>` or `<tbody>` elements
  - Expecting all CSS properties to work on columns
  - Forgetting that columns don't have height or vertical alignment properties
* **Performance**: More efficient than styling individual cells for large tables
* **Responsive design**: Useful for hiding or resizing columns at different breakpoints
* **Print optimization**: Excellent for controlling column widths and visibility in print media

---
