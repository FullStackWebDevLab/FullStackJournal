# `<tfoot>`

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

The `<tfoot>` (table footer) element defines a block of footer rows in an HTML table. It groups one or more rows that contain summary information, totals, or concluding data for the table. Despite its name and position in HTML source, browsers render `<tfoot>` content after the table body, providing a semantic way to include summary rows that appear at the bottom of the table.

---

## Syntax and Variants

+ **Standard syntax**: `<tfoot>...</tfoot>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps one or more `<tr>` elements containing summary data
+ **No self-closing variant**: Must contain table rows
+ **Table section**: Part of table's structural grouping with `<thead>` and `<tbody>`

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies on semantic role within table structure
+ **Commonly used**: `class`, `id` for styling and scripting

---

## Content Model

+ **Permitted content**: Zero or more `<tr>` elements
+ **Required children**: At least one `<tr>` for meaningful footer content
+ **Row restrictions**: Only `<tr>` elements allowed as direct children
+ **Cell types**: Can contain `<td>` data cells or `<th>` header cells for footer labels

---

## Context

+ **Required parent**: Must be a direct child of `<table>` element
+ **Position requirements**:
  - Can appear after `<caption>` and `<colgroup>`
  - Can appear before or after `<tbody>` in HTML source
  - Always renders after `<tbody>` content visually
  - Only one `<tfoot>` allowed per table
+ **Sibling relationships**:
  - Optional `<thead>` and `<tbody>` elements
  - Multiple `<tbody>` elements can be used with one `<tfoot>`

---

## Behavior and Semantics

+ **Default display**: Table-footer-group element
+ **Default styling**:
  - `display: table-footer-group`
  - No inherent visual styling differences from regular rows
  - Inherits table's border and spacing properties
+ **Rendering behavior**:
  - Always appears at the bottom of the table, regardless of HTML source position
  - May repeat on each printed page for long tables (browser-dependent)
  - Provides semantic grouping for summary information
+ **Semantic meaning**:
  - Represents the footer section of a table
  - Screen readers announce as table footer section
  - Groups summary rows for better accessibility
+ **Accessibility**: Helps screen reader users identify summary and concluding information

---

## Examples

**Basic table with tfoot for totals:**
```html
<table>
  <thead>
    <tr>
      <th scope="col">Product</th>
      <th scope="col">Quantity</th>
      <th scope="col">Price</th>
      <th scope="col">Total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Wireless Headphones</td>
      <td>2</td>
      <td>$199.99</td>
      <td>$399.98</td>
    </tr>
    <tr>
      <td>Bluetooth Speaker</td>
      <td>1</td>
      <td>$89.99</td>
      <td>$89.99</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3"><strong>Grand Total</strong></td>
      <td><strong>$489.97</strong></td>
    </tr>
  </tfoot>
</table>
```

**Styled tfoot with summary information:**
```html
<table class="financial-table">
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
  <tfoot class="table-footer">
    <tr>
      <th scope="row">Net Profit</th>
      <td>$36,000</td>
      <td>$46,000</td>
      <td>$47,000</td>
      <td>$58,000</td>
    </tr>
    <tr>
      <th scope="row">Yearly Total</th>
      <td colspan="4">$187,000</td>
    </tr>
  </tfoot>
</table>

<style>
.financial-table .table-footer {
  background-color: #f8f9fa;
  border-top: 2px solid #dee2e6;
}

.financial-table .table-footer th {
  font-weight: 600;
  color: #2c3e50;
}
</style>
```

**Tfoot with multiple summary rows:**
```html
<table>
  <thead>
    <tr>
      <th scope="col">Department</th>
      <th scope="col">Budget</th>
      <th scope="col">Actual</th>
      <th scope="col">Variance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Engineering</td>
      <td>$500,000</td>
      <td>$485,000</td>
      <td>-$15,000</td>
    </tr>
    <tr>
      <td>Marketing</td>
      <td>$300,000</td>
      <td>$315,000</td>
      <td>+$15,000</td>
    </tr>
    <tr>
      <td>Sales</td>
      <td>$400,000</td>
      <td>$420,000</td>
      <td>+$20,000</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td><strong>Department Total</strong></td>
      <td><strong>$1,200,000</strong></td>
      <td><strong>$1,220,000</strong></td>
      <td><strong>+$20,000</strong></td>
    </tr>
    <tr>
      <td><em>Corporate Overhead</em></td>
      <td><em>$200,000</em></td>
      <td><em>$195,000</em></td>
      <td><em>-$5,000</em></td>
    </tr>
    <tr>
      <td><strong>Company Total</strong></td>
      <td><strong>$1,400,000</strong></td>
      <td><strong>$1,415,000</strong></td>
      <td><strong>+$15,000</strong></td>
    </tr>
  </tfoot>
