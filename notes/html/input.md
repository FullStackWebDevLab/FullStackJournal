# `<input>`

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

The `<input>` element creates an interactive control within a web form, allowing users to enter data. It is the most versatile form control, capable of rendering various types of input fields based on its `type` attribute, from simple text fields to complex date pickers and file upload controls.

---

## Syntax and Variants

+ **Standard syntax**: `<input>` (void element)
+ **Void element**: No closing tag required
+ **Self-closing variants**:
  - HTML5: `<input>`
  - XHTML: `<input />` or `<input></input>`
+ **Type-driven**: Behavior and appearance determined by `type` attribute

---

## Attributes

+ **Core attributes**:
  - `type` (optional): Input type (`text`, `password`, `email`, `number`, etc.)
  - `name` (optional): Name for form submission and scripting
  - `value` (optional): Initial value of the input
  - `placeholder` (optional): Hint text displayed when input is empty
  - `required` (optional): Marks field as mandatory (boolean)
  - `disabled` (optional): Disables the input (boolean)
  - `readonly` (optional): Makes input read-only (boolean)
  - `autocomplete` (optional): Enable/disable autocomplete (`on`, `off`)
  - `autofocus` (optional): Automatically focus on page load (boolean)

+ **Type-specific attributes**:
  - `min`, `max`, `step` (for numeric and date types)
  - `pattern` (for text validation)
  - `multiple` (for file and email inputs)
  - `accept` (for file inputs)
  - `src`, `alt` (for image inputs)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Deprecated attributes**:
  - `align` (use CSS instead)

---

## Content Model

+ **Empty element**: Must not contain any content
+ **No children permitted**: Cannot contain text or other elements
+ **Void element category**: Defined as having no content model in HTML specification
+ **Self-contained**: All data and state managed through attributes

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

+ **Default display**: Inline-level replaced element
+ **Default styling**:
  - `display: inline-block`
  - Varies significantly by `type` attribute
  - Browser-dependent appearance
+ **Interactive behavior**:
  - Accepts user input based on type
  - Supports focus, blur, and change events
  - Provides built-in validation for many types
+ **Semantic meaning**:
  - Represents a form input control
  - Screen readers announce based on type and attributes
  - Provides context for user data entry
+ **Accessibility**: Critical to associate with labels and provide proper attributes

---

## Examples

**Basic text input:**
```html
<label for="username">Username:</label>
<input type="text" id="username" name="username" 
       placeholder="Enter your username" required>
```

**Email input with validation:**
```html
<label for="email">Email Address:</label>
<input type="email" id="email" name="email" 
       placeholder="user@example.com" 
       required
       aria-describedby="email-help">
<small id="email-help">We'll never share your email with anyone else.</small>
```

**Password input:**
```html
<label for="password">Password:</label>
<input type="password" id="password" name="password" 
       minlength="8" required
       aria-describedby="password-requirements">
<small id="password-requirements">Must be at least 8 characters long.</small>
```

**Number input with constraints:**
```html
<label for="quantity">Quantity:</label>
<input type="number" id="quantity" name="quantity" 
       min="1" max="100" step="1" value="1"
       aria-label="Number of items to purchase">
```

**Date and time inputs:**
```html
<div class="form-group">
  <label for="birthdate">Birth Date:</label>
  <input type="date" id="birthdate" name="birthdate" 
         min="1900-01-01" max="2024-12-31">
</div>

<div class="form-group">
  <label for="appointment">Appointment Time:</label>
  <input type="datetime-local" id="appointment" name="appointment">
</div>

<div class="form-group">
  <label for="reminder">Reminder:</label>
  <input type="time" id="reminder" name="reminder" value="09:00">
</div>
```

**File upload input:**
```html
<label for="document-upload">Upload Document:</label>
<input type="file" id="document-upload" name="document" 
       accept=".pdf,.doc,.docx,.txt"
       aria-describedby="file-help">
<small id="file-help">Accepted formats: PDF, DOC, DOCX, TXT (Max: 10MB)</small>
```

**Range input (slider):**
```html
<label for="volume">Volume:</label>
<input type="range" id="volume" name="volume" 
       min="0" max="100" step="10" value="50"
       aria-valuetext="50 percent">
<output for="volume" id="volume-output">50%</output>

<script>
document.getElementById('volume').addEventListener('input', function() {
  document.getElementById('volume-output').textContent = this.value + '%';
});
</script>
```

**Color picker:**
```html
<label for="fav-color">Favorite Color:</label>
<input type="color" id="fav-color" name="fav_color" value="#3498db">
```

**Search input:**
```html
<label for="site-search" class="visually-hidden">Search the site</label>
<input type="search" id="site-search" name="q" 
       placeholder="Search..." 
       aria-label="Search through site content">
<button type="submit">Search</button>
```

**URL input:**
```html
<label for="website">Website URL:</label>
<input type="url" id="website" name="website" 
       placeholder="https://example.com"
       pattern="https://.*" 
       aria-describedby="url-help">
<small id="url-help">Must start with https://</small>
```

**Telephone input:**
```html
<label for="phone">Phone Number:</label>
<input type="tel" id="phone" name="phone" 
       pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}"
       placeholder="123-456-7890"
       aria-describedby="phone-format">
<small id="phone-format">Format: 123-456-7890</small>
```

