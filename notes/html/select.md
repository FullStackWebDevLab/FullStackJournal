# `<select>`

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

The `<select>` element represents a control that provides a menu of options, allowing users to choose one or multiple values from a list. It creates a dropdown selection interface that can display options in a compact form, making it ideal for forms where space is limited or when presenting a predefined set of choices.

---

## Syntax and Variants

+ **Standard syntax**: `<select>...</select>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps `<option>` and `<optgroup>` elements
+ **No self-closing variant**: Must contain option elements
+ **Selection control**: Creates dropdown or list box interface

---

## Attributes

+ **Core attributes**:
  - `name` (optional): Name for form submission and scripting
  - `multiple` (optional): Allows multiple selections (boolean)
  - `size` (optional): Number of visible options in list box
  - `required` (optional): Marks field as mandatory (boolean)
  - `disabled` (optional): Disables the select control (boolean)
  - `autofocus` (optional): Automatically focus on page load (boolean)
  - `form` (optional): Associates select with a form (by form ID)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No deprecated attributes**: All original attributes remain supported

---

## Content Model

+ **Permitted content**:
  - Zero or more `<option>` elements
  - Zero or more `<optgroup>` elements (for grouping options)
  - Script-supporting elements (`<script>`, `<template>`)
+ **Required children**: At least one `<option>` for meaningful selection
+ **Option structure**: Options can be grouped logically with `<optgroup>`
+ **Mixed content**: Cannot contain text directly, only option elements

---

## Context

+ **Required parent**: Should be within a `<form>` element for submission
+ **Common locations**:
  - Directly within `<form>` elements
  - Within `<div>`, `<fieldset>`, or other form containers
  - With associated `<label>` elements for accessibility
+ **Form association**: Can be associated with forms using `form` attribute

---

## Behavior and Semantics

+ **Default display**: Inline-block element
+ **Default styling**:
  - `display: inline-block`
  - Browser-dependent dropdown appearance
  - Typically includes dropdown arrow indicator
  - System font and colors
+ **Interactive behavior**:
  - Click/tap opens dropdown menu
  - Keyboard navigation with arrow keys
  - Supports single or multiple selection
  - Can be searchable in some browsers
+ **Semantic meaning**:
  - Represents a selection control with predefined options
  - Screen readers announce as "combobox" or "listbox"
  - Provides context for option selection
+ **Accessibility**: Requires proper labeling and may need additional instructions for complex selections

---

## Examples

**Basic select dropdown:**
```html
<label for="country">Country:</label>
<select id="country" name="country">
  <option value="">Select a country</option>
  <option value="us">United States</option>
  <option value="ca">Canada</option>
  <option value="uk">United Kingdom</option>
  <option value="au">Australia</option>
</select>
```

**Select with default selected option:**
```html
<label for="color">Favorite Color:</label>
<select id="color" name="color">
  <option value="red">Red</option>
  <option value="blue" selected>Blue</option>
  <option value="green">Green</option>
  <option value="yellow">Yellow</option>
</select>
```

**Required select with validation:**
```html
<label for="category">Product Category:</label>
<select id="category" name="category" required>
  <option value="">Please select a category</option>
  <option value="electronics">Electronics</option>
  <option value="clothing">Clothing</option>
  <option value="books">Books</option>
  <option value="home">Home & Garden</option>
</select>
```

**Multiple selection with size:**
```html
<label for="skills">Skills (select multiple):</label>
<select id="skills" name="skills" multiple size="4">
  <option value="html">HTML</option>
  <option value="css">CSS</option>
  <option value="js">JavaScript</option>
  <option value="python">Python</option>
  <option value="java">Java</option>
  <option value="sql">SQL</option>
</select>
<small>Hold Ctrl/Cmd to select multiple options</small>
```

**Grouped options with optgroup:**
```html
<label for="car-model">Car Model:</label>
<select id="car-model" name="car_model">
  <option value="">Select a model</option>
  
  <optgroup label="Toyota">
    <option value="camry">Camry</option>
    <option value="corolla">Corolla</option>
    <option value="rav4">RAV4</option>
  </optgroup>
  
  <optgroup label="Honda">
    <option value="civic">Civic</option>
    <option value="accord">Accord</option>
    <option value="crv">CR-V</option>
  </optgroup>
  
  <optgroup label="Ford">
    <option value="focus">Focus</option>
    <option value="fusion">Fusion</option>
    <option value="escape">Escape</option>
  </optgroup>
