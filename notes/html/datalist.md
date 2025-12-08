# `<datalist>`

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

The `<datalist>` element provides a set of predefined options for an `<input>` element, offering users suggestions while still allowing them to enter custom values. It creates an accessible, native autocomplete or suggestion interface without requiring JavaScript, enhancing user experience by reducing typing effort and ensuring data consistency while maintaining flexibility for free-form input.

---

## Syntax and Variants

+ **Standard syntax**: `<datalist>...</datalist>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Contains `<option>` elements as suggestions
+ **No self-closing variant**: Must have proper opening and closing tags
+ **Association method**: Linked to input via `list` attribute matching the datalist's `id`

---

## Attributes

+ **Core attributes**:
  - `id` (required): Unique identifier used by input elements to reference the datalist

+ **Global attributes**: `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No specific attributes** beyond `id` and global attributes

---

## Content Model

+ **Permitted content**: Zero or more `<option>` elements
+ **Allowed content**:
  - `<option>` elements with `value` attributes
  - `<option>` elements with text content (used as value if no `value` attribute)
+ **Restricted content**: Cannot contain other elements besides `<option>`
+ **Empty datalist**: Valid but provides no suggestions

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<form>` elements
  - Within `<div>` containers near associated inputs
  - In the `<body>` anywhere (datalists can be referenced from anywhere in document)
+ **Association**: Not limited to parent form; any input can reference any datalist via `list` attribute
+ **Multiple references**: Single datalist can be used by multiple input elements

---

## Behavior and Semantics

+ **Default display**: None (hidden element)
+ **Default styling**: Not visible to users; only affects associated input behavior
+ **Interactive behavior**:
  - Suggestions appear when user focuses on associated input
  - Filtering occurs as user types (browser matches input against option values/labels)
  - Users can select from suggestions or continue typing custom values
  - Keyboard navigation supported through browser's native autocomplete interface
+ **Semantic meaning**:
  - Represents a set of predefined options for an input control
  - Provides accessible autocomplete functionality
  - Screen readers announce available options when appropriate
+ **Accessibility**: Native browser support ensures consistent accessibility across platforms

---

## Examples

**Basic datalist with text input:**
```html
<label for="browser">Choose a browser:</label>
<input type="text" id="browser" name="browser" list="browsers">

<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
  <option value="Edge">
  <option value="Opera">
</datalist>
```

**Datalist with different value and label:**
```html
<label for="country">Country:</label>
<input type="text" id="country" name="country" list="countries">

<datalist id="countries">
  <option value="US" label="United States">
  <option value="CA" label="Canada">
  <option value="MX" label="Mexico">
  <option value="UK" label="United Kingdom">
  <option value="FR" label="France">
  <option value="DE" label="Germany">
  <option value="JP" label="Japan">
</datalist>
```

**Datalist with email suggestions:**
```html
<label for="email">Email address:</label>
<input type="email" id="email" name="email" list="email-suggestions" placeholder="user@example.com">

<datalist id="email-suggestions">
  <option value="user@gmail.com">
  <option value="user@yahoo.com">
  <option value="user@hotmail.com">
  <option value="user@outlook.com">
  <option value="user@company.com">
</datalist>
```

**Datalist with number input:**
```html
<label for="quantity">Quantity (1-50):</label>
<input type="number" id="quantity" name="quantity" min="1" max="50" list="common-quantities">

<datalist id="common-quantities">
  <option value="1">
  <option value="5">
  <option value="10">
  <option value="25">
  <option value="50">
</datalist>
```

**Datalist with range input:**
```html
<label for="volume">Volume level:</label>
<input type="range" id="volume" name="volume" min="0" max="100" list="volume-markers">

<datalist id="volume-markers">
  <option value="0" label="Off">
  <option value="25" label="Low">
  <option value="50" label="Medium">
  <option value="75" label="High">
  <option value="100" label="Max">
</datalist>
```

**Styled datalist with CSS:**
```html
<label for="theme">Choose a theme:</label>
<input type="text" id="theme" name="theme" list="themes" class="styled-input">

<datalist id="themes">
  <option value="Dark">
  <option value="Light">
  <option value="Blue">
  <option value="Green">
  <option value="High Contrast">
  <option value="Solarized">
</datalist>

<style>
.styled-input {
  padding: 8px 12px;
  border: 2px solid #ddd;
  border-radius: 4px;
  font-size: 16px;
  width: 200px;
}

.styled-input:focus {
  border-color: #007bff;
  outline: none;
  box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.1);
}
</style>
```

**Multiple inputs using same datalist:**
```html
<div class="form-group">
  <label for="from-city">From:</label>
  <input type="text" id="from-city" name="from_city" list="cities" placeholder="Departure city">
