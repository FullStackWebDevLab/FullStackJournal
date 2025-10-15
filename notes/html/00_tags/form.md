# `<form>`

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

The `<form>` element represents a document section that contains interactive controls for submitting information to a web server or processing user input client-side. It serves as a container for various form elements like text fields, checkboxes, radio buttons, and submission buttons, enabling user data collection, validation, and transmission.

---

## Syntax and Variants

+ **Standard syntax**: `<form>...</form>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps form controls and other content
+ **No self-closing variant**: Must contain form elements
+ **Interactive container**: Creates a form context for user input elements

---

## Attributes

+ **Core attributes**:
  - `action` (optional): URL where form data is sent upon submission
  - `method` (optional): HTTP method for form submission (`get`, `post`)
  - `enctype` (optional): Encoding type for form data (`application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain`)
  - `target` (optional): Where to display response (`_self`, `_blank`, `_parent`, `_top`, frame name)
  - `autocomplete` (optional): Enable/disable autocomplete (`on`, `off`)
  - `novalidate` (optional): Bypass form validation (boolean)
  - `name` (optional): Name for scripting and reference
  - `accept-charset` (optional): Character encodings for form submission
  - `rel` (optional): Relationship between current document and target URL

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Deprecated attributes**:
  - `accept` (use `accept` on `<input type="file">` instead)

---

## Content Model

+ **Permitted content**: Flow content, but cannot contain nested `<form>` elements
+ **Allowed content**:
  - Form controls: `<input>`, `<textarea>`, `<select>`, `<button>`, etc.
  - Structural elements: `<div>`, `<fieldset>`, `<legend>`, `<label>`
  - Text and phrasing content
  - Interactive elements that are not form controls
+ **Restricted content**: Cannot contain another `<form>` element
+ **Mixed content**: Can contain both form and non-form elements

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<body>` as direct children
  - Within `<article>`, `<section>`, `<main>` for content forms
  - Within `<div>` containers for layout purposes
  - In headers, sidebars, and modal dialogs
+ **No nesting**: Forms cannot be nested within other forms

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - `margin-top: 0em` (varies by browser)
  - No borders, background, or padding by default
+ **Submission behavior**:
  - Gathers data from contained form controls
  - Validates required fields (unless `novalidate` is set)
  - Submits data to specified `action` URL using `method`
  - Can trigger page reload or handle submission via JavaScript
+ **Semantic meaning**:
  - Represents an interactive form for user input
  - Screen readers announce as "form" and describe form purpose
  - Provides context for form controls and their relationships
+ **Accessibility**: Essential for screen reader users to understand form structure and purpose

---

## Examples

**Basic contact form:**
```html
<form action="/contact" method="post">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>
  
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>
  
  <label for="message">Message:</label>
  <textarea id="message" name="message" required></textarea>
  
  <button type="submit">Send Message</button>
</form>
```

**Form with various input types:**
```html
<form action="/survey" method="post" class="survey-form">
  <fieldset>
    <legend>Personal Information</legend>
    
    <div class="form-group">
      <label for="fullname">Full Name:</label>
      <input type="text" id="fullname" name="fullname" required>
    </div>
    
    <div class="form-group">
      <label for="age">Age:</label>
      <input type="number" id="age" name="age" min="18" max="100">
    </div>
    
    <div class="form-group">
      <label for="newsletter">
        <input type="checkbox" id="newsletter" name="newsletter" value="yes">
        Subscribe to newsletter
      </label>
    </div>
  </fieldset>
  
  <fieldset>
    <legend>Preferences</legend>
    
    <div class="form-group">
      <label>Favorite Color:</label>
      <select name="color">
        <option value="red">Red</option>
        <option value="blue">Blue</option>
        <option value="green">Green</option>
      </select>
    </div>
    
    <div class="form-group">
      <label>Communication Method:</label>
      <label>
        <input type="radio" name="communication" value="email" checked>
        Email
      </label>
      <label>
        <input type="radio" name="communication" value="phone">
        Phone
      </label>
      <label>
        <input type="radio" name="communication" value="sms">
        SMS
      </label>
    </div>
  </fieldset>
  
  <div class="form-actions">
    <button type="submit">Submit Survey</button>
    <button type="reset">Reset Form</button>
  </div>
</form>
```

