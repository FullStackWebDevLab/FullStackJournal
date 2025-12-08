# `<legend>`

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

The `<legend>` element represents a caption or title for the content of its parent `<fieldset>` element. It provides a semantic description for a group of related form controls, helping users understand the purpose of the grouped elements and improving accessibility by providing context for screen reader users.

---

## Syntax and Variants

+ **Standard syntax**: `<legend>...</legend>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain text and inline elements
+ **No self-closing variant**: Must contain content
+ **Fieldset association**: Always used as the first child of a `<fieldset>` element

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies on semantic role within fieldset structure
+ **Commonly used**: `class`, `id` for styling and scripting

---

## Content Model

+ **Permitted content**: Phrasing content
+ **Allowed content**:
  - Text and character references
  - Phrasing elements: `<strong>`, `<em>`, `<span>`, etc.
  - Images and other inline elements
+ **Restricted content**: Cannot contain heading elements or block-level elements
+ **Text focus**: Primarily intended for concise descriptive text

---

## Context

+ **Required parent**: Must be a direct child of `<fieldset>` element
+ **Position requirements**: 
  - Must be the first child of the `<fieldset>`
  - Should appear before any other content in the fieldset
+ **Single instance**: Only one `<legend>` allowed per `<fieldset>`
+ **Fieldset relationship**: Describes the entire fieldset content

---

## Behavior and Semantics

+ **Default display**: Block-level element with special positioning
+ **Default styling**:
  - Typically appears overlaying the fieldset's top border
  - Browser-dependent appearance (often bold or emphasized)
  - Padding and margin handling varies by browser
  - Width typically constrained to content width
+ **Interactive behavior**:
  - Non-interactive (doesn't respond to clicks or focus)
  - Provides semantic context for screen readers
  - Helps visual users understand form sections
+ **Semantic meaning**:
  - Represents a caption for a fieldset group
  - Screen readers announce before reading fieldset content
  - Provides hierarchical organization for complex forms
+ **Accessibility**: Essential for screen reader users to understand grouped form controls

---

## Examples

**Basic legend in a fieldset:**
```html
<fieldset>
  <legend>Personal Information</legend>
  
  <label for="first-name">First Name:</label>
  <input type="text" id="first-name" name="first_name">
  
  <label for="last-name">Last Name:</label>
  <input type="text" id="last-name" name="last_name">
  
  <label for="email">Email:</label>
  <input type="email" id="email" name="email">
</fieldset>
```

**Legend with contact information grouping:**
```html
<fieldset>
  <legend>Contact Details</legend>
  
  <div class="form-group">
    <label for="phone">Phone Number:</label>
    <input type="tel" id="phone" name="phone" placeholder="123-456-7890">
  </div>
  
  <div class="form-group">
    <label for="address">Street Address:</label>
    <input type="text" id="address" name="address">
  </div>
  
  <div class="form-group">
    <label for="city">City:</label>
    <input type="text" id="city" name="city">
  </div>
</fieldset>
```

**Styled legend with CSS:**
```html
<fieldset class="styled-fieldset">
  <legend class="styled-legend">Payment Information</legend>
  
  <label for="card-number">Card Number:</label>
  <input type="text" id="card-number" name="card_number" placeholder="1234 5678 9012 3456">
  
  <label for="expiry">Expiry Date:</label>
  <input type="text" id="expiry" name="expiry" placeholder="MM/YY">
  
  <label for="cvc">CVC:</label>
  <input type="text" id="cvc" name="cvc" placeholder="123">
</fieldset>

<style>
.styled-fieldset {
  border: 2px solid #007bff;
  border-radius: 8px;
  padding: 20px;
  margin: 20px 0;
}

.styled-legend {
  color: #007bff;
  font-weight: 600;
  font-size: 1.1em;
  padding: 0 12px;
  background: white;
}
</style>
```

**Legend in a registration form:**
```html
<form class="registration-form">
  <fieldset>
    <legend>Account Details</legend>
    
    <div class="form-row">
      <label for="username">Username:</label>
      <input type="text" id="username" name="username" required>
    </div>
    
    <div class="form-row">
      <label for="password">Password:</label>
      <input type="password" id="password" name="password" required>
    </div>
    
    <div class="form-row">
      <label for="confirm-password">Confirm Password:</label>
      <input type="password" id="confirm-password" name="confirm_password" required>
    </div>
  </fieldset>
  
  <fieldset>
    <legend>Profile Information</legend>
    
    <div class="form-row">
      <label for="full-name">Full Name:</label>
      <input type="text" id="full-name" name="full_name" required>
    </div>
    
    <div class="form-row">
      <label for="birthdate">Date of Birth:</label>
      <input type="date" id="birthdate" name="birthdate">
    </div>
    
    <div class="form-row">
      <label for="bio">Biography:</label>
      <textarea id="bio" name="bio" rows="4"></textarea>
    </div>
  </fieldset>