</div>

<div class="form-group">
  <label for="to-city">To:</label>
  <input type="text" id="to-city" name="to_city" list="cities" placeholder="Destination city">
</div>

<datalist id="cities">
  <option value="New York">
  <option value="Los Angeles">
  <option value="Chicago">
  <option value="Houston">
  <option value="Phoenix">
  <option value="Philadelphia">
  <option value="San Antonio">
  <option value="San Diego">
  <option value="Dallas">
  <option value="San Jose">
</datalist>

<style>
.form-group {
  margin-bottom: 16px;
}

.form-group label {
  display: block;
  margin-bottom: 4px;
  font-weight: 600;
}

.form-group input {
  padding: 8px 12px;
  border: 1px solid #ddd;
  border-radius: 4px;
  width: 250px;
}
</style>
```

**Datalist with categories using option groups:**
```html
<label for="product">Search products:</label>
<input type="text" id="product" name="product" list="products" autocomplete="off">

<datalist id="products">
  <optgroup label="Electronics">
    <option value="iPhone 14">
    <option value="MacBook Pro">
    <option value="iPad Air">
    <option value="Apple Watch">
  </optgroup>
  <optgroup label="Home & Kitchen">
    <option value="Coffee Maker">
    <option value="Air Fryer">
    <option value="Blender">
    <option value="Toaster">
  </optgroup>
  <optgroup label="Books">
    <option value="Science Fiction">
    <option value="Mystery">
    <option value="Biography">
    <option value="History">
  </optgroup>
</datalist>
```

**Datalist with complex values and labels:**
```html
<label for="shipping">Shipping method:</label>
<input type="text" id="shipping" name="shipping" list="shipping-methods">

<datalist id="shipping-methods">
  <option value="standard" label="Standard (5-7 days) - Free">
  <option value="expedited" label="Expedited (2-3 days) - $9.99">
  <option value="overnight" label="Overnight (1 day) - $19.99">
  <option value="same_day" label="Same Day - $29.99">
  <option value="international" label="International - $49.99">
</datalist>
```

**Datalist with date suggestions:**
```html
<label for="event-date">Event date:</label>
<input type="text" id="event-date" name="event_date" list="common-dates" placeholder="YYYY-MM-DD">

<datalist id="common-dates">
  <option value="2024-01-01" label="New Year's Day">
  <option value="2024-02-14" label="Valentine's Day">
  <option value="2024-03-17" label="St. Patrick's Day">
  <option value="2024-04-01" label="April Fool's Day">
  <option value="2024-07-04" label="Independence Day">
  <option value="2024-10-31" label="Halloween">
  <option value="2024-12-25" label="Christmas">
</datalist>
```

**Datalist with color names:**
```html
<label for="favorite-color">Favorite color:</label>
<input type="text" id="favorite-color" name="favorite_color" list="colors">

<datalist id="colors">
  <option value="Red">
  <option value="Orange">
  <option value="Yellow">
  <option value="Green">
  <option value="Blue">
  <option value="Purple">
  <option value="Pink">
  <option value="Brown">
  <option value="Black">
  <option value="White">
  <option value="Gray">
  <option value="Cyan">
  <option value="Magenta">
  <option value="Teal">
  <option value="Navy">
</datalist>
```

**Datalist with programming languages:**
```html
<label for="language">Programming language:</label>
<input type="text" id="language" name="language" list="languages" autocomplete="off">

<datalist id="languages">
  <option value="JavaScript">
  <option value="Python">
  <option value="Java">
  <option value="C#">
  <option value="PHP">
  <option value="TypeScript">
  <option value="Ruby">
  <option value="Go">
  <option value="Rust">
  <option value="Swift">
  <option value="Kotlin">
  <option value="Scala">
  <option value="R">
  <option value="MATLAB">
  <option value="Perl">
</datalist>
```

**Datalist in a search form:**
```html
<form role="search">
  <label for="site-search" class="visually-hidden">Search the site:</label>
  <div class="search-container">
    <input type="search" 
           id="site-search" 
           name="q" 
           list="search-suggestions"
           placeholder="What are you looking for?"
           aria-describedby="search-help">
    <button type="submit">Search</button>
  </div>
  <div id="search-help" class="help-text">
    Type to see search suggestions or enter your own terms.
  </div>
</form>

<datalist id="search-suggestions">
  <option value="Product Documentation">
  <option value="API Reference">
  <option value="Getting Started Guide">
  <option value="Troubleshooting">
  <option value="Release Notes">
  <option value="Support Contact">
  <option value="Pricing Information">
  <option value="Feature Requests">
