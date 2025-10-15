# `<fieldset>`

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

The `<fieldset>` element groups several form controls and labels within a web form, creating a semantic and structural unit. It provides visual organization by drawing a border around related form elements and enables logical grouping for accessibility tools. When combined with the `<legend>` element, it offers a programmatically determinable label for the entire group, enhancing usability for screen reader users and improving overall form comprehension.

---

## Syntax and Variants

+ **Standard syntax**: `<fieldset>...</fieldset>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain form controls and other HTML elements
+ **No self-closing variant**: Must have proper opening and closing tags
+ **Optional legend**: May contain a single `<legend>` element as the first child

---

## Attributes

+ **Core attributes**:
  - `disabled` (optional): Disables all form controls within the fieldset
  - `form` (optional): ID of the form the fieldset belongs to (when not nested)
  - `name` (optional): Name of the fieldset for scripting purposes

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No deprecated attributes**: All original attributes remain supported

---

## Content Model

+ **Permitted content**: Flow content, with exactly zero or one `<legend>` element as the first child
+ **Allowed content**:
  - Form controls: `<input>`, `<select>`, `<textarea>`, `<button>`
  - Structural elements: `<div>`, `<p>`, `<span>`
  - Other form grouping elements: additional `<fieldset>` elements
  - Text content and phrasing elements
+ **Required structure**: If present, `<legend>` must be the first direct child
+ **No restrictions** on the number of form controls within a fieldset

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<form>` elements as direct children
  - Within other `<fieldset>` elements for nested groupings
  - Within `<div>` or other container elements in complex forms
+ **Form association**: Can be inside or outside associated forms using `form` attribute
+ **No usage limits**: Multiple fieldsets can be used within a single form

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - `min-inline-size: min-content`
  - Border: 2px groove (typically gray)
  - Padding and margins applied by user agent stylesheet
+ **Interactive behavior**:
  - `disabled` attribute propagates to all contained form controls
  - Creates a semantic group for assistive technologies
  - Provides visual grouping for sighted users
+ **Semantic meaning**:
  - Represents a set of form controls as a logical unit
  - Screen readers announce the legend text when entering the group
  - Creates programmatic relationship between related controls
+ **Accessibility**: Essential for grouping related form controls and providing context

---

## Examples

**Basic fieldset with legend:**
```html
<form>
  <fieldset>
    <legend>Personal Information</legend>
    
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email">
  </fieldset>
</form>
```

**Fieldset with radio buttons:**
```html
<form>
  <fieldset>
    <legend>Shipping Method</legend>
    
    <label>
      <input type="radio" name="shipping" value="standard" checked>
      Standard (5-7 business days)
    </label>
    
    <label>
      <input type="radio" name="shipping" value="express">
      Express (2-3 business days)
    </label>
    
    <label>
      <input type="radio" name="shipping" value="overnight">
      Overnight (1 business day)
    </label>
  </fieldset>
</form>
```

**Disabled fieldset:**
```html
<form>
  <fieldset disabled>
    <legend>Billing Information (Disabled until shipping method selected)</legend>
    
    <label for="card">Credit Card Number:</label>
    <input type="text" id="card" name="card">
    
    <label for="expiry">Expiration Date:</label>
    <input type="text" id="expiry" name="expiry">
  </fieldset>
</form>
```

**Nested fieldsets:**
```html
<form>
  <fieldset>
    <legend>Account Settings</legend>
    
    <fieldset>
      <legend>Privacy Settings</legend>
      
      <label>
        <input type="checkbox" name="profile_public">
        Make profile public
      </label>
      
      <label>
        <input type="checkbox" name="email_public">
        Show email address
      </label>
    </fieldset>
    
    <fieldset>
      <legend>Notification Preferences</legend>
      
      <label>
        <input type="checkbox" name="email_notifications">
        Email notifications
      </label>
      
      <label>
        <input type="checkbox" name="push_notifications">
        Push notifications
      </label>
    </fieldset>
  </fieldset>
</form>
```

**Styled fieldset with CSS:**
```html
<form>
  <fieldset class="modern-fieldset">
    <legend class="modern-legend">Contact Preferences</legend>
    
    <div class="form-group">
      <label>
        <input type="checkbox" name="contact_email">
        Email
      </label>
    </div>
    
    <div class="form-group">
      <label>
        <input type="checkbox" name="contact_phone">
        Phone
      </label>
    </div>
    
    <div class="form-group">
      <label>
        <input type="checkbox" name="contact_sms">
        SMS
      </label>
    </div>
  </fieldset>
</form>

<style>
.modern-fieldset {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 20px;
  margin: 16px 0;
  background-color: #fafafa;
}

.modern-legend {
  font-weight: 600;
  color: #333;
  padding: 0 12px;
  margin-left: -12px;
  background-color: white;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
}

.form-group {
  margin-bottom: 12px;
}

.form-group label {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
}
</style>
```