**File upload form:**
```html
<form action="/upload" method="post" enctype="multipart/form-data">
  <h3>Upload Documents</h3>
  
  <div class="form-group">
    <label for="document">Select Document:</label>
    <input type="file" id="document" name="document" 
           accept=".pdf,.doc,.docx,.txt" required>
  </div>
  
  <div class="form-group">
    <label for="description">Description:</label>
    <input type="text" id="description" name="description" 
           placeholder="Brief description of the document">
  </div>
  
  <div class="form-group">
    <label for="category">Category:</label>
    <select id="category" name="category" required>
      <option value="">Select a category</option>
      <option value="contract">Contract</option>
      <option value="report">Report</option>
      <option value="proposal">Proposal</option>
    </select>
  </div>
  
  <button type="submit">Upload Document</button>
</form>
```

**Login form with validation:**
```html
<form id="login-form" action="/login" method="post" novalidate>
  <h2>Login to Your Account</h2>
  
  <div class="form-group">
    <label for="username">Username or Email:</label>
    <input type="text" id="username" name="username" 
           required minlength="3" maxlength="50"
           pattern="[a-zA-Z0-9@._-]+"
           aria-describedby="username-help">
    <small id="username-help">3-50 characters, letters, numbers, @ . _ - only</small>
    <span class="error-message" id="username-error"></span>
  </div>
  
  <div class="form-group">
    <label for="password">Password:</label>
    <input type="password" id="password" name="password" 
           required minlength="8"
           aria-describedby="password-help">
    <small id="password-help">Minimum 8 characters</small>
    <span class="error-message" id="password-error"></span>
  </div>
  
  <div class="form-group">
    <label>
      <input type="checkbox" name="remember" value="yes">
      Remember me
    </label>
  </div>
  
  <div class="form-actions">
    <button type="submit">Login</button>
    <a href="/forgot-password">Forgot Password?</a>
  </div>
</form>

<script>
document.getElementById('login-form').addEventListener('submit', function(event) {
  const username = document.getElementById('username');
  const password = document.getElementById('password');
  let isValid = true;
  
  // Clear previous errors
  document.getElementById('username-error').textContent = '';
  document.getElementById('password-error').textContent = '';
  
  // Validate username
  if (!username.value.trim()) {
    document.getElementById('username-error').textContent = 'Username is required';
    isValid = false;
  }
  
  // Validate password
  if (password.value.length < 8) {
    document.getElementById('password-error').textContent = 'Password must be at least 8 characters';
    isValid = false;
  }
  
  if (!isValid) {
    event.preventDefault();
  }
});
</script>
```

**Search form:**
```html
<form action="/search" method="get" role="search" class="search-form">
  <label for="search-query" class="visually-hidden">Search</label>
  <input type="search" id="search-query" name="q" 
         placeholder="Search products..." 
         aria-label="Search products">
  
  <div class="search-filters">
    <label for="category-filter">Category:</label>
    <select id="category-filter" name="category">
      <option value="">All Categories</option>
      <option value="electronics">Electronics</option>
      <option value="clothing">Clothing</option>
      <option value="books">Books</option>
    </select>
    
    <label for="price-range">Price Range:</label>
    <select id="price-range" name="price">
      <option value="">Any Price</option>
      <option value="0-50">$0 - $50</option>
      <option value="50-100">$50 - $100</option>
      <option value="100-500">$100 - $500</option>
    </select>
  </div>
  
  <button type="submit">
    <span aria-hidden="true">🔍</span>
    Search
  </button>
</form>
```

