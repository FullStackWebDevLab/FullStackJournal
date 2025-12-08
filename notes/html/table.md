# `<table>`

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

The `<table>` element represents tabular data; information presented in a two-dimensional grid comprised of rows and columns of cells containing data. It provides a structured way to display relational data, comparisons, schedules, pricing, and other information that benefits from a grid-like organization where the relationship between data points is important.

---

## Syntax and Variants

+ **Standard syntax**: `<table>...</table>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps table structure elements
+ **No self-closing variant**: Must contain table content
+ **Complex structure**: Composed of multiple child elements for proper semantics

---

## Attributes

+ **Core attributes**:
  - `border` (deprecated): Specifies table border width (use CSS instead)
  - `cellpadding` (deprecated): Space between cell content and borders (use CSS)
  - `cellspacing` (deprecated): Space between cells (use CSS)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Deprecated attributes**:
  - `align` (use CSS `float` or `text-align`)
  - `bgcolor` (use CSS `background-color`)
  - `width` (use CSS `width`)
  - `frame`, `rules` (use CSS borders)

---

## Content Model

+ **Permitted content** in this order:
  - Optional one `<caption>` element
  - Zero or more `<colgroup>` elements
  - Optional one `<thead>` element
  - Optional one `<tfoot>` element
  - Either:
    - One or more `<tbody>` elements
    - Or one or more `<tr>` elements
  - Optional one `<tfoot>` element (but only one total)

+ **Required children**: At least one `<tr>` or `<tbody>` for data content

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<article>`, `<section>` for data presentation
  - In dashboards, reports, and data visualization
  - For pricing comparisons, schedules, and specifications
  - Within `<div>` containers for layout purposes
+ **Flow content**: Treated as block-level element in document flow

---

## Behavior and Semantics

+ **Default display**: Table-level element
+ **Default styling**:
  - `display: table`
  - `border-collapse: separate`
  - `border-spacing: 2px`
  - `border-color: gray`
+ **Layout behavior**:
  - Creates a grid structure for tabular data
  - Automatically adjusts column widths based on content
  - Supports row and column spanning
+ **Semantic meaning**:
  - Represents tabular data with relationships
  - Screen readers announce table structure and navigation
  - Conveys data relationships to assistive technologies
+ **Accessibility**: Critical to provide proper headers and descriptions for screen reader users

---

## Examples

**Basic data table:**
```html
<table>
  <tr>
    <th>Name</th>
    <th>Age</th>
    <th>Department</th>
  </tr>
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

**Structured table with sections:**
```html
<table>
  <caption>Employee Quarterly Performance Ratings</caption>
  <thead>
    <tr>
      <th scope="col">Employee ID</th>
      <th scope="col">Name</th>
      <th scope="col">Q1 Rating</th>
      <th scope="col">Q2 Rating</th>
      <th scope="col">Q3 Rating</th>
      <th scope="col">Q4 Rating</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">EMP001</th>
      <td>John Smith</td>
      <td>4.2</td>
      <td>4.5</td>
      <td>4.3</td>
      <td>4.7</td>
    </tr>
    <tr>
      <th scope="row">EMP002</th>
      <td>Sarah Johnson</td>
      <td>3.8</td>
      <td>4.1</td>
      <td>4.4</td>
      <td>4.6</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="2">Department Average</td>
      <td>4.0</td>
      <td>4.3</td>
      <td>4.35</td>
      <td>4.65</td>
    </tr>
  </tfoot>
