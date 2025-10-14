# `<td>`

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

The `<td>` (table data) element defines a standard data cell in an HTML table. It represents a single data point within a table row, containing the actual content or values that make up the tabular data. Each `<td>` cell holds one piece of information that relates to the corresponding header cells in the same column and row.

---

## Syntax and Variants

+ **Standard syntax**: `<td>...</td>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain various content types
+ **No self-closing variant**: Must contain content or be empty
+ **Closing tag optional**: Technically optional in HTML but recommended

---

## Attributes

+ **Core attributes**:
  - `colspan` (optional): Number of columns the cell spans (positive integer)
  - `rowspan` (optional): Number of rows the cell spans (positive integer)
  - `headers` (optional): Space-separated list of header cell IDs

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Deprecated attributes**:
  - `align` (use CSS `text-align` instead)
  - `bgcolor` (use CSS `background-color` instead)
  - `height` (use CSS `height` instead)
  - `width` (use CSS `width` instead)
  - `valign` (use CSS `vertical-align` instead)
  - `nowrap` (use CSS `white-space: nowrap` instead)

---

## Content Model

+ **Permitted content**: Flow content
+ **Allowed content**:
  - Text and phrasing content
  - Paragraphs, headings, lists, and other block elements
  - Images, videos, and other embedded content
  - Interactive elements and form controls
  - Other tables (nested tables)
+ **Rich content support**: Can contain complex HTML structures
+ **Empty cells**: Valid to have empty `<td>` elements for spacing

---

## Context

+ **Required parent**: Must be a direct child of `<tr>` element
+ **Sibling relationships**: 
  - Multiple `<td>` elements form the data cells in a row
  - Can be mixed with `<th>` elements in the same row
+ **Column alignment**: Cells in the same column typically contain related data
+ **Table context**: Always exists within a table structure

---

## Behavior and Semantics

+ **Default display**: Table-cell element
+ **Default styling**:
  - `display: table-cell`
  - `padding: 1px` (varies by browser)
  - Inherits table's border and spacing properties
  - Text aligns left, vertically middle
+ **Layout behavior**:
  - Participates in table's automatic column width calculation
  - Respects colspan and rowspan for cell merging
  - Aligns vertically with other cells in the same row
+ **Semantic meaning**:
  - Represents a data point in tabular data
  - Screen readers associate with corresponding header cells
  - Identifies as data (not header) content
+ **Accessibility**: Screen readers read cell content in context of associated headers

---

## Examples

**Basic data cells in a table:**
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

**Data cells with colspan and rowspan:**
```html
<table>
  <tr>
    <td colspan="2">Merged Header</td>
    <td>Regular Cell</td>
  </tr>
  <tr>
    <td rowspan="2">Merged Vertical</td>
    <td>Data A</td>
    <td>Data B</td>
  </tr>
  <tr>
    <td>Data C</td>
    <td>Data D</td>
  </tr>
</table>
```

**Styled data cells with classes:**
```html
<table class="financial-table">
  <tr>
    <td class="amount positive">$1,250.00</td>
    <td class="amount negative">-$450.00</td>
    <td class="amount neutral">$800.00</td>
  </tr>
  <tr>
    <td class="highlighted">Quarter 1 Total</td>
    <td class="percentage">15%</td>
    <td class="status completed">Completed</td>
  </tr>
</table>