</select>
```

**Styled select with CSS:**
```html
<label for="styled-select">Choose an option:</label>
<div class="select-wrapper">
  <select id="styled-select" name="styled_option" class="custom-select">
    <option value="">Select an option</option>
    <option value="premium">Premium Plan</option>
    <option value="standard">Standard Plan</option>
    <option value="basic">Basic Plan</option>
  </select>
  <span class="select-arrow" aria-hidden="true">▼</span>
</div>

<style>
.select-wrapper {
  position: relative;
  display: inline-block;
  max-width: 300px;
}

.custom-select {
  width: 100%;
  padding: 12px 40px 12px 16px;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  background: white;
  font-size: 16px;
  appearance: none;
  cursor: pointer;
}

.custom-select:focus {
  border-color: #007bff;
  outline: none;
  box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.1);
}

.select-arrow {
  position: absolute;
  right: 16px;
  top: 50%;
  transform: translateY(-50%);
  pointer-events: none;
  color: #666;
}
</style>
```

**Accessible select with ARIA:**
```html
<div class="form-group">
  <label for="accessible-select" id="select-label">
    Notification Frequency
    <span class="required" aria-hidden="true">*</span>
  </label>
  
  <select id="accessible-select"
          name="notification_frequency"
          required
          aria-labelledby="select-label"
          aria-required="true"
          aria-describedby="select-help">
    <option value="">Choose frequency</option>
    <option value="instant">Instant</option>
    <option value="hourly">Hourly Digest</option>
    <option value="daily">Daily Summary</option>
    <option value="weekly">Weekly Report</option>
  </select>
  
  <div id="select-help" class="help-text">
    How often you would like to receive notifications about updates.
  </div>
</div>
```

**Select with dynamic options via JavaScript:**
```html
<label for="dynamic-select">Select Timezone:</label>
<select id="dynamic-select" name="timezone">
  <option value="">Loading timezones...</option>
</select>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const timezones = [
    { value: 'est', label: 'Eastern Time (EST)' },
    { value: 'cst', label: 'Central Time (CST)' },
    { value: 'mst', label: 'Mountain Time (MST)' },
    { value: 'pst', label: 'Pacific Time (PST)' },
    { value: 'ast', label: 'Alaska Time (AST)' },
    { value: 'hst', label: 'Hawaii Time (HST)' }
  ];
  
  const select = document.getElementById('dynamic-select');
  select.innerHTML = '<option value="">Select your timezone</option>';
  
  timezones.forEach(tz => {
    const option = document.createElement('option');
    option.value = tz.value;
    option.textContent = tz.label;
    select.appendChild(option);
  });
});
</script>
```

**Select with change event handling:**
```html
<label for="category-select">Product Category:</label>
<select id="category-select" name="category">
  <option value="">Select a category</option>
  <option value="electronics">Electronics</option>
  <option value="clothing">Clothing</option>
  <option value="books">Books</option>
</select>

<div id="category-details" class="details-panel" hidden>
  <!-- Dynamic content will appear here -->
</div>

<script>
document.getElementById('category-select').addEventListener('change', function() {
  const detailsPanel = document.getElementById('category-details');
  const selectedValue = this.value;
  
  if (!selectedValue) {
    detailsPanel.hidden = true;
    return;
  }
  
  // Show loading state
  detailsPanel.hidden = false;
  detailsPanel.innerHTML = '<p>Loading category details...</p>';
  
  // Simulate API call
  setTimeout(() => {
    const details = {
      electronics: 'Electronics include devices, components, and accessories.',
      clothing: 'Clothing includes apparel, footwear, and accessories.',
      books: 'Books include fiction, non-fiction, and educational materials.'
    };
    
    detailsPanel.innerHTML = `
      <h3>Category Information</h3>
      <p>${details[selectedValue]}</p>
      <button onclick="hideDetails()">Close</button>
    `;
  }, 1000);
});

function hideDetails() {
  document.getElementById('category-details').hidden = true;
}
</script>

<style>
.details-panel {
  margin-top: 16px;
  padding: 16px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: #f9f9f9;
}
</style>
```

**Select with search functionality:**
```html
<label for="searchable-select">Search for a Country:</label>
<input type="text" id="select-search" placeholder="Type to search..." class="search-input">
<select id="searchable-select" name="country" size="8" class="searchable-select">
  <option value="af">Afghanistan</option>
  <option value="al">Albania</option>
  <option value="dz">Algeria</option>
  <option value="us">United States</option>
  <option value="ca">Canada</option>
  <option value="uk">United Kingdom</option>
  <option value="fr">France</option>
  <option value="de">Germany</option>
  <!-- More countries... -->
</select>