</table>
```

**Accessible table with complex headers:**
```html
<table aria-labelledby="pricing-title">
  <caption id="pricing-title">Monthly Subscription Pricing</caption>
  <thead>
    <tr>
      <th scope="col">Plan</th>
      <th scope="col" colspan="2">Individual</th>
      <th scope="col" colspan="2">Team</th>
      <th scope="col" colspan="2">Enterprise</th>
    </tr>
    <tr>
      <th scope="col"></th>
      <th scope="col">Monthly</th>
      <th scope="col">Annual</th>
      <th scope="col">Monthly</th>
      <th scope="col">Annual</th>
      <th scope="col">Monthly</th>
      <th scope="col">Annual</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Price</th>
      <td>$15</td>
      <td>$150</td>
      <td>$25</td>
      <td>$250</td>
      <td>$45</td>
      <td>$450</td>
    </tr>
    <tr>
      <th scope="row">Users</th>
      <td>1</td>
      <td>1</td>
      <td>5</td>
      <td>5</td>
      <td>Unlimited</td>
      <td>Unlimited</td>
    </tr>
  </tbody>
</table>
```

**Table with column groups and styling:**
```html
<table class="financial-data">
  <colgroup>
    <col span="1" class="description-col">
    <col span="4" class="quarter-col">
  </colgroup>
  <caption>Quarterly Financial Report (in millions)</caption>
  <thead>
    <tr>
      <th scope="col">Category</th>
      <th scope="col">Q1 2024</th>
      <th scope="col">Q2 2024</th>
      <th scope="col">Q3 2024</th>
      <th scope="col">Q4 2024</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Revenue</th>
      <td>$125.4</td>
      <td>$138.2</td>
      <td>$142.7</td>
      <td>$156.3</td>
    </tr>
    <tr>
      <th scope="row">Expenses</th>
      <td>$89.1</td>
      <td>$92.4</td>
      <td>$95.8</td>
      <td>$98.2</td>
    </tr>
    <tr>
      <th scope="row">Net Income</th>
      <td>$36.3</td>
      <td>$45.8</td>
      <td>$46.9</td>
      <td>$58.1</td>
    </tr>
  </tbody>
</table>
```

**Responsive table design:**
```html
<div class="table-container">
  <table class="responsive-table">
    <thead>
      <tr>
        <th scope="col">Product</th>
        <th scope="col">Category</th>
        <th scope="col">Price</th>
        <th scope="col">Stock</th>
        <th scope="col">Rating</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td data-label="Product">Wireless Headphones</td>
        <td data-label="Category">Audio</td>
        <td data-label="Price">$199.99</td>
        <td data-label="Stock">In Stock</td>
        <td data-label="Rating">4.5/5</td>
      </tr>
      <tr>
        <td data-label="Product">Smart Watch</td>
        <td data-label="Category">Wearables</td>
        <td data-label="Price">$299.99</td>
        <td data-label="Stock">Low Stock</td>
        <td data-label="Rating">4.2/5</td>
      </tr>
    </tbody>
  </table>
</div>

<style>
.table-container {
  overflow-x: auto;
}

.responsive-table {
  width: 100%;
  border-collapse: collapse;
}

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

**Interactive table with sorting:**
```html
<table id="sortable-table" class="sortable">
  <thead>
    <tr>
      <th scope="col" data-sort="string">Name</th>
      <th scope="col" data-sort="number">Age</th>
      <th scope="col" data-sort="string">Department</th>
      <th scope="col" data-sort="number">Salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John Smith</td>
      <td>32</td>
      <td>Engineering</td>
      <td>85000</td>
    </tr>
    <tr>
      <td>Sarah Johnson</td>
      <td>28</td>
      <td>Marketing</td>
      <td>72000</td>
    </tr>
    <tr>
      <td>Mike Chen</td>
      <td>45</td>
      <td>Engineering</td>
      <td>110000</td>
    </tr>
  </tbody>
</table>

<script>
document.querySelectorAll('#sortable-table th').forEach(header => {
  header.addEventListener('click', () => {
    const table = header.closest('table');
    const tbody = table.querySelector('tbody');
    const rows = Array.from(tbody.querySelectorAll('tr'));
    const columnIndex = Array.from(header.parentNode.children).indexOf(header);
    const sortType = header.dataset.sort;
    
    rows.sort((a, b) => {
      const aValue = a.children[columnIndex].textContent;
      const bValue = b.children[columnIndex].textContent;
      
      if (sortType === 'number') {
        return Number(aValue) - Number(bValue);
      }
      return aValue.localeCompare(bValue);
    });
    
    rows.forEach(row => tbody.appendChild(row));
  });
});
</script>
```

