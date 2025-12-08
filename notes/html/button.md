# `<button>`

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

The `<button>` element represents a clickable button that can be used to submit forms, trigger actions, or perform operations within a web page. It provides a more flexible and accessible alternative to `<input type="button">` by allowing rich content within the button, including text, images, and other HTML elements.

---

## Syntax and Variants

+ **Standard syntax**: `<button>...</button>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain text, images, and other HTML content
+ **No self-closing variant**: Must contain content
+ **Type-driven**: Behavior determined by `type` attribute

---

## Attributes

+ **Core attributes**:
  - `type` (optional): Button type (`submit`, `reset`, `button`) - defaults to `submit` in forms
  - `name` (optional): Name for form submission and scripting
  - `value` (optional): Value submitted with form data
  - `disabled` (optional): Disables the button (boolean)
  - `autofocus` (optional): Automatically focus on page load (boolean)
  - `form` (optional): Associates button with a form (by form ID)
  - `formaction` (optional): Overrides form's `action` attribute
  - `formenctype` (optional): Overrides form's `enctype` attribute
  - `formmethod` (optional): Overrides form's `method` attribute
  - `formnovalidate` (optional): Bypasses form validation (boolean)
  - `formtarget` (optional): Overrides form's `target` attribute

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No deprecated attributes**: All original attributes remain supported

---

## Content Model

+ **Permitted content**: Phrasing content, but no interactive content descendants
+ **Allowed content**:
  - Text and character references
  - Images, spans, emphasis elements
  - Line breaks and formatting elements
+ **Restricted content**: Cannot contain other buttons, links, or form elements
+ **Rich content**: Supports complex content unlike `<input type="button">`

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within `<form>` elements for submission/reset
  - Within `<div>`, `<header>`, `<footer>` for general actions
  - In navigation, toolbars, and interactive components
+ **Form association**: Can be inside or outside associated forms

---

## Behavior and Semantics

+ **Default display**: Inline-block element
+ **Default styling**:
  - `display: inline-block`
  - Browser-dependent appearance (typically 3D-rendered button)
  - System font and colors
  - Cursor changes to pointer on hover
+ **Interactive behavior**:
  - Clickable/tappable interface element
  - Supports focus, hover, active states
  - Keyboard accessible (Space/Enter keys)
  - Can submit forms or trigger JavaScript actions
+ **Semantic meaning**:
  - Represents a clickable button control
  - Screen readers announce as "button" and read button content
  - Provides clear call-to-action for users
+ **Accessibility**: Naturally accessible when properly implemented with semantic content

---

## Examples

**Basic button with text:**
```html
<button type="button">Click Me</button>
```

**Form submission buttons:**
```html
<form action="/submit" method="post">
  <!-- Form fields here -->
  
  <button type="submit">Save Changes</button>
  <button type="reset">Reset Form</button>
  <button type="button" onclick="previewForm()">Preview</button>
</form>
```

**Button with icon and text:**
```html
<button type="button" class="icon-button">
  <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
    <path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z"/>
  </svg>
  Add Item
</button>

<style>
.icon-button {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  background: white;
  cursor: pointer;
}

.icon-button:hover {
  background: #f5f5f5;
}
</style>
```

**Accessible button with ARIA:**
```html
<button type="button" 
        class="accessible-btn"
        aria-label="Close dialog window"
        aria-describedby="close-help">
  <span aria-hidden="true">×</span>
</button>
<span id="close-help" class="visually-hidden">Closes the current dialog and returns to main content</span>

<style>
.accessible-btn {
  width: 40px;
  height: 40px;
  border: none;
  background: #f0f0f0;
  border-radius: 50%;
  font-size: 20px;
  cursor: pointer;
}