</table>
```

**Tfoot with calculated values using JavaScript:**
```html
<table id="invoice-table">
  <thead>
    <tr>
      <th scope="col">Item</th>
      <th scope="col">Quantity</th>
      <th scope="col">Unit Price</th>
      <th scope="col">Total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Web Development</td>
      <td><input type="number" class="quantity" value="10" min="0"></td>
      <td>$150.00</td>
      <td class="item-total">$1,500.00</td>
    </tr>
    <tr>
      <td>Design Services</td>
      <td><input type="number" class="quantity" value="5" min="0"></td>
      <td>$100.00</td>
      <td class="item-total">$500.00</td>
    </tr>
  </tbody>
  <tfoot id="invoice-footer">
    <tr>
      <td colspan="3">Subtotal</td>
      <td id="subtotal">$2,000.00</td>
    </tr>
    <tr>
      <td colspan="3">Tax (8%)</td>
      <td id="tax">$160.00</td>
    </tr>
    <tr>
      <td colspan="3"><strong>Grand Total</strong></td>
      <td id="grand-total"><strong>$2,160.00</strong></td>
    </tr>
  </tfoot>
</table>

<script>
function calculateTotals() {
  const quantities = document.querySelectorAll('.quantity');
  const itemTotals = document.querySelectorAll('.item-total');
  let subtotal = 0;
  
  quantities.forEach((input, index) => {
    const quantity = parseInt(input.value) || 0;
    const unitPrice = 150; // This would normally come from data
    const total = quantity * unitPrice;
    itemTotals[index].textContent = `$${total.toFixed(2)}`;
    subtotal += total;
  });
  
  const tax = subtotal * 0.08;
  const grandTotal = subtotal + tax;
  
  document.getElementById('subtotal').textContent = `$${subtotal.toFixed(2)}`;
  document.getElementById('tax').textContent = `$${tax.toFixed(2)}`;
  document.getElementById('grand-total').textContent = `$${grandTotal.toFixed(2)}`;
}

document.querySelectorAll('.quantity').forEach(input => {
  input.addEventListener('input', calculateTotals);
});
</script>
```

**Accessible tfoot with ARIA attributes:**
```html
<table role="grid" aria-labelledby="sales-title">
  <caption id="sales-title">Monthly Sales Report</caption>
  <thead role="rowgroup">
    <tr role="row">
      <th role="columnheader" scope="col">Salesperson</th>
      <th role="columnheader" scope="col">Region</th>
      <th role="columnheader" scope="col">Sales</th>
      <th role="columnheader" scope="col">Commission</th>
    </tr>
  </thead>
  <tbody role="rowgroup">
    <tr role="row">
      <td role="gridcell">John Smith</td>
      <td role="gridcell">North America</td>
      <td role="gridcell">$45,000</td>
      <td role="gridcell">$4,500</td>
    </tr>
  </tbody>
  <tfoot role="rowgroup" aria-label="Summary information">
    <tr role="row">
      <td role="gridcell" colspan="2"><strong>Team Total</strong></td>
      <td role="gridcell"><strong>$45,000</strong></td>
      <td role="gridcell"><strong>$4,500</strong></td>
    </tr>
  </tfoot>
</table>
```

**Tfoot with responsive design:**
```html
<table class="responsive-table">
  <thead>
    <tr>
      <th scope="col">Product</th>
      <th scope="col">Category</th>
      <th scope="col">Price</th>
      <th scope="col">Sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td data-label="Product">Wireless Headphones</td>
      <td data-label="Category">Audio</td>
      <td data-label="Price">$199.99</td>
      <td data-label="Sales">150 units</td>
    </tr>
    <tr>
      <td data-label="Product">Smart Watch</td>
      <td data-label="Category">Wearables</td>
      <td data-label="Price">$299.99</td>
      <td data-label="Sales">89 units</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td data-label="Summary" colspan="2"><strong>Total Revenue</strong></td>
      <td data-label="Total Price" colspan="2"><strong>$59,998.11</strong></td>
    </tr>
  </tfoot>
</table>