<style>
.amount { text-align: right; font-family: monospace; }
.positive { color: green; }
.negative { color: red; }
.highlighted { background-color: #ffffcc; font-weight: bold; }
.completed { color: #006600; }
</style>
```

**Data cells with rich content:**
```html
<table>
  <tr>
    <td>
      <strong>Project Alpha</strong>
      <p class="project-description">Website redesign with modern framework</p>
      <span class="deadline">Due: 2024-06-15</span>
    </td>
    <td>
      <div class="progress-bar">
        <div class="progress" style="width: 75%"></div>
      </div>
      <span class="progress-text">75% Complete</span>
    </td>
    <td>
      <button class="btn-edit">Edit</button>
      <button class="btn-delete">Delete</button>
    </td>
  </tr>
</table>
```

**Accessible data cells with header associations:**
```html
<table>
  <thead>
    <tr>
      <th id="name">Name</th>
      <th id="department">Department</th>
      <th id="salary">Salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td headers="name">John Smith</td>
      <td headers="department">Engineering</td>
      <td headers="salary">$85,000</td>
    </tr>
    <tr>
      <td headers="name">Sarah Johnson</td>
      <td headers="department">Marketing</td>
      <td headers="salary">$72,000</td>
    </tr>
  </tbody>
</table>
```

**Interactive data cells with JavaScript:**
```html
<table id="editable-table">
  <tr>
    <td contenteditable="true" data-field="firstName">John</td>
    <td contenteditable="true" data-field="lastName">Smith</td>
    <td contenteditable="true" data-field="email">john@example.com</td>
    <td>
      <button onclick="saveRow(this)">Save</button>
      <button onclick="cancelEdit(this)">Cancel</button>
    </td>
  </tr>
</table>

<script>
function saveRow(button) {
  const row = button.closest('tr');
  const data = {};
  
  row.querySelectorAll('[contenteditable]').forEach(cell => {
    data[cell.dataset.field] = cell.textContent;
  });
  
  console.log('Saving:', data);
  // Send data to server
}
</script>
```

**Data cells with form elements:**
```html
<table class="order-form">
  <tr>
    <td>
      <input type="text" name="product[]" placeholder="Product name" required>
    </td>
    <td>
      <input type="number" name="quantity[]" min="1" value="1" required>
    </td>
    <td>
      <input type="number" name="price[]" step="0.01" placeholder="0.00" required>
    </td>
    <td>
      <button type="button" onclick="addRow(this)">Add Row</button>
    </td>
  </tr>
</table>
```

**Complex data cells with nested tables:**
```html
<table class="nested-data">
  <tr>
    <td>
      <strong>Quarter 1 Results</strong>
      <table class="sub-table">
        <tr>
          <td>Revenue</td>
          <td>$125,000</td>
        </tr>
        <tr>
          <td>Expenses</td>
          <td>$89,000</td>
        </tr>
        <tr>
          <td>Profit</td>
          <td>$36,000</td>
        </tr>
      </table>
    </td>
    <td>
      <div class="chart-container">
        <canvas id="q1-chart" width="200" height="100"></canvas>
      </div>
    </td>
  </tr>
</table>
```

**Data cells with responsive design:**
```html
<table class="responsive-table">
  <tr>
    <td data-label="Product Name">
      <div class="product-cell">
        <img src="product.jpg" alt="Product image" class="product-image">
        <div class="product-info">
          <h4>Wireless Headphones Pro</h4>
          <span class="sku">SKU: WHP-2024</span>
        </div>
      </div>
    </td>
    <td data-label="Price">$199.99</td>
    <td data-label="Stock">
      <span class="stock-badge in-stock">In Stock</span>
    </td>
    <td data-label="Actions">
      <button class="btn-small">Add to Cart</button>
    </td>
  </tr>
</table>

<style>
@media (max-width: 768px) {
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
  
  .product-cell {
    display: flex;
    align-items: center;
    gap: 1rem;
  }
}
</style>
```

**Data cells with validation states:**
```html
<table class="validation-table">
  <tr>
    <td class="valid">
      <input type="email" value="user@example.com" required>
      <span class="validation-icon">✓</span>
    </td>
    <td class="invalid">
      <input type="email" value="invalid-email" required>
      <span class="validation-icon">✗</span>
      <span class="error-message">Invalid email format</span>
    </td>
    <td class="warning">
      <input type="text" value="Short" minlength="5">
      <span class="validation-icon">⚠</span>
      <span class="warning-message">Minimum 5 characters</span>
    </td>
  </tr>
</table>

<style>
.valid { background-color: #f0fff0; }
.invalid { background-color: #fff0f0; }
.warning { background-color: #fffaf0; }
.validation-icon { margin-left: 0.5rem; font-weight: bold; }
</style>
```

---

## Notes

* **Semantic role**: Represents actual data content, not header information
* **Accessibility considerations**:
  - Use `headers` attribute to associate with relevant `<th>` elements
  - Ensure proper reading order and logical structure
  - Provide text alternatives for non-text content
  - Maintain consistent data types within columns
* **CSS styling**:
  - Use `padding` for internal spacing
  - Apply `border` for cell outlines
  - Use `text-align` and `vertical-align` for content positioning
  - Consider `white-space` properties for text wrapping
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using for layout purposes instead of tabular data
  - Missing proper header associations for accessibility
  - Overusing complex content when simple text would suffice
  - Inconsistent cell structure across rows
  - Forgetting to handle empty cells appropriately
* **Performance**: Complex content in many cells can impact rendering performance
* **Responsive design**: 
  - Consider stacking approaches for mobile devices
  - Use data attributes for mobile labels
  - Hide less important columns on small screens
* **Print considerations**: Ensure tables break appropriately across pages
* **SEO benefits**: Proper table structure helps search engines understand data relationships

---