.accessible-btn:hover {
  background: #e0e0e0;
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

**Button with loading state:**
```html
<button type="button" id="load-data" class="btn-loading" onclick="loadData()">
  <span class="btn-text">Load Data</span>
  <span class="btn-spinner" aria-hidden="true"></span>
</button>

<style>
.btn-loading {
  position: relative;
}

.btn-spinner {
  display: none;
  width: 16px;
  height: 16px;
  border: 2px solid transparent;
  border-top: 2px solid currentColor;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

.btn-loading.loading .btn-text {
  opacity: 0;
}

.btn-loading.loading .btn-spinner {
  display: inline-block;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>

<script>
function loadData() {
  const button = document.getElementById('load-data');
  button.classList.add('loading');
  button.disabled = true;
  
  // Simulate API call
  setTimeout(() => {
    button.classList.remove('loading');
    button.disabled = false;
    alert('Data loaded!');
  }, 2000);
}
</script>
```

**Button group with different styles:**
```html
<div class="button-group">
  <button type="button" class="btn-primary">Primary Action</button>
  <button type="button" class="btn-secondary">Secondary Action</button>
  <button type="button" class="btn-danger">Dangerous Action</button>
  <button type="button" class="btn-outline">Outline Button</button>
</div>

<style>
.button-group {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}

.btn-primary {
  background: #007bff;
  color: white;
  border: none;
  padding: 12px 24px;
  border-radius: 6px;
  cursor: pointer;
}

.btn-secondary {
  background: #6c757d;
  color: white;
  border: none;
  padding: 12px 24px;
  border-radius: 6px;
  cursor: pointer;
}

.btn-danger {
  background: #dc3545;
  color: white;
  border: none;
  padding: 12px 24px;
  border-radius: 6px;
  cursor: pointer;
}

.btn-outline {
  background: transparent;
  color: #007bff;
  border: 2px solid #007bff;
  padding: 10px 22px;
  border-radius: 6px;
  cursor: pointer;
}

/* Hover states */
.btn-primary:hover { background: #0056b3; }
.btn-secondary:hover { background: #545b62; }
.btn-danger:hover { background: #c82333; }
.btn-outline:hover { background: #007bff; color: white; }

/* Focus states */
button:focus {
  outline: 2px solid #0056b3;
  outline-offset: 2px;
}
</style>
```

**Toggle button with ARIA:**
```html
<button type="button" 
        id="toggle-btn"
        class="toggle-button"
        aria-pressed="false"
        onclick="toggleButton(this)">
  <span class="toggle-icon" aria-hidden="true">🔔</span>
  Notifications: Off
</button>

<style>
.toggle-button {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 10px 16px;
  border: 2px solid #ddd;
  background: white;
  border-radius: 25px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.toggle-button[aria-pressed="true"] {
  background: #4CAF50;
  color: white;
  border-color: #4CAF50;
}

.toggle-icon {
  font-size: 1.2em;
}
</style>

<script>
function toggleButton(button) {
  const isPressed = button.getAttribute('aria-pressed') === 'true';
  button.setAttribute('aria-pressed', !isPressed);
  button.querySelector('.toggle-icon').textContent = !isPressed ? '🔔' : '🔕';
  button.lastChild.textContent = `Notifications: ${!isPressed ? 'On' : 'Off'}`;
}
</script>
```

**Button with confirmation dialog:**
```html
<button type="button" 
        class="btn-danger"
        onclick="confirmAction('Are you sure you want to delete this item?', deleteItem)">
  Delete Item
</button>

<script>
function confirmAction(message, callback) {
  if (confirm(message)) {
    callback();
  }
}

function deleteItem() {
  // Perform deletion logic
  console.log('Item deleted');
  alert('Item has been deleted successfully.');
}
</script>
```

**Button with form override attributes:**
```html
<form id="user-form" action="/save" method="post">
  <input type="text" name="username" placeholder="Username" required>
  
  <button type="submit">Save Normally</button>
  
  <button type="submit"
          formaction="/save-draft"
          formmethod="get"
          formnovalidate>
    Save as Draft
  </button>
  
  <button type="submit"
          formaction="/preview"
          formtarget="_blank">
    Preview in New Tab
  </button>
</form>
```

**Button with complex content:**
```html
<button type="button" class="feature-button">
  <div class="button-content">
    <div class="button-icon">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
        <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
      </svg>
    </div>
    <div class="button-text">
      <strong>Premium Feature</strong>
      <span>Unlock advanced capabilities</span>
    </div>
    <div class="button-badge">NEW</div>
  </div>
</button>

<style>
.feature-button {
  width: 280px;
  padding: 16px;
  border: 2px solid #e0e0e0;
  background: white;
  border-radius: 12px;
  cursor: pointer;
  text-align: left;
  transition: all 0.3s ease;
}

.feature-button:hover {
  border-color: #007bff;
  box-shadow: 0 4px 12px rgba(0, 123, 255, 0.15);
}

.button-content {
  display: flex;
  align-items: center;
  gap: 12px;
}

.button-icon {
  color: #007bff;
  flex-shrink: 0;
}

.button-text {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.button-text strong {
  font-size: 1.1em;
  color: #333;
}

.button-text span {
  font-size: 0.9em;
  color: #666;
}

.button-badge {
  background: #ff4757;
  color: white;
  padding: 2px 8px;
  border-radius: 12px;
  font-size: 0.8em;
  font-weight: bold;
}
</style>
```

**Disabled button states:**
```html
<div class="button-examples">
  <button type="button" disabled>Permanently Disabled</button>
  
  <button type="button" id="conditional-btn">Conditionally Enabled</button>
  
  <button type="button" class="btn-with-tooltip" disabled 
          aria-describedby="disabled-reason">
    Disabled with Reason
  </button>
  <span id="disabled-reason" class="tooltip">This feature requires premium subscription</span>
</div>

<style>
.button-examples {
  display: flex;
  flex-direction: column;
  gap: 12px;
  max-width: 300px;
}

button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.tooltip {
  font-size: 0.875em;
  color: #666;
  margin-top: -8px;
}
</style>

<script>
// Conditional enabling example
const conditionalBtn = document.getElementById('conditional-btn');
let isEnabled = false;

conditionalBtn.addEventListener('click', function() {
  if (!isEnabled) {
    alert('Button is now enabled!');
    isEnabled = true;
    this.textContent = 'Click Me!';
  } else {
    alert('Button clicked!');
  }
});
</script>
```

**Button with keyboard shortcuts:**
```html
<button type="button" 
        id="shortcut-btn"
        class="shortcut-button"
        accesskey="s"
        aria-keyshortcuts="Alt+S">
  Save Document
  <kbd class="shortcut-hint">Alt+S</kbd>
</button>

<style>
.shortcut-button {
  position: relative;
  padding: 12px 48px 12px 16px;
  border: 1px solid #ccc;
  background: white;
  border-radius: 4px;
  cursor: pointer;
}

.shortcut-hint {
  position: absolute;
  right: 8px;
  top: 50%;
  transform: translateY(-50%);
  padding: 2px 6px;
  background: #f0f0f0;
  border: 1px solid #ccc;
  border-radius: 3px;
  font-size: 0.8em;
  color: #666;
}
</style>

<script>
// Add keyboard event listener
document.addEventListener('keydown', function(event) {
  if (event.altKey && event.key === 's') {
    event.preventDefault();
    document.getElementById('shortcut-btn').click();
  }
});
</script>
```

---

## Notes

* **Type attribute importance**: Always specify `type` attribute to prevent unexpected form submissions
* **Accessibility best practices**:
  - Use descriptive text content that clearly indicates the button's purpose
  - Provide ARIA labels for icon-only buttons
  - Ensure adequate color contrast and focus indicators
  - Maintain sufficient touch target size (minimum 44×44px)
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using `<div>` or `<span>` instead of `<button>` for interactive elements
  - Forgetting to specify `type="button"` for non-submit buttons
  - Using images without proper alt text in buttons
  - Creating buttons that are too small for touch interfaces
  - Overlooking focus management in dynamic interfaces
* **CSS styling**:
  - Buttons can be extensively styled while maintaining accessibility
  - Use `:focus`, `:hover`, `:active` pseudo-classes for interactive states
  - Consider `cursor: pointer` for better UX indication
* **Mobile considerations**:
  - Ensure adequate touch target size
  - Consider hover states on touch devices
  - Test with various screen readers and assistive technologies
* **Performance**: 
  - Buttons are lightweight and have minimal performance impact
  - Complex CSS animations may affect performance on low-end devices
* **Security**: 
  - Buttons that trigger sensitive actions should have confirmation dialogs
  - Validate all form submissions server-side regardless of button type

---