<style>
@media (max-width: 768px) {
  .responsive-table tfoot tr {
    display: block;
    background-color: #f8f9fa;
    border-top: 2px solid #dee2e6;
  }
  
  .responsive-table tfoot td {
    display: block;
    text-align: center;
    padding: 1rem;
  }
}
</style>
```

**Tfoot in a complex table structure:**
```html
<table>
  <caption>Project Budget Allocation</caption>
  <colgroup>
    <col style="width: 30%">
    <col style="width: 20%">
    <col style="width: 20%">
    <col style="width: 30%">
  </colgroup>
  <thead>
    <tr>
      <th scope="col">Department</th>
      <th scope="col">Q1 Allocation</th>
      <th scope="col">Q2 Allocation</th>
      <th scope="col">Remaining Budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Engineering</th>
      <td>$200,000</td>
      <td>$250,000</td>
      <td>$50,000</td>
    </tr>
    <tr>
      <th scope="row">Marketing</th>
      <td>$100,000</td>
      <td>$120,000</td>
      <td>$30,000</td>
    </tr>
    <tr>
      <th scope="row">Operations</th>
      <td>$80,000</td>
      <td>$90,000</td>
      <td>$20,000</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row">Total Allocated</th>
      <td>$380,000</td>
      <td>$460,000</td>
      <td>$100,000</td>
    </tr>
    <tr>
      <th scope="row">Project Total</th>
      <td colspan="3">$940,000</td>
    </tr>
    <tr>
      <td colspan="4" style="text-align: center; font-style: italic;">
        Budget figures are subject to quarterly review and adjustment
      </td>
    </tr>
  </tfoot>
</table>
```

**Tfoot with conditional formatting:**
```html
<table id="performance-table">
  <thead>
    <tr>
      <th scope="col">Metric</th>
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
      <td class="performance-metric">96.7%</td>
    </tr>
    <tr>
      <td>Response Time</td>
      <td>24h</td>
      <td>22h</td>
      <td class="performance-metric">108.3%</td>
    </tr>
  </tbody>
  <tfoot id="performance-footer">
    <tr>
      <td><strong>Overall Performance</strong></td>
      <td colspan="3" id="overall-score">Calculating...</td>
    </tr>
  </tfoot>
</table>

<script>
function calculatePerformance() {
  const metrics = document.querySelectorAll('.performance-metric');
  let total = 0;
  
  metrics.forEach(metric => {
    const value = parseFloat(metric.textContent);
    total += value;
  });
  
  const average = total / metrics.length;
  const overallScore = document.getElementById('overall-score');
  
  overallScore.textContent = `${average.toFixed(1)}% of Target`;
  
  if (average >= 100) {
    overallScore.style.color = '#28a745';
    overallScore.innerHTML += ' <span class="success-indicator">✓ Exceeding Target</span>';
  } else if (average >= 90) {
    overallScore.style.color = '#ffc107';
    overallScore.innerHTML += ' <span class="warning-indicator">⚠ Near Target</span>';
  } else {
    overallScore.style.color = '#dc3545';
    overallScore.innerHTML += ' <span class="danger-indicator">✗ Below Target</span>';
  }
}

// Calculate when page loads
document.addEventListener('DOMContentLoaded', calculatePerformance);
</script>
```

---

## Notes

* **Rendering position**: Always appears at the bottom of the table visually, regardless of HTML source order
* **Semantic importance**: Provides structural meaning to summary rows beyond visual presentation
* **Accessibility benefits**:
  - Screen readers can distinguish footer content from main data
  - Helps users quickly locate summary information
  - Provides context for calculated totals and conclusions
* **Print behavior**: May repeat on each printed page for long tables in some browsers
* **CSS styling**:
  - Often styled differently from `<tbody>` for visual distinction
  - Commonly uses borders, background colors, and bold text
  - Can be styled independently from other table sections
* **Browser support**: Well-supported in all modern browsers
* **Common mistakes**:
  - Using `<tfoot>` for regular data rows instead of summary information
  - Expecting `<tfoot>` to render in source order (it always renders last)
  - Using multiple `<tfoot>` elements (only one allowed per table)
  - Forgetting to use proper cell spanning for summary rows
* **JavaScript interaction**:
  - Ideal for dynamically calculated totals and summaries
  - Can be efficiently updated without affecting main table data
  - Useful for real-time calculations in interactive tables
* **Responsive considerations**:
  - May need special styling for mobile devices
  - Consider stacking layout for complex footer rows on small screens
  - Ensure summary information remains clear and accessible
* **SEO benefits**: Proper table structure helps search engines understand data relationships and summaries

---