**Fieldset with complex layout:**
```html
<form>
  <fieldset class="address-fieldset">
    <legend>Shipping Address</legend>
    
    <div class="form-row">
      <div class="form-group">
        <label for="street">Street Address</label>
        <input type="text" id="street" name="street" required>
      </div>
    </div>
    
    <div class="form-row">
      <div class="form-group">
        <label for="city">City</label>
        <input type="text" id="city" name="city" required>
      </div>
      
      <div class="form-group">
        <label for="state">State</label>
        <select id="state" name="state" required>
          <option value="">Select State</option>
          <option value="CA">California</option>
          <option value="NY">New York</option>
          <option value="TX">Texas</option>
        </select>
      </div>
      
      <div class="form-group">
        <label for="zip">ZIP Code</label>
        <input type="text" id="zip" name="zip" required pattern="[0-9]{5}">
      </div>
    </div>
  </fieldset>
</form>

<style>
.address-fieldset {
  border: none;
  padding: 0;
  margin: 0 0 24px 0;
}

.address-fieldset legend {
  font-size: 1.25em;
  font-weight: 600;
  margin-bottom: 16px;
  padding: 0;
  width: 100%;
  border-bottom: 2px solid #007bff;
  padding-bottom: 8px;
}

.form-row {
  display: flex;
  gap: 16px;
  margin-bottom: 16px;
  flex-wrap: wrap;
}

.form-group {
  flex: 1;
  min-width: 200px;
}

.form-group label {
  display: block;
  margin-bottom: 4px;
  font-weight: 500;
}

.form-group input,
.form-group select {
  width: 100%;
  padding: 8px 12px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 16px;
}
</style>
```

**Fieldset with ARIA enhancements:**
```html
<form>
  <fieldset aria-describedby="payment-help">
    <legend>
      Payment Information
      <span class="required" aria-hidden="true">*</span>
    </legend>
    
    <div id="payment-help" class="help-text">
      All payment fields are required for transaction processing.
    </div>
    
    <div class="form-group">
      <label for="card-type">Card Type</label>
      <select id="card-type" name="card_type" required>
        <option value="">Select Card Type</option>
        <option value="visa">Visa</option>
        <option value="mastercard">MasterCard</option>
        <option value="amex">American Express</option>
      </select>
    </div>
    
    <div class="form-group">
      <label for="card-number">Card Number</label>
      <input type="text" 
             id="card-number" 
             name="card_number" 
             required 
             pattern="[0-9]{13,16}"
             aria-describedby="card-number-help">
      <div id="card-number-help" class="help-text">
        Enter 13-16 digit card number without spaces.
      </div>
    </div>
  </fieldset>
</form>

<style>
.help-text {
  font-size: 0.875em;
  color: #666;
  margin-top: 4px;
}

.required {
  color: #dc3545;
  margin-left: 4px;
}
</style>
```

**Fieldset for agreement sections:**
```html
<form>
  <fieldset class="agreement-fieldset">
    <legend>Terms and Conditions</legend>
    
    <div class="agreement-content">
      <p>By creating an account, you agree to our Terms of Service and Privacy Policy.</p>
      
      <div class="scrollable-terms">
        <h4>Terms of Service</h4>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua...</p>
        <!-- More terms content -->
      </div>
    </div>
    
    <div class="agreement-actions">
      <label>
        <input type="checkbox" name="agree_terms" required>
        I have read and agree to the Terms of Service
      </label>
      
      <label>
        <input type="checkbox" name="agree_privacy" required>
        I have read and agree to the Privacy Policy
      </label>
    </div>
  </fieldset>
</form>

<style>
.agreement-fieldset {
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 20px;
}

.agreement-content {
  margin-bottom: 20px;
}

.scrollable-terms {
  max-height: 200px;
  overflow-y: auto;
  border: 1px solid #eee;
  padding: 12px;
  margin: 12px 0;
  background-color: #f9f9f9;
}

.agreement-actions label {
  display: block;
  margin-bottom: 12px;
  font-weight: 500;
}
</style>
```

