# `<col>`

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

The `<col>` (table column) element defines a column within a column group (`<colgroup>`) and represents one or more columns in a table for applying common styling and properties. It serves as a structural hook to target specific columns with CSS styles without the need to add classes to individual cells, enabling efficient column-based styling across entire tables.

---

## Syntax and Variants

+ **Standard syntax**: `<col>` (void element)
+ **Void element**: No closing tag required
+ **Self-closing variants**:
  - HTML5: `<col>`
  - XHTML: `<col />` or `<col></col>`
+ **Column specifier**: Always used within `<colgroup>` or as direct child of `<table>`

---

## Attributes

+ **Core attributes**:
  - `span` (optional): Number of consecutive columns the element spans (positive integer, default: 1)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Deprecated attributes**:
  - `width` (use CSS `width` instead)
  - `align` (use CSS `text-align` instead)
  - `char`, `charoff` (obsolete alignment attributes)
  - `valign` (use CSS `vertical-align` instead)
  - `bgcolor` (use CSS `background-color` instead)

---

## Content Model

+ **Empty element**: Must not contain any content
+ **No children permitted**: Cannot contain text or other elements
+ **Void element category**: Defined as having no content model in HTML specification
+ **No fallback content**: Relies on parent `<colgroup>` for structural context

---

## Context

+ **Required parent**: Must be a direct child of `<colgroup>` element
+ **Sibling relationships**:
  - Multiple `<col>` elements can exist within one `<colgroup>`
  - Each `<col>` represents one or more consecutive columns
  - Order corresponds to left-to-right column order in table
+ **Column assignment**: 
  - Without `span`: Each `<col>` represents one column
  - With `span`: Represents specified number of consecutive columns

---

## Behavior and Semantics

+ **Default display**: Table-column element
+ **Default styling**:
  - `display: table-column`
  - No inherent visual styling
  - Serves as a structural hook for CSS
+ **Column mapping**:
  - First `<col>` applies to first table column
  - Subsequent `<col>` elements apply to following columns
  - `span` attribute extends influence to multiple columns
+ **Semantic meaning**:
  - Represents a column or column range in a table
  - Screen readers may use for column context
  - Provides structural organization for styling
+ **Accessibility**: Can help convey column purpose and relationships

---

## Examples

**Basic column styling:**
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

**Column with span attribute:**
```html
<table>
  <colgroup>
    <col span="2" style="background-color: #f0f8ff">
    <col style="background-color: #fff0f5">
  </colgroup>
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

**Column width control:**
```html
<table class="fixed-layout">
  <colgroup>
    <col style="width: 200px">
    <col style="width: 150px">
    <col style="width: 100px">
    <col style="width: 80px">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Description</th>
      <th scope="col">Category</th>
      <th scope="col">Status</th>
      <th scope="col">Priority</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Implement user authentication system</td>
      <td>Security</td>
      <td>In Progress</td>
      <td>High</td>
    </tr>
    <tr>
      <td>Update API documentation</td>
      <td>Documentation</td>
      <td>Pending</td>
      <td>Medium</td>
    </tr>
  </tbody>
</table>
```

**Column classes for maintainable styling:**
```html
<table class="financial-report">
  <colgroup>
    <col class="label-col">
    <col class="data-col positive">
    <col class="data-col positive">
    <col class="data-col negative">
    <col class="summary-col">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Metric</th>
      <th scope="col">Q1</th>
      <th scope="col">Q2</th>
      <th scope="col">Q3</th>
      <th scope="col">YTD</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Revenue</th>
      <td>$125,000</td>
      <td>$138,000</td>
      <td>$95,000</td>
      <td>$358,000</td>
    </tr>
    <tr>
      <th scope="row">Profit</th>
      <td>$36,000</td>
      <td>$46,000</td>
      <td>$15,000</td>
      <td>$97,000</td>
    </tr>
  </tbody>
</table>

<style>
.label-col {
  background-color: #f8f9fa;
  width: 200px;
  font-weight: bold;
}