</form>

<style>
.registration-form {
  max-width: 600px;
}

fieldset {
  border: 1px solid #ddd;
  border-radius: 6px;
  padding: 20px;
  margin-bottom: 20px;
}

legend {
  font-weight: 600;
  color: #333;
  padding: 0 10px;
}

.form-row {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: 500;
}

input, textarea {
  width: 100%;
  padding: 8px 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}
</style>
```

**Accessible legend with ARIA:**
```html
<fieldset aria-labelledby="shipping-legend">
  <legend id="shipping-legend">Shipping Address</legend>
  
  <div class="form-group">
    <label for="shipping-street">Street Address:</label>
    <input type="text" id="shipping-street" name="shipping_street" required>
  </div>
  
  <div class="form-group">
    <label for="shipping-city">City:</label>
    <input type="text" id="shipping-city" name="shipping_city" required>
  </div>
  
  <div class="form-group">
    <label for="shipping-zip">ZIP Code:</label>
    <input type="text" id="shipping-zip" name="shipping_zip" required>
  </div>
</fieldset>
```

**Legend with icon and styling:**
```html
<fieldset class="icon-fieldset">
  <legend class="icon-legend">
    <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
      <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
    </svg>
    User Profile
  </legend>
  
  <label for="avatar">Avatar URL:</label>
  <input type="url" id="avatar" name="avatar">
  
  <label for="website">Website:</label>
  <input type="url" id="website" name="website">
</fieldset>

<style>
.icon-fieldset {
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  padding: 20px;
}

.icon-legend {
  display: flex;
  align-items: center;
  gap: 8px;
  font-weight: 600;
  color: #333;
  padding: 0 12px;
  background: white;
}
</style>
```

**Legend in a multi-step form:**
```html
<form class="multi-step-form">
  <!-- Step 1 -->
  <fieldset id="step1" class="form-step active">
    <legend>Step 1: Personal Information</legend>
    
    <div class="form-group">
      <label for="full-name">Full Name:</label>
      <input type="text" id="full-name" name="full_name" required>
    </div>
    
    <div class="form-group">
      <label for="email">Email Address:</label>
      <input type="email" id="email" name="email" required>
    </div>
    
    <button type="button" class="next-step">Next</button>
  </fieldset>
  
  <!-- Step 2 -->
  <fieldset id="step2" class="form-step">
    <legend>Step 2: Company Details</legend>
    
    <div class="form-group">
      <label for="company-name">Company Name:</label>
      <input type="text" id="company-name" name="company_name">
    </div>
    
    <div class="form-group">
      <label for="position">Position:</label>
      <input type="text" id="position" name="position">
    </div>
    
    <button type="button" class="prev-step">Previous</button>
    <button type="submit">Complete Registration</button>
  </fieldset>
</form>

<style>
.form-step {
  display: none;
  border: 1px solid #ddd;
  border-radius: 6px;
  padding: 20px;
  margin-bottom: 20px;
}

.form-step.active {
  display: block;
}

legend {
  font-weight: 600;
  margin-bottom: 15px;
  color: #2c3e50;
}
</style>

<script>
document.querySelector('.next-step').addEventListener('click', function() {
  document.getElementById('step1').classList.remove('active');
  document.getElementById('step2').classList.add('active');
});

document.querySelector('.prev-step').addEventListener('click', function() {
  document.getElementById('step2').classList.remove('active');
  document.getElementById('step1').classList.add('active');
});
</script>
```

**Legend with required field indicator:**
```html
<fieldset>
  <legend>
    Billing Information
    <span class="required-fields">* Required fields</span>
  </legend>
  
  <div class="form-group">
    <label for="billing-name">
      Full Name <span class="required">*</span>
    </label>
    <input type="text" id="billing-name" name="billing_name" required>
  </div>
  
  <div class="form-group">
    <label for="billing-address">
      Address <span class="required">*</span>
    </label>
    <input type="text" id="billing-address" name="billing_address" required>
  </div>
  
  <div class="form-group">
    <label for="billing-phone">Phone Number:</label>
    <input type="tel" id="billing-phone" name="billing_phone">
  </div>
</fieldset>

<style>
.required-fields {
  font-size: 0.8em;
  color: #666;
  font-weight: normal;
  margin-left: 10px;
}