</datalist>

<style>
.search-container {
  display: flex;
  max-width: 400px;
  margin-bottom: 8px;
}

.search-container input {
  flex: 1;
  padding: 10px 12px;
  border: 2px solid #007bff;
  border-right: none;
  border-radius: 4px 0 0 4px;
  font-size: 16px;
}

.search-container button {
  padding: 10px 20px;
  background: #007bff;
  color: white;
  border: 2px solid #007bff;
  border-radius: 0 4px 4px 0;
  cursor: pointer;
  font-size: 16px;
}

.help-text {
  font-size: 0.875em;
  color: #666;
}

.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
</style>
```

**Datalist with dynamic options using JavaScript:**
```html
<label for="dynamic-input">Dynamic suggestions:</label>
<input type="text" id="dynamic-input" list="dynamic-list">

<datalist id="dynamic-list"></datalist>

<script>
// Example: Populate datalist based on user input or other conditions
const dynamicList = document.getElementById('dynamic-list');
const dynamicInput = document.getElementById('dynamic-input');

// Sample data - in real application, this could come from an API
const suggestionData = {
  'a': ['Apple', 'Apricot', 'Avocado'],
  'b': ['Banana', 'Blueberry', 'Blackberry'],
  'c': ['Cherry', 'Cantaloupe', 'Coconut'],
  'd': ['Date', 'Dragonfruit', 'Durian'],
  // ... more data
};

dynamicInput.addEventListener('input', function() {
  const firstChar = this.value.charAt(0).toLowerCase();
  const suggestions = suggestionData[firstChar] || [];
  
  // Clear existing options
  dynamicList.innerHTML = '';
  
  // Add new options
  suggestions.forEach(suggestion => {
    const option = document.createElement('option');
    option.value = suggestion;
    dynamicList.appendChild(option);
  });
});
</script>
```

**Datalist with validation feedback:**
```html
<label for="username">Username:</label>
<input type="text" 
       id="username" 
       name="username" 
       list="username-suggestions"
       pattern="[a-zA-Z0-9_]{3,20}"
       aria-describedby="username-help username-error"
       required>

<datalist id="username-suggestions">
  <option value="john_doe">
  <option value="jane_smith">
  <option value="admin_user">
  <option value="test_account">
  <option value="demo_user">
</datalist>

<div id="username-help" class="help-text">
  Choose a username or select from suggestions. 3-20 characters, letters, numbers, and underscores only.
</div>

<div id="username-error" class="error-text" role="alert" hidden>
  Please choose a valid username from suggestions or enter your own (3-20 characters, letters, numbers, underscores).
</div>

<script>
document.getElementById('username').addEventListener('blur', function() {
  const errorElement = document.getElementById('username-error');
  if (!this.checkValidity()) {
    errorElement.hidden = false;
  } else {
    errorElement.hidden = true;
  }
});
</script>

<style>
.help-text {
  font-size: 0.875em;
  color: #666;
  margin-top: 4px;
}

.error-text {
  font-size: 0.875em;
  color: #dc3545;
  margin-top: 4px;
}
</style>
```

---

## Notes

* **Browser compatibility**: Well supported in modern browsers, but always test fallback behavior
* **Input types**: Works with `text`, `search`, `url`, `tel`, `email`, `number`, `range`, `date`, and other text-like inputs
* **Fallback strategy**: 
  - Browsers that don't support datalist will simply ignore it
  - Inputs will function as normal text inputs without suggestions
  - Consider JavaScript polyfills for critical autocomplete functionality
* **Accessibility considerations**:
  - Native browser implementation generally provides good accessibility
  - Screen readers typically announce when suggestions are available
  - Ensure proper labeling of both input and datalist options
* **Common mistakes**:
  - Forgetting to set the `id` attribute on the datalist
  - Mismatching `list` attribute value with datalist `id`
  - Placing datalist inside elements that don't accept flow content
  - Using complex HTML inside datalist (only `<option>` elements allowed)
* **Performance**: Large datalists (1000+ options) may impact performance; consider dynamic loading
* **Styling limitations**: 
  - Cannot style the dropdown appearance directly with CSS
  - Appearance is controlled by the browser/operating system
  - Focus on styling the input element instead
* **Best practices**:
  - Place datalist near associated input for maintainability
  - Use descriptive `id` values that indicate purpose
  - Provide meaningful option values and labels
  - Consider user expectations for autocomplete behavior
  - Test across different browsers and devices
  - Implement graceful degradation for unsupported browsers

---