.data-col.positive {
  background-color: #f0fff0;
}

.data-col.negative {
  background-color: #fff0f0;
}

.summary-col {
  background-color: #fff8e1;
  border-left: 2px solid #ffd54f;
}
</style>
```

**Accessible column with ARIA:**
```html
<table role="grid" aria-labelledby="schedule-title">
  <caption id="schedule-title">Weekly Class Schedule</caption>
  <colgroup>
    <col aria-label="Time slots" style="width: 100px">
    <col aria-label="Monday classes" style="background-color: #f0f8ff">
    <col aria-label="Tuesday classes" style="background-color: #fff8f0">
    <col aria-label="Wednesday classes" style="background-color: #f8fff0">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Time</th>
      <th scope="col">Monday</th>
      <th scope="col">Tuesday</th>
      <th scope="col">Wednesday</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">9:00 AM</th>
      <td>Mathematics</td>
      <td>Physics</td>
      <td>Chemistry</td>
    </tr>
  </tbody>
</table>
```

**Column for responsive hiding:**
```html
<table class="responsive-data">
  <colgroup>
    <col class="essential-col">
    <col class="optional-col">
    <col class="detail-col">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Product</th>
      <th scope="col">Price</th>
      <th scope="col">Specifications</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Wireless Headphones Pro</td>
      <td>$199.99</td>
      <td>Frequency: 20Hz-20kHz, Battery: 30h, Weight: 250g</td>
    </tr>
    <tr>
      <td>Smart Watch Series 5</td>
      <td>$299.99</td>
      <td>Display: 1.7" AMOLED, GPS: Built-in, Water: 50m</td>
    </tr>
  </tbody>
</table>

<style>
@media (max-width: 768px) {
  .detail-col {
    display: none;
  }
  
  .essential-col {
    width: 60%;
  }
  
  .optional-col {
    width: 40%;
  }
}

@media (max-width: 480px) {
  .optional-col {
    display: none;
  }
  
  .essential-col {
    width: 100%;
  }
}
</style>
```

**Column with hover effects:**
```html
<table class="interactive-columns">
  <colgroup>
    <col class="name-col">
    <col class="email-col">
    <col class="role-col">
    <col class="actions-col">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Email</th>
      <th scope="col">Role</th>
      <th scope="col">Actions</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John Smith</td>
      <td>john@example.com</td>
      <td>Administrator</td>
      <td>
        <button>Edit</button>
        <button>Delete</button>
      </td>
    </tr>
    <tr>
      <td>Sarah Johnson</td>
      <td>sarah@example.com</td>
      <td>User</td>
      <td>
        <button>Edit</button>
        <button>Delete</button>
      </td>
    </tr>
  </tbody>
</table>

<style>
.name-col:hover {
  background-color: #e3f2fd;
}

.email-col:hover {
  background-color: #f3e5f5;
}

.role-col:hover {
  background-color: #e8f5e8;
}

.actions-col:hover {
  background-color: #fff3e0;
}

.interactive-columns td {
  transition: background-color 0.2s ease;
}
</style>
```

**Column for print optimization:**
```html
<table class="print-friendly">
  <colgroup>
    <col class="print-col-1">
    <col class="print-col-2">
    <col class="print-col-3">
    <col class="print-col-4">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">ID</th>
      <th scope="col">Description</th>
      <th scope="col">Quantity</th>
      <th scope="col">Unit Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>ITEM-001</td>
      <td>Professional Web Development Services</td>
      <td>10</td>
      <td>$150.00</td>
    </tr>
    <tr>
      <td>ITEM-002</td>
      <td>Technical Consulting Hours</td>
      <td>5</td>
      <td>$200.00</td>
    </tr>
  </tbody>
</table>