.required {
  color: #dc3545;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: 500;
}
</style>
```

**Legend in a settings form:**
```html
<form class="settings-form">
  <fieldset>
    <legend>Privacy Settings</legend>
    
    <div class="setting-item">
      <label>
        <input type="checkbox" name="profile_public" checked>
        Make profile public
      </label>
      <span class="setting-description">Allow other users to view your profile</span>
    </div>
    
    <div class="setting-item">
      <label>
        <input type="checkbox" name="email_notifications" checked>
        Email notifications
      </label>
      <span class="setting-description">Receive email updates about your account</span>
    </div>
    
    <div class="setting-item">
      <label>
        <input type="checkbox" name="search_engine_index">
        Allow search engine indexing
      </label>
      <span class="setting-description">Let search engines index your public profile</span>
    </div>
  </fieldset>
  
  <fieldset>
    <legend>Communication Preferences</legend>
    
    <div class="setting-item">
      <label>Newsletter Frequency:</label>
      <select name="newsletter_frequency">
        <option value="daily">Daily</option>
        <option value="weekly" selected>Weekly</option>
        <option value="monthly">Monthly</option>
        <option value="never">Never</option>
      </select>
    </div>
    
    <div class="setting-item">
      <label>Preferred Contact Method:</label>
      <div class="radio-group">
        <label>
          <input type="radio" name="contact_method" value="email" checked>
          Email
        </label>
        <label>
          <input type="radio" name="contact_method" value="sms">
          SMS
        </label>
        <label>
          <input type="radio" name="contact_method" value="push">
          Push Notification
        </label>
      </div>
    </div>
  </fieldset>
</form>

<style>
.settings-form {
  max-width: 600px;
}

fieldset {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 20px;
}

legend {
  font-weight: 600;
  color: #2c3e50;
  padding: 0 10px;
}

.setting-item {
  margin-bottom: 20px;
  padding-bottom: 15px;
  border-bottom: 1px solid #f0f0f0;
}

.setting-item:last-child {
  border-bottom: none;
}

.setting-description {
  display: block;
  font-size: 0.875em;
  color: #666;
  margin-top: 4px;
}

.radio-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
  margin-top: 5px;
}
</style>
```

**Legend with complex form structure:**
```html
<form class="complex-form">
  <fieldset class="form-section">
    <legend class="section-legend">Order Details</legend>
    
    <div class="form-grid">
      <div class="form-group">
        <label for="order-date">Order Date:</label>
        <input type="date" id="order-date" name="order_date" required>
      </div>
      
      <div class="form-group">
        <label for="order-amount">Order Amount:</label>
        <input type="number" id="order-amount" name="order_amount" min="0" step="0.01" required>
      </div>
      
      <div class="form-group">
        <label for="order-status">Status:</label>
        <select id="order-status" name="order_status" required>
          <option value="pending">Pending</option>
          <option value="processing">Processing</option>
          <option value="shipped">Shipped</option>
          <option value="delivered">Delivered</option>
        </select>
      </div>
      
      <div class="form-group full-width">
        <label for="order-notes">Special Instructions:</label>
        <textarea id="order-notes" name="order_notes" rows="3"></textarea>
      </div>
    </div>
  </fieldset>
</form>

<style>
.complex-form {
  max-width: 800px;
}

.form-section {
  border: 2px solid #3498db;
  border-radius: 10px;
  padding: 25px;
  margin-bottom: 25px;
}

.section-legend {
  font-size: 1.2em;
  font-weight: 700;
  color: #3498db;
  padding: 0 15px;
  background: white;
}

.form-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-group.full-width {
  grid-column: 1 / -1;
}

label {
  margin-bottom: 8px;
  font-weight: 600;
  color: #333;
}

input, select, textarea {
  padding: 10px 12px;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-size: 16px;
}

@media (max-width: 768px) {
  .form-grid {
    grid-template-columns: 1fr;
  }
}
</style>
```

---

## Notes

* **Position requirement**: Must be the first child of `<fieldset>` for proper semantics and styling
* **Accessibility importance**: 
  - Screen readers announce legend text when entering the fieldset
  - Provides essential context for grouped form controls
  - Helps users understand the relationship between related fields
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Placing `<legend>` after other content in the fieldset
  - Using multiple `<legend>` elements in one fieldset
  - Using block-level elements within the legend
  - Creating overly long or complex legend text
  - Forgetting to use legends for fieldsets with related controls
* **Styling considerations**:
  - Legends have unique positioning that overlays the fieldset border
  - Background color is often needed to cover the fieldset border
  - Width is typically constrained to content width
  - Padding and margin behavior varies across browsers
* **Mobile considerations**:
  - Ensure legend text remains readable on small screens
  - Test fieldset and legend rendering on mobile browsers
  - Consider responsive styling for complex form layouts
* **Best practices**:
  - Use clear, concise text that describes the fieldset content
  - Keep legends short and descriptive
  - Use consistent styling across all legends in a form
  - Ensure adequate color contrast for accessibility
  - Test with screen readers for proper announcement

---