**Complex table with row and column spanning:**
```html
<table class="schedule">
  <caption>Weekly Class Schedule</caption>
  <thead>
    <tr>
      <th scope="col">Time</th>
      <th scope="col">Monday</th>
      <th scope="col">Tuesday</th>
      <th scope="col">Wednesday</th>
      <th scope="col">Thursday</th>
      <th scope="col">Friday</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">9:00 - 10:30</th>
      <td rowspan="2">Mathematics<br>Room 101</td>
      <td>Physics<br>Room 201</td>
      <td rowspan="2">Mathematics<br>Room 101</td>
      <td>Chemistry<br>Lab 3</td>
      <td>Computer Science<br>Lab 1</td>
    </tr>
    <tr>
      <th scope="row">10:45 - 12:15</th>
      <td>English Literature<br>Room 105</td>
      <td>History<br>Room 102</td>
      <td>Art Studio<br>Room 301</td>
    </tr>
    <tr>
      <th scope="row">1:00 - 2:30</th>
      <td colspan="5" style="text-align: center; background: #f0f0f0;">
        Lunch Break
      </td>
    </tr>
  </tbody>
</table>
```

**Table with accessibility features:**
```html
<table aria-describedby="table-description">
  <caption>Project Timeline and Responsibilities</caption>
  <thead>
    <tr>
      <th scope="col" id="phase">Phase</th>
      <th scope="col" id="timeline">Timeline</th>
      <th scope="col" id="lead">Lead</th>
      <th scope="col" id="team">Team Members</th>
      <th scope="col" id="status">Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row" id="planning" headers="phase">Planning</th>
      <td headers="planning timeline">Week 1-2</td>
      <td headers="planning lead">Project Manager</td>
      <td headers="planning team">All Teams</td>
      <td headers="planning status">
        <span aria-label="Completed" class="status-completed">✓</span>
      </td>
    </tr>
    <tr>
      <th scope="row" id="development" headers="phase">Development</th>
      <td headers="development timeline">Week 3-8</td>
      <td headers="development lead">Tech Lead</td>
      <td headers="development team">Dev Team</td>
      <td headers="development status">
        <span aria-label="In Progress" class="status-progress">⟳</span>
      </td>
    </tr>
  </tbody>
</table>
<div id="table-description" class="visually-hidden">
  This table shows the project timeline with phases, durations, responsible leads, team members, and current status indicators.
</div>
```

---

## Notes

* **Semantic purpose**: Use only for tabular data, not for layout purposes
* **Accessibility requirements**:
  - Use `<th>` elements for headers with proper `scope` attributes
  - Provide captions for table context
  - Use `aria-describedby` for complex tables
  - Ensure proper reading order and navigation
* **CSS styling**:
  - Use `border-collapse: collapse` for clean borders
  - Style with `padding`, `border`, and `background-color`
  - Consider responsive designs for mobile devices
* **Browser support**: Universally supported but styling may vary
* **Common mistakes**:
  - Using tables for page layout (use CSS Grid/Flexbox instead)
  - Missing header cells or proper scope attributes
  - Overusing rowspan/colspan making tables difficult to navigate
  - Not providing alternatives for complex data
* **Responsive strategies**:
  - Horizontal scrolling containers
  - Stacked layouts on mobile
  - Hidden columns on smaller screens
  - Alternative data visualization for complex tables
* **SEO benefits**: Proper table structure helps search engines understand data relationships
* **Performance**: Complex tables with many cells can impact rendering performance
* **Print considerations**: Tables generally print well but test pagination breaks

---