**Checkbox and radio inputs:**
```html
<fieldset>
  <legend>Notification Preferences</legend>
  
  <div class="checkbox-group">
    <label>
      <input type="checkbox" name="notifications" value="email" checked>
      Email Notifications
    </label>
    <label>
      <input type="checkbox" name="notifications" value="sms">
      SMS Notifications
    </label>
    <label>
      <input type="checkbox" name="notifications" value="push">
      Push Notifications
    </label>
  </div>
</fieldset>

<fieldset>
  <legend>Preferred Contact Method</legend>
  
  <div class="radio-group">
    <label>
      <input type="radio" name="contact_method" value="email" checked>
      Email
    </label>
    <label>
      <input type="radio" name="contact_method" value="phone">
      Phone
    </label>
    <label>
      <input type="radio" name="contact_method" value="mail">
      Postal Mail
    </label>
  </div>
</fieldset>
```

**Hidden input:**
```html
<input type="hidden" name="user_id" value="12345">
<input type="hidden" name="csrf_token" value="abc123def456">
```

**Button inputs:**
```html
<!-- Submit button -->
<input type="submit" value="Save Changes">

<!-- Reset button -->
<input type="reset" value="Reset Form">

<!-- Image button -->
<input type="image" src="submit-button.png" alt="Submit Form" width="100" height="40">

<!-- Regular button -->
<input type="button" value="Click Me" onclick="handleClick()">
```

**Input with datalist:**
```html
<label for="browser">Choose your browser:</label>
<input type="text" id="browser" name="browser" list="browsers">
<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
  <option value="Edge">
  <option value="Opera">
</datalist>
```

**Advanced input with multiple attributes:**
```html
<label for="product-code">Product Code:</label>
<input type="text" 
       id="product-code" 
       name="product_code" 
       class="form-control"
       placeholder="Enter product code"
       pattern="[A-Z]{2}-[0-9]{4}"
       title="Product code format: AA-1234"
       minlength="7"
       maxlength="7"
       required
       autocomplete="off"
       autocapitalize="characters"
       aria-describedby="code-help code-error"
       data-validation="product-code">
<small id="code-help">Format: AA-1234 (2 letters, hyphen, 4 numbers)</small>
<span id="code-error" class="error-message" aria-live="polite"></span>
```

**Accessible input with ARIA:**
```html
<div class="form-group">
  <span id="salary-label" class="label">Desired Salary</span>
  
  <input type="number" 
         id="salary" 
         name="salary"
         min="30000" 
         max="200000" 
         step="5000"
         aria-labelledby="salary-label"
         aria-required="true"
         aria-describedby="salary-constraints salary-error"
         aria-invalid="false">
         
  <span id="salary-constraints" class="help-text">
    Must be between $30,000 and $200,000 in increments of $5,000
  </span>
  
  <span id="salary-error" class="error-text" aria-live="polite"></span>
</div>

<script>
document.getElementById('salary').addEventListener('blur', function() {
  const errorElement = document.getElementById('salary-error');
  const value = parseInt(this.value);
  
  if (value < 30000 || value > 200000) {
    this.setAttribute('aria-invalid', 'true');
    errorElement.textContent = 'Salary must be between $30,000 and $200,000';
  } else {
    this.setAttribute('aria-invalid', 'false');
    errorElement.textContent = '';
  }
});
</script>
```

**Input with JavaScript validation:**
```html
<label for="username">Username:</label>
<input type="text" 
       id="username" 
       name="username" 
       pattern="[a-zA-Z0-9_]{3,20}"
       required
       aria-describedby="username-feedback">
<span id="username-feedback" class="feedback" aria-live="polite"></span>

<script>
const usernameInput = document.getElementById('username');
const feedback = document.getElementById('username-feedback');

usernameInput.addEventListener('input', function() {
  const value = this.value;
  
  if (value.length === 0) {
    feedback.textContent = '';
    this.setAttribute('aria-invalid', 'false');
  } else if (value.length < 3) {
    feedback.textContent = 'Username must be at least 3 characters';
    feedback.className = 'feedback error';
    this.setAttribute('aria-invalid', 'true');
  } else if (!/^[a-zA-Z0-9_]+$/.test(value)) {
    feedback.textContent = 'Username can only contain letters, numbers, and underscores';
    feedback.className = 'feedback error';
    this.setAttribute('aria-invalid', 'true');
  } else {
    feedback.textContent = 'Username is available';
    feedback.className = 'feedback success';
    this.setAttribute('aria-invalid', 'false');
  }
});
</script>
```

---

## Notes

* **Type attribute default**: If `type` is omitted or invalid, defaults to `text`
* **Accessibility requirements**:
  - Always associate with `<label>` elements using `for` and `id`
  - Use `aria-*` attributes for complex validation and states
  - Ensure proper focus management and keyboard navigation
  - Provide clear error messages and instructions
* **Browser support**: 
  - Basic types supported universally
  - Newer HTML5 types have varying support (provide fallbacks when needed)
  - Custom styling may be needed for consistent appearance
* **Security considerations**:
  - Client-side validation is for UX only; always validate server-side
  - Sanitize all user input to prevent XSS and injection attacks
  - Use appropriate input types for data (e.g., `email`, `url`)
* **Common mistakes**:
  - Forgetting `name` attribute (required for form submission)
  - Not providing proper labels for accessibility
  - Relying solely on client-side validation
  - Using inappropriate input types for the data
  - Overlooking mobile user experience
* **Mobile optimization**:
  - Use appropriate input types for virtual keyboards
  - Ensure adequate touch target sizes (minimum 44×44px)
  - Test with various mobile devices and screen sizes
* **Performance**: 
  - Complex validation patterns can impact performance
  - Consider debouncing real-time validation for text inputs
  - Use native validation when possible for better performance
* **Progressive enhancement**: Ensure forms work without JavaScript when possible

---