<style>
@media print {
  .print-col-1 { width: 15%; }
  .print-col-2 { width: 50%; }
  .print-col-3 { width: 15%; }
  .print-col-4 { width: 20%; text-align: right; }
  
  .print-friendly {
    font-size: 11pt;
    font-family: "Times New Roman", serif;
  }
}
</style>
```

**Column with conditional formatting:**
```html
<table id="performance-table">
  <colgroup>
    <col class="metric-col">
    <col class="target-col">
    <col class="actual-col">
    <col class="performance-col">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">KPI</th>
      <th scope="col">Target</th>
      <th scope="col">Actual</th>
      <th scope="col">Performance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Customer Satisfaction</td>
      <td>90%</td>
      <td>87%</td>
      <td>96.7%</td>
    </tr>
    <tr>
      <td>Response Time</td>
      <td>24h</td>
      <td>22h</td>
      <td>109.1%</td>
    </tr>
    <tr>
      <td>Conversion Rate</td>
      <td>5%</td>
      <td>4.2%</td>
      <td>84.0%</td>
    </tr>
  </tbody>
</table>

<style>
.performance-col {
  background-color: #ffffff;
}

/* Style based on data - would typically use JavaScript */
#performance-table tr:nth-child(1) .performance-col {
  background-color: #fff3cd; /* Warning - near target */
}

#performance-table tr:nth-child(2) .performance-col {
  background-color: #d1edff; /* Good - above target */
}

#performance-table tr:nth-child(3) .performance-col {
  background-color: #f8d7da; /* Poor - below target */
}
</style>
```

**Column with JavaScript interaction:**
```html
<table id="sortable-table">
  <colgroup>
    <col id="name-col" class="sortable-col">
    <col id="date-col" class="sortable-col">
    <col id="amount-col" class="sortable-col">
    <col class="action-col">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Date</th>
      <th scope="col">Amount</th>
      <th scope="col">Actions</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Project Alpha</td>
      <td>2024-03-15</td>
      <td>$1,500.00</td>
      <td><button>View</button></td>
    </tr>
    <tr>
      <td>Project Beta</td>
      <td>2024-03-10</td>
      <td>$2,300.00</td>
      <td><button>View</button></td>
    </tr>
  </tbody>
</table>

<style>
.sortable-col {
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.sortable-col:hover {
  background-color: #e3f2fd;
}

.sortable-col.active {
  background-color: #bbdefb;
  font-weight: bold;
}

.action-col {
  width: 100px;
}
</style>

<script>
document.querySelectorAll('.sortable-col').forEach(col => {
  col.addEventListener('click', function() {
    const columnIndex = Array.from(this.parentNode.children).indexOf(this);
    
    // Remove active class from all columns
    document.querySelectorAll('.sortable-col').forEach(c => {
      c.classList.remove('active');
    });
    
    // Add active class to clicked column
    this.classList.add('active');
    
    // Sort table by this column
    sortTableByColumn(columnIndex);
  });
});

function sortTableByColumn(columnIndex) {
  // Implementation for sorting would go here
  console.log(`Sorting by column ${columnIndex}`);
}
</script>
```

---

## Notes

* **Styling limitations**: Only specific CSS properties apply to columns:
  - `width`, `min-width`, `max-width`
  - `background-color`, `background-image`
  - `border` (limited support)
  - `visibility: collapse` (hides entire column)
* **Column order**: `<col>` elements must appear in the same order as table columns
* **Accessibility considerations**:
  - Screen readers have varying support for column semantics
  - Use `aria-label` or `aria-describedby` for important column context
  - Ensure color contrast when using background colors
* **Browser support**: Well-supported but some CSS properties may have inconsistent behavior
* **Common mistakes**:
  - Using outside of `<colgroup>` (though technically allowed in HTML5)
  - Expecting vertical alignment or height properties to work
  - Forgetting that `span` counts include the current column
  - Mixing `<col>` with `span` attributes inconsistently
* **Performance benefits**: More efficient than styling individual cells in large tables
* **Responsive design**: Excellent for controlling column visibility and width at different breakpoints
* **Print media**: Very effective for optimizing table layout in printed documents
* **Progressive enhancement**: Columns without styling still render the table content normally

---