**Fieldset with dynamic content:**
```html
<form>
  <fieldset id="dynamic-fieldset">
    <legend>Product Options</legend>
    
    <div class="option-group">
      <label for="product-type">Product Type:</label>
      <select id="product-type" name="product_type">
        <option value="physical">Physical Product</option>
        <option value="digital">Digital Download</option>
        <option value="service">Service</option>
      </select>
    </div>
    
    <!-- Dynamic content will be inserted here -->
    <div id="dynamic-content"></div>
  </fieldset>
</form>

<script>
document.getElementById('product-type').addEventListener('change', function() {
  const contentDiv = document.getElementById('dynamic-content');
  const fieldset = document.getElementById('dynamic-fieldset');
  
  // Clear previous dynamic content
  contentDiv.innerHTML = '';
  
  switch(this.value) {
    case 'physical':
      contentDiv.innerHTML = `
        <div class="form-group">
          <label for="weight">Weight (kg):</label>
          <input type="number" id="weight" name="weight" step="0.1" min="0">
        </div>
        <div class="form-group">
          <label for="dimensions">Dimensions (L×W×H):</label>
          <input type="text" id="dimensions" name="dimensions" placeholder="e.g., 10×5×2">
        </div>
      `;
      break;
      
    case 'digital':
      contentDiv.innerHTML = `
        <div class="form-group">
          <label for="file-size">File Size (MB):</label>
          <input type="number" id="file-size" name="file_size" min="0">
        </div>
        <div class="form-group">
          <label for="download-limit">Download Limit:</label>
          <input type="number" id="download-limit" name="download_limit" min="1" value="1">
        </div>
      `;
      break;
      
    case 'service':
      contentDiv.innerHTML = `
        <div class="form-group">
          <label for="duration">Service Duration (hours):</label>
          <input type="number" id="duration" name="duration" min="1" value="1">
        </div>
        <div class="form-group">
          <label for="location">Service Location:</label>
          <select id="location" name="location">
            <option value="remote">Remote</option>
            <option value="onsite">On-site</option>
          </select>
        </div>
      `;
      break;
  }
});
</script>
```

**Fieldset with validation state:**
```html
<form>
  <fieldset class="validation-fieldset" id="billing-fieldset">
    <legend>Billing Information</legend>
    
    <div class="form-group">
      <label for="billing-name">Full Name</label>
      <input type="text" id="billing-name" name="billing_name" required>
    </div>
    
    <div class="form-group">
      <label for="billing-address">Billing Address</label>
      <textarea id="billing-address" name="billing_address" rows="3" required></textarea>
    </div>
  </fieldset>
</form>

<script>
// Example validation feedback
document.addEventListener('DOMContentLoaded', function() {
  const fieldset = document.getElementById('billing-fieldset');
  const inputs = fieldset.querySelectorAll('input, textarea');
  
  inputs.forEach(input => {
    input.addEventListener('blur', function() {
      if (!this.checkValidity()) {
        fieldset.classList.add('invalid');
        fieldset.classList.remove('valid');
      } else {
        fieldset.classList.add('valid');
        fieldset.classList.remove('invalid');
      }
    });
  });
});
</script>

<style>
.validation-fieldset {
  border: 2px solid #e0e0e0;
  transition: border-color 0.3s ease;
}

.validation-fieldset.valid {
  border-color: #28a745;
}

.validation-fieldset.invalid {
  border-color: #dc3545;
}

.validation-fieldset.valid legend {
  color: #28a745;
}

.validation-fieldset.invalid legend {
  color: #dc3545;
}
</style>
```

**Fieldset without border:**
```html
<form>
  <fieldset class="borderless-fieldset">
    <legend class="sr-only">Account Preferences</legend>
    
    <h3>Account Preferences</h3>
    
    <div class="preference-group">
      <label>
        <input type="checkbox" name="newsletter" checked>
        Receive monthly newsletter
      </label>
    </div>
    
    <div class="preference-group">
      <label>
        <input type="checkbox" name="product_updates">
        Receive product update notifications
      </label>
    </div>
    
    <div class="preference-group">
      <label>
        <input type="checkbox" name="marketing_emails">
        Receive marketing emails
      </label>
    </div>
  </fieldset>
</form>

<style>
.borderless-fieldset {
  border: none;
  padding: 0;
  margin: 0;
}

.borderless-fieldset legend {
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

.borderless-fieldset h3 {
  margin-bottom: 16px;
  color: #333;
}

.preference-group {
  margin-bottom: 12px;
}

.preference-group label {
  display: flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
}
</style>
```

---

## Notes

* **Legend placement**: The `<legend>` element must be the first child of `<fieldset>` to be valid
* **Disabled behavior**: When a fieldset is disabled, all form controls within it are automatically disabled
* **Styling considerations**:
  - Browser default styles for fieldset borders and legends can vary
  - Legends are typically positioned overlapping the fieldset border
  - Custom styling often requires resetting default browser styles
* **Accessibility benefits**:
  - Screen readers announce the legend when users enter the fieldset
  - Provides contextual information for groups of related controls
  - Helps users understand the relationship between form elements
* **Browser support**: Universally supported across all modern browsers
* **Common mistakes**:
  - Using fieldsets for visual grouping without semantic purpose
  - Placing `<legend>` elements after other content in the fieldset
  - Overusing nested fieldsets, which can complicate form structure
  - Forgetting to associate fieldsets with forms when using the `form` attribute
* **Best practices**:
  - Use fieldsets to group related form controls logically
  - Always include a descriptive `<legend>` for accessibility
  - Consider using fieldsets for radio button and checkbox groups
  - Use the `disabled` attribute judiciously for conditional form sections
  - Test fieldset and legend announcements with screen readers
* **Mobile considerations**:
  - Ensure adequate spacing within fieldsets for touch interactions
  - Consider responsive layouts for complex fieldset content
  - Test legend readability on small screens

---
