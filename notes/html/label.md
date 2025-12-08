# `<label>`

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

The `<label>` element represents a caption for an item in a user interface, typically associated with a form control. It provides an accessible name and description for the control, enhancing usability for all users and critically improving accessibility for screen reader users and those who navigate via keyboard or other assistive technologies.

---

## Syntax and Variants

+ **Standard syntax**: `<label>...</label>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain text and inline elements
+ **No self-closing variant**: Must contain content
+ **Two association methods**: Implicit (wrapping) and explicit (using `for` attribute)

---

## Attributes

+ **Core attributes**:
  - `for` (optional): ID of the form control the label is associated with
  - `form` (optional): ID of the form the label belongs to (when not nested)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No deprecated attributes**: All original attributes remain supported

---

## Content Model

+ **Permitted content**: Phrasing content, but no interactive content descendants
+ **Allowed content**:
  - Text and character references
  - Phrasing elements: `<strong>`, `<em>`, `<span>`, etc.
  - Images and other inline elements
+ **Restricted content**: Cannot contain other interactive elements like `<a>`, `<button>`, or nested form controls
+ **Text focus**: Primarily intended for descriptive text content

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Directly before or after form controls in `<form>` elements
  - Within `<div>`, `<fieldset>`, or other form containers
  - As captions for checkboxes, radio buttons, and other inputs
+ **Form association**: Can be inside or outside associated forms using `form` attribute

---

## Behavior and Semantics

+ **Default display**: Inline element
+ **Default styling**:
  - `display: inline`
  - No inherent visual styling (appears as plain text)
  - Cursor may change to pointer when associated with clickable controls
+ **Interactive behavior**:
  - Clicking label focuses or activates associated form control
  - Supports keyboard navigation and screen reader focus
  - Provides hit area enlargement for small controls
+ **Semantic meaning**:
  - Represents a caption for a form control
  - Screen readers announce label text when control receives focus
  - Creates programmatic association between text and control
+ **Accessibility**: Essential for screen reader users to understand form control purpose

---

## Examples

**Basic label with input:**
```html
<label for="username">Username:</label>
<input type="text" id="username" name="username">
```

**Implicit label association (wrapping):**
```html
<label>
  Email Address:
  <input type="email" name="email" required>
</label>
```

**Label with checkbox:**
```html
<label>
  <input type="checkbox" name="subscribe" value="yes">
  Subscribe to newsletter
</label>
```

**Label with radio buttons:**
```html
<fieldset>
  <legend>Preferred Contact Method:</legend>
  
  <label>
    <input type="radio" name="contact" value="email" checked>
    Email
  </label>
  
  <label>
    <input type="radio" name="contact" value="phone">
    Phone
  </label>
  
  <label>
    <input type="radio" name="contact" value="mail">
    Postal Mail
  </label>
</fieldset>
```

**Styled labels with CSS:**
```html
<label for="styled-input" class="form-label">
  Your Name:
</label>
<input type="text" id="styled-input" name="name" class="form-input">

<style>
.form-label {
  display: block;
  margin-bottom: 8px;
  font-weight: 600;
  color: #333;
  cursor: pointer;
}

.form-input {
  width: 100%;
  max-width: 300px;
  padding: 8px 12px;
  border: 2px solid #ddd;
  border-radius: 4px;
  font-size: 16px;
}

.form-input:focus {
  border-color: #007bff;
  outline: none;
}
</style>
```

**Accessible label with ARIA:**
```html
<label for="password" id="password-label">
  Password
  <span class="required" aria-hidden="true">*</span>
</label>
<input type="password" 
       id="password" 
       name="password"
       aria-labelledby="password-label"
       aria-required="true"
       aria-describedby="password-help">
<div id="password-help" class="help-text">
  Must be at least 8 characters with one number and one special character.
</div>
```

**Label with complex content:**
```html
<label for="plan-select" class="complex-label">
  <span class="label-main">Subscription Plan</span>
  <span class="label-sub">Choose the plan that fits your needs</span>
</label>
<select id="plan-select" name="plan" class="form-select">
  <option value="basic">Basic Plan - $9/month</option>
  <option value="pro">Pro Plan - $19/month</option>
  <option value="enterprise">Enterprise Plan - $49/month</option>
</select>

<style>
.complex-label {
  display: block;
  margin-bottom: 8px;
  cursor: pointer;
}

.label-main {
  display: block;
  font-weight: 600;
  color: #333;
}

.label-sub {
  display: block;
  font-size: 0.875em;
  color: #666;
}
</style>
```

**Label for disabled control:**
```html
<label for="disabled-input" class="disabled-label">
  Disabled Field
</label>
<input type="text" id="disabled-input" name="disabled_field" disabled>

<style>
.disabled-label {
  color: #999;
  cursor: not-allowed;
}
</style>
```

**Label with icon:**
```html
<label for="search-input" class="icon-label">
  <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
    <path d="M15.5 14h-.79l-.28-.27C15.41 12.59 16 11.11 16 9.5 16 5.91 13.09 3 9.5 3S3 5.91 3 9.5 5.91 16 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
  </svg>
  Search Products
</label>
<input type="search" id="search-input" name="search" placeholder="Enter product name...">