**Multi-step form:**
```html
<form id="multi-step-form" action="/register" method="post">
  <!-- Step 1: Personal Information -->
  <div id="step-1" class="form-step active">
    <h3>Step 1: Personal Information</h3>
    
    <div class="form-group">
      <label for="first-name">First Name:</label>
      <input type="text" id="first-name" name="first_name" required>
    </div>
    
    <div class="form-group">
      <label for="last-name">Last Name:</label>
      <input type="text" id="last-name" name="last_name" required>
    </div>
    
    <div class="form-group">
      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required>
    </div>
    
    <button type="button" class="next-step">Next</button>
  </div>
  
  <!-- Step 2: Account Details -->
  <div id="step-2" class="form-step">
    <h3>Step 2: Account Details</h3>
    
    <div class="form-group">
      <label for="username">Username:</label>
      <input type="text" id="username" name="username" required>
    </div>
    
    <div class="form-group">
      <label for="password">Password:</label>
      <input type="password" id="password" name="password" required>
    </div>
    
    <div class="form-group">
      <label for="confirm-password">Confirm Password:</label>
      <input type="password" id="confirm-password" name="confirm_password" required>
    </div>
    
    <button type="button" class="prev-step">Previous</button>
    <button type="button" class="next-step">Next</button>
  </div>
  
  <!-- Step 3: Preferences -->
  <div id="step-3" class="form-step">
    <h3>Step 3: Preferences</h3>
    
    <div class="form-group">
      <label>Newsletter Preferences:</label>
      <label>
        <input type="checkbox" name="newsletters[]" value="weekly">
        Weekly Updates
      </label>
      <label>
        <input type="checkbox" name="newsletters[]" value="promotions">
        Special Promotions
      </label>
      <label>
        <input type="checkbox" name="newsletters[]" value="events">
        Event Notifications
      </label>
    </div>
    
    <div class="form-group">
      <label for="timezone">Timezone:</label>
      <select id="timezone" name="timezone">
        <option value="est">Eastern Time (EST)</option>
        <option value="cst">Central Time (CST)</option>
        <option value="pst">Pacific Time (PST)</option>
      </select>
    </div>
    
    <button type="button" class="prev-step">Previous</button>
    <button type="submit">Complete Registration</button>
  </div>
</form>

<script>
// Multi-step form navigation
document.querySelectorAll('.next-step').forEach(button => {
  button.addEventListener('click', function() {
    const currentStep = this.closest('.form-step');
    const nextStep = currentStep.nextElementSibling;
    
    currentStep.classList.remove('active');
    nextStep.classList.add('active');
  });
});

document.querySelectorAll('.prev-step').forEach(button => {
  button.addEventListener('click', function() {
    const currentStep = this.closest('.form-step');
    const prevStep = currentStep.previousElementSibling;
    
    currentStep.classList.remove('active');
    prevStep.classList.add('active');
  });
});
</script>
```

**Form with AJAX submission:**
```html
<form id="ajax-form" action="/api/contact" method="post">
  <h3>Contact Us</h3>
  
  <div class="form-group">
    <label for="contact-name">Name:</label>
    <input type="text" id="contact-name" name="name" required>
  </div>
  
  <div class="form-group">
    <label for="contact-email">Email:</label>
    <input type="email" id="contact-email" name="email" required>
  </div>
  
  <div class="form-group">
    <label for="contact-subject">Subject:</label>
    <input type="text" id="contact-subject" name="subject" required>
  </div>
  
  <div class="form-group">
    <label for="contact-message">Message:</label>
    <textarea id="contact-message" name="message" required></textarea>
  </div>
  
  <div class="form-status" id="form-status"></div>
  
  <button type="submit" id="submit-btn">Send Message</button>
</form>

<script>
document.getElementById('ajax-form').addEventListener('submit', async function(event) {
  event.preventDefault();
  
  const submitBtn = document.getElementById('submit-btn');
  const statusDiv = document.getElementById('form-status');
  
  // Disable submit button
  submitBtn.disabled = true;
  submitBtn.textContent = 'Sending...';
  statusDiv.textContent = '';
  
  try {
    const formData = new FormData(this);
    
    const response = await fetch(this.action, {
      method: this.method,
      body: formData
    });
    
    const result = await response.json();
    
    if (response.ok) {
      statusDiv.textContent = 'Message sent successfully!';
      statusDiv.className = 'form-status success';
      this.reset();
    } else {
      throw new Error(result.message || 'Submission failed');
    }
  } catch (error) {
    statusDiv.textContent = error.message;
    statusDiv.className = 'form-status error';
  } finally {
    submitBtn.disabled = false;
    submitBtn.textContent = 'Send Message';
  }
});
</script>
```