<script>
document.getElementById('select-search').addEventListener('input', function() {
  const searchTerm = this.value.toLowerCase();
  const select = document.getElementById('searchable-select');
  const options = select.getElementsByTagName('option');
  
  for (let option of options) {
    const text = option.textContent.toLowerCase();
    option.style.display = text.includes(searchTerm) ? '' : 'none';
  }
});
</script>

<style>
.search-input {
  width: 100%;
  max-width: 300px;
  padding: 8px 12px;
  margin-bottom: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.searchable-select {
  width: 100%;
  max-width: 300px;
}
</style>
```

**Select with dependent options:**
```html
<label for="country-select">Country:</label>
<select id="country-select" name="country">
  <option value="">Select a country</option>
  <option value="us">United States</option>
  <option value="ca">Canada</option>
  <option value="uk">United Kingdom</option>
</select>

<label for="state-select">State/Province:</label>
<select id="state-select" name="state" disabled>
  <option value="">First select a country</option>
</select>

<script>
const statesByCountry = {
  us: [
    { value: 'ca', label: 'California' },
    { value: 'ny', label: 'New York' },
    { value: 'tx', label: 'Texas' },
    { value: 'fl', label: 'Florida' }
  ],
  ca: [
    { value: 'on', label: 'Ontario' },
    { value: 'bc', label: 'British Columbia' },
    { value: 'qc', label: 'Quebec' },
    { value: 'ab', label: 'Alberta' }
  ],
  uk: [
    { value: 'eng', label: 'England' },
    { value: 'sct', label: 'Scotland' },
    { value: 'wls', label: 'Wales' },
    { value: 'nir', label: 'Northern Ireland' }
  ]
};

document.getElementById('country-select').addEventListener('change', function() {
  const country = this.value;
  const stateSelect = document.getElementById('state-select');
  
  if (!country) {
    stateSelect.disabled = true;
    stateSelect.innerHTML = '<option value="">First select a country</option>';
    return;
  }
  
  const states = statesByCountry[country] || [];
  stateSelect.disabled = false;
  stateSelect.innerHTML = '<option value="">Select a state/province</option>';
  
  states.forEach(state => {
    const option = document.createElement('option');
    option.value = state.value;
    option.textContent = state.label;
    stateSelect.appendChild(option);
  });
});
</script>
```

**Select with custom validation:**
```html
<form id="validation-form">
  <label for="age-range">Age Range:</label>
  <select id="age-range" name="age_range" required>
    <option value="">Select your age range</option>
    <option value="under18">Under 18</option>
    <option value="18-25">18-25</option>
    <option value="26-35">26-35</option>
    <option value="36-50">36-50</option>
    <option value="over50">Over 50</option>
  </select>
  <span id="age-error" class="error-message" aria-live="polite"></span>
  
  <button type="submit">Submit</button>
</form>

<script>
document.getElementById('validation-form').addEventListener('submit', function(event) {
  const ageSelect = document.getElementById('age-range');
  const errorElement = document.getElementById('age-error');
  
  if (!ageSelect.value) {
    event.preventDefault();
    errorElement.textContent = 'Please select your age range.';
    ageSelect.focus();
  } else if (ageSelect.value === 'under18') {
    event.preventDefault();
    errorElement.textContent = 'You must be 18 or older to proceed.';
    ageSelect.focus();
  } else {
    errorElement.textContent = '';
  }
});
</script>

<style>
.error-message {
  color: #dc3545;
  font-size: 0.875em;
  display: block;
  margin-top: 4px;
}
</style>
```

---

## Notes

* **Accessibility requirements**:
  - Always associate with `<label>` elements
  - Use `aria-*` attributes for complex select controls
  - Ensure keyboard navigation works properly
  - Provide clear instructions for multiple selections
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Forgetting to include a default empty option for required selects
  - Not providing proper labels for screen reader users
  - Using selects for very long lists (consider searchable alternatives)
  - Overlooking mobile user experience with large option sets
  - Forgetting `name` attribute for form submission
* **Mobile considerations**:
  - Native select interfaces vary by mobile OS
  - Large option sets may be difficult to navigate on mobile
  - Consider custom select implementations for better mobile UX
* **Performance**: 
  - Very large option sets (1000+) can impact performance
  - Consider virtual scrolling or search for large datasets
  - Dynamic option loading can improve initial page load
* **Styling limitations**:
  - Native select styling is limited and varies by browser
  - Custom select implementations often needed for consistent design
  - Consider accessibility when creating custom select controls
* **Form submission**:
  - Selected option's `value` attribute is submitted, not the text content
  - For multiple selects, all selected values are submitted as an array
  - Disabled options cannot be selected or submitted

---