<style>
.icon-label {
  display: flex;
  align-items: center;
  gap: 8px;
  font-weight: 600;
  margin-bottom: 8px;
  cursor: pointer;
}
</style>
```

**Label in a form layout:**
```html
<form class="form-layout">
  <div class="form-row">
    <label for="first-name" class="form-label">First Name:</label>
    <input type="text" id="first-name" name="first_name" class="form-input" required>
  </div>
  
  <div class="form-row">
    <label for="last-name" class="form-label">Last Name:</label>
    <input type="text" id="last-name" name="last_name" class="form-input" required>
  </div>
  
  <div class="form-row">
    <label for="email" class="form-label">Email Address:</label>
    <input type="email" id="email" name="email" class="form-input" required>
  </div>
</form>

<style>
.form-layout {
  max-width: 400px;
}

.form-row {
  display: flex;
  flex-direction: column;
  margin-bottom: 16px;
}

.form-label {
  margin-bottom: 4px;
  font-weight: 600;
}

.form-input {
  padding: 8px 12px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 16px;
}

@media (min-width: 768px) {
  .form-row {
    flex-direction: row;
    align-items: center;
  }
  
  .form-label {
    width: 120px;
    margin-bottom: 0;
    margin-right: 16px;
    text-align: right;
  }
  
  .form-input {
    flex: 1;
  }
}
</style>
```

**Label with error state:**
```html
<label for="email-input" class="error-label">
  Email Address
  <span class="error-indicator" aria-hidden="true">*</span>
</label>
<input type="email" 
       id="email-input" 
       name="email"
       class="error-input"
       aria-invalid="true"
       aria-describedby="email-error">
<div id="email-error" class="error-message" role="alert">
  Please enter a valid email address.
</div>

<style>
.error-label {
  color: #dc3545;
  font-weight: 600;
}

.error-input {
  border-color: #dc3545;
  background-color: #fff5f5;
}

.error-message {
  color: #dc3545;
  font-size: 0.875em;
  margin-top: 4px;
}

.error-indicator {
  color: #dc3545;
  margin-left: 4px;
}
</style>
```

**Label for textarea:**
```html
<label for="comments" class="textarea-label">
  Comments and Feedback
  <span class="optional">(optional)</span>
</label>
<textarea id="comments" name="comments" rows="4" placeholder="Share your thoughts..."></textarea>

<style>
.textarea-label {
  display: block;
  margin-bottom: 8px;
  font-weight: 600;
}

.optional {
  font-weight: normal;
  color: #666;
  font-size: 0.875em;
}
</style>
```

**Label with tooltip:**
```html
<label for="api-key" class="tooltip-label">
  API Key
  <button type="button" class="tooltip-trigger" aria-describedby="api-key-help">
    <span aria-hidden="true">ℹ️</span>
    <span class="visually-hidden">More information about API Key</span>
  </button>
</label>
<input type="text" id="api-key" name="api_key">
<div id="api-key-help" class="tooltip-content" role="tooltip">
  Your API key can be found in your account settings under Developer Options.
</div>

<style>
.tooltip-label {
  display: flex;
  align-items: center;
  gap: 8px;
}

.tooltip-trigger {
  background: none;
  border: none;
  cursor: help;
  font-size: 0.875em;
}

.tooltip-content {
  display: none;
  position: absolute;
  background: #333;
  color: white;
  padding: 8px 12px;
  border-radius: 4px;
  font-size: 0.875em;
  max-width: 200px;
}

.tooltip-trigger:focus + .tooltip-content,
.tooltip-trigger:hover + .tooltip-content {
  display: block;
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

**Label for custom control:**
```html
<label for="custom-slider" class="custom-label">
  Volume Level: <output id="volume-output">50</output>%
</label>
<input type="range" 
       id="custom-slider" 
       name="volume"
       min="0" 
       max="100" 
       value="50"
       class="custom-slider">

<script>
document.getElementById('custom-slider').addEventListener('input', function() {
  document.getElementById('volume-output').textContent = this.value;
});
</script>

<style>
.custom-label {
  display: block;
  margin-bottom: 8px;
  font-weight: 600;
}

.custom-slider {
  width: 100%;
  max-width: 300px;
}
</style>
```

**Multiple labels for one control (not recommended but possible):**
```html
<label for="shared-input" class="primary-label">Primary Label</label>
<span id="secondary-label" class="secondary-label">Secondary description</span>
<input type="text" 
       id="shared-input" 
       name="shared_field"
       aria-labelledby="primary-label secondary-label">

<style>
.primary-label {
  display: block;
  font-weight: 600;
  margin-bottom: 4px;
}

.secondary-label {
  display: block;
  font-size: 0.875em;
  color: #666;
  margin-bottom: 8px;
}
</style>
```

---

## Notes

* **Association methods**: 
  - Implicit: Wrap the form control within the `<label>` element
  - Explicit: Use `for` attribute matching the control's `id`
* **Accessibility requirements**:
  - Every form control should have an associated label
  - Labels should be descriptive and clear
  - Avoid using placeholder text as a replacement for labels
  - Ensure labels are programmatically associated with controls
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using labels without proper association (`for` attribute or wrapping)
  - Using non-descriptive label text like "Click here" or "Enter value"
  - Nesting interactive elements inside labels
  - Using placeholder text instead of proper labels
  - Forgetting labels for checkboxes and radio buttons
* **Click behavior**: Clicking a label focuses/activates the associated control
* **Styling flexibility**: Labels can be extensively styled while maintaining functionality
* **Mobile considerations**:
  - Labels provide larger touch targets for small controls
  - Ensure adequate spacing and readability on small screens
  - Test label association on touch devices
* **Best practices**:
  - Use clear, concise, and descriptive text
  - Place labels close to their associated controls
  - Use consistent labeling patterns throughout forms
  - Include required field indicators in labels when appropriate
  - Test with screen readers for accessibility

---