**Accessible form with ARIA:**
```html
<form id="accessible-form" action="/apply" method="post" 
      aria-labelledby="form-title" aria-describedby="form-description">
  <h2 id="form-title">Job Application Form</h2>
  <p id="form-description">Please fill out all required fields marked with an asterisk (*)</p>
  
  <fieldset aria-labelledby="personal-info-title">
    <legend id="personal-info-title">Personal Information</legend>
    
    <div class="form-group" role="group" aria-labelledby="name-label">
      <span id="name-label" class="label-text">Full Name *</span>
      <input type="text" name="full_name" required
             aria-required="true"
             aria-describedby="name-help">
      <span id="name-help" class="help-text">Enter your legal full name</span>
    </div>
    
    <div class="form-group" role="group" aria-labelledby="phone-label">
      <span id="phone-label" class="label-text">Phone Number</span>
      <input type="tel" name="phone"
             pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}"
             aria-describedby="phone-format">
      <span id="phone-format" class="help-text">Format: 123-456-7890</span>
    </div>
  </fieldset>
  
  <fieldset aria-labelledby="position-info-title">
    <legend id="position-info-title">Position Information</legend>
    
    <div class="form-group">
      <label for="position">Desired Position *</label>
      <select id="position" name="position" required aria-required="true">
        <option value="">Select a position</option>
        <option value="developer">Software Developer</option>
        <option value="designer">UI/UX Designer</option>
        <option value="manager">Project Manager</option>
      </select>
    </div>
    
    <div class="form-group" role="group" aria-labelledby="availability-label">
      <span id="availability-label" class="label-text">Availability</span>
      <label>
        <input type="radio" name="availability" value="fulltime" checked>
        Full Time
      </label>
      <label>
        <input type="radio" name="availability" value="parttime">
        Part Time
      </label>
      <label>
        <input type="radio" name="availability" value="contract">
        Contract
      </label>
    </div>
  </fieldset>
  
  <div class="form-actions">
    <button type="submit" aria-label="Submit job application">Submit Application</button>
    <button type="reset">Clear Form</button>
  </div>
</form>
```

---

## Notes

* **Security considerations**: Always validate and sanitize form data on the server-side
* **Accessibility requirements**:
  - Use proper `<label>` associations for all form controls
  - Provide clear error messages and validation feedback
  - Ensure keyboard navigation works throughout the form
  - Use ARIA attributes for complex form interactions
* **Method differences**:
  - `GET`: Data appended to URL, limited length, bookmarkable, visible in history
  - `POST`: Data in request body, no size limits, not bookmarkable, more secure for sensitive data
* **Encoding types**:
  - `application/x-www-form-urlencoded`: Default, URL-encoded key-value pairs
  - `multipart/form-data`: Required for file uploads, preserves binary data
  - `text/plain`: Space-separated key-value pairs, rarely used
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Forgetting server-side validation (relying only on client-side)
  - Not providing proper form labels and instructions
  - Using GET for sensitive data or large submissions
  - Nesting forms within other forms
  - Overlooking mobile usability and touch targets
* **Performance considerations**:
  - Large forms may benefit from progressive enhancement
  - Consider lazy loading for very long forms
  - Optimize file uploads with proper encoding and size limits
* **SEO impact**: Forms with GET method can be crawled, POST forms generally cannot
* **Progressive enhancement**: Ensure forms work without JavaScript when possible

---
