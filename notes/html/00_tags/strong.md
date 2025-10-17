# `<strong>`

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

The `<strong>` element represents text with strong importance, seriousness, or urgency. It indicates that its contents have strong importance relative to the surrounding content. Unlike purely presentational bold styling, `<strong>` carries semantic meaning that is communicated to assistive technologies and has implications for document structure and interpretation.

---

## Syntax and Variants

+ **Standard syntax**: `<strong>...</strong>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain text and inline elements
+ **No self-closing variant**: Must contain content
+ **No alternative forms**: Standard syntax only

---

## Attributes

+ **No specific attributes**: The `<strong>` element does not have any element-specific attributes
+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, `lang`, `dir`, etc.
+ **Event handlers**: All global event attributes supported

---

## Content Model

+ **Permitted content**: Phrasing content
+ **Allowed content**:
  - Text and character references
  - Other phrasing elements: `<em>`, `<span>`, `<a>`, etc.
  - Images and other inline elements
+ **Restricted content**: Cannot contain flow content (paragraphs, lists, etc.)
+ **Nesting**: Can be nested with other text-level semantic elements

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within paragraphs (`<p>`)
  - Within headings (`<h1>`-`<h6>`)
  - Within list items (`<li>`)
  - Within table cells (`<td>`, `<th>`)
  - Within other text-level semantic elements
+ **Nesting relationships**:
  - Can contain other phrasing elements
  - Can be nested within other phrasing elements
  - Multiple `<strong>` elements can be nested for increased importance

---

## Behavior and Semantics

+ **Default display**: Inline element
+ **Default styling**:
  - `display: inline`
  - `font-weight: bold` (most browsers)
  - No other inherent visual styling
  - Inherits text properties from parent elements
+ **Semantic meaning**:
  - Indicates strong importance for its contents
  - Nested instances indicate increasing levels of importance
  - Communicates seriousness or urgency to users
+ **Accessibility role**:
  - Implicit ARIA role: `strong`
  - Screen readers may change vocal emphasis or announce as "strong"
  - Helps users identify critical information
+ **SEO significance**: May influence how search engines interpret content importance

---

## Examples

**Basic strong emphasis:**
```html
<p>Warning: <strong>This action cannot be undone.</strong> Please proceed with caution.</p>
```

**Multiple strong elements in context:**
```html
<article>
  <h1>Security Alert</h1>
  <p>
    <strong>Important security update required.</strong> All users must 
    update their software immediately to protect against 
    <strong>critical vulnerabilities</strong> that could compromise 
    system security.
  </p>
</article>
```

**Nested strong elements for increased importance:**
```html
<p>
  The system will undergo maintenance tonight. 
  <strong>
    All unsaved work will be lost 
    <strong>and cannot be recovered</strong>.
  </strong>
  Please save your work before 10:00 PM.
</p>
```

**Strong in form labels and instructions:**
```html
<form>
  <div class="form-group">
    <label for="password">
      Password <strong>*</strong>
    </label>
    <input type="password" id="password" name="password" required>
    <p class="help-text">
      <strong>Must contain:</strong> at least 8 characters, one uppercase letter, 
      one number, and one special character.
    </p>
  </div>
</form>

<style>
.form-group {
  margin-bottom: 1rem;
}

.help-text {
  font-size: 0.875em;
  color: #666;
  margin-top: 0.25rem;
}
</style>
```

**Strong in warning messages:**
```html
<div class="alert alert-warning">
  <h3>⚠️ System Maintenance</h3>
  <p>
    <strong>Scheduled maintenance</strong> will occur on Saturday, 
    December 14th from 2:00 AM to 6:00 AM EST. 
    <strong>All services will be unavailable</strong> during this period.
  </p>
</div>

<style>
.alert {
  padding: 1rem;
  border-radius: 4px;
  margin: 1rem 0;
}

.alert-warning {
  background-color: #fff3cd;
  border: 1px solid #ffecb5;
  color: #856404;
}
</style>
```

**Strong in legal and compliance text:**
```html
<section class="legal-notice">
  <h2>Terms and Conditions</h2>
  <p>
    By using this service, you agree to our terms of service. 
    <strong>You are responsible for maintaining the confidentiality</strong> 
    of your account credentials. The company 
    <strong>shall not be liable for any unauthorized access</strong> 
    resulting from your failure to secure your login information.
  </p>
</section>

<style>
.legal-notice {
  border-left: 4px solid #dc3545;
  padding-left: 1rem;
  background-color: #f8f9fa;
  padding: 1rem;
}
</style>
```

**Strong with custom styling:**
```html
<p class="instruction-text">
  Before submitting your application, 
  <strong class="critical-step">double-check all entered information</strong> 
  for accuracy. Errors may delay processing by 
  <strong class="warning">several weeks</strong>.
</p>

<style>
.instruction-text {
  font-size: 1.1em;
  line-height: 1.6;
}

.critical-step {
  color: #dc3545;
  font-weight: 700;
  text-decoration: underline;
}

.warning {
  color: #fd7e14;
  font-weight: 600;
  background-color: #fff3cd;
  padding: 0.1em 0.3em;
  border-radius: 3px;
}
</style>
```

**Strong in data tables:**
```html
<table class="financial-table">
  <caption>Quarterly Financial Summary</caption>
  <thead>
    <tr>
      <th>Quarter</th>
      <th>Revenue</th>
      <th>Profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Q1</td>
      <td>$1,200,000</td>
      <td>$150,000</td>
    </tr>
    <tr>
      <td>Q2</td>
      <td>$1,350,000</td>
      <td><strong>$180,000</strong></td>
    </tr>
    <tr>
      <td>Q3</td>
      <td><strong>$1,550,000</strong></td>
      <td><strong>$210,000</strong></td>
    </tr>
    <tr>
      <td>Q4</td>
      <td>$1,400,000</td>
      <td>$170,000</td>
    </tr>
  </tbody>
</table>

<style>
.financial-table {
  width: 100%;
  border-collapse: collapse;
}

.financial-table th,
.financial-table td {
  padding: 0.75rem;
  text-align: left;
  border-bottom: 1px solid #dee2e6;
}

.financial-table thead th {
  background-color: #343a40;
  color: white;
}

.financial-table tbody tr:hover {
  background-color: #f8f9fa;
}
</style>
```

**Strong in navigation and interactive elements:**
```html
<nav aria-label="Main navigation">
  <ul class="nav-list">
    <li><a href="/">Home</a></li>
    <li>
      <a href="/products">
        Products 
        <strong class="new-badge">New</strong>
      </a>
    </li>
    <li><a href="/about">About</a></li>
    <li>
      <a href="/support">
        Support
        <strong class="alert-badge">24/7</strong>
      </a>
    </li>
  </ul>
</nav>

<style>
.nav-list {
  list-style: none;
  padding: 0;
  display: flex;
  gap: 2rem;
}

.nav-list a {
  text-decoration: none;
  color: #333;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.new-badge {
  background-color: #28a745;
  color: white;
  font-size: 0.7em;
  padding: 0.2em 0.6em;
  border-radius: 12px;
  font-weight: 600;
}

.alert-badge {
  background-color: #dc3545;
  color: white;
  font-size: 0.7em;
  padding: 0.2em 0.6em;
  border-radius: 12px;
  font-weight: 600;
}
</style>
```

**Strong with ARIA attributes for enhanced accessibility:**
```html
<div class="status-message" role="status">
  <p>
    File upload completed. 
    <strong aria-live="polite" aria-atomic="true">
      Successfully processed 1,247 records.
    </strong>
  </p>
</div>

<div class="error-message" role="alert">
  <p>
    <strong aria-live="assertive" aria-atomic="true">
      Connection lost:
    </strong> 
    Please check your network connection and try again.
  </p>
</div>

<style>
.status-message {
  background-color: #d1ecf1;
  border: 1px solid #bee5eb;
  color: #0c5460;
  padding: 1rem;
  border-radius: 4px;
  margin: 1rem 0;
}

.error-message {
  background-color: #f8d7da;
  border: 1px solid #f5c6cb;
  color: #721c24;
  padding: 1rem;
  border-radius: 4px;
  margin: 1rem 0;
}
</style>
```

**Strong in complex document structure:**
```html
<article class="research-paper">
  <header>
    <h1>The Impact of Climate Change on Coastal Ecosystems</h1>
    <p class="author">Dr. Maria Rodriguez, Environmental Research Institute</p>
  </header>
  
  <section class="abstract">
    <h2>Abstract</h2>
    <p>
      This study examines the <strong>accelerating effects</strong> of climate change 
      on coastal biodiversity. Our findings indicate 
      <strong>significant habitat loss</strong> in the observed regions, with 
      <strong>critical implications</strong> for conservation efforts.
    </p>
  </section>
  
  <section class="key-findings">
    <h2>Key Findings</h2>
    <ul>
      <li>
        <strong>Sea level rise</strong> has exceeded previous projections by 23%
      </li>
      <li>
        <strong>Coastal erosion</strong> rates have doubled in the past decade
      </li>
      <li>
        <strong>Biodiversity loss</strong> is most pronounced in mangrove ecosystems
      </li>
    </ul>
  </section>
  
  <section class="conclusion">
    <h2>Conclusion</h2>
    <p>
      <strong>Immediate intervention is required</strong> to mitigate further damage. 
      The study strongly recommends implementing the proposed conservation 
      strategies <strong>within the next 24 months</strong> to prevent 
      irreversible ecosystem collapse.
    </p>
  </section>
</article>

<style>
.research-paper {
  max-width: 800px;
  margin: 0 auto;
  line-height: 1.7;
  font-family: 'Georgia', serif;
}

.research-paper h1 {
  text-align: center;
  color: #2c5530;
  border-bottom: 2px solid #2c5530;
  padding-bottom: 1rem;
}

.abstract {
  background-color: #f8f9fa;
  padding: 1.5rem;
  border-left: 4px solid #6c757d;
  margin: 2rem 0;
}

.key-findings ul {
  padding-left: 1.5rem;
}

.key-findings li {
  margin-bottom: 0.5rem;
}

.conclusion {
  background-color: #fff3cd;
  padding: 1.5rem;
  border: 1px solid #ffeaa7;
  border-radius: 4px;
  margin: 2rem 0;
}
</style>
```

**Strong in responsive design patterns:**
```html
<div class="pricing-grid">
  <div class="pricing-tier">
    <h3>Basic</h3>
    <p class="price"><strong>$9</strong>/month</p>
    <ul class="features">
      <li>10 GB Storage</li>
      <li>Basic Support</li>
      <li><strong>1 User</strong></li>
    </ul>
  </div>
  
  <div class="pricing-tier featured">
    <h3>Professional</h3>
    <p class="price"><strong>$29</strong>/month</p>
    <ul class="features">
      <li><strong>100 GB Storage</strong></li>
      <li><strong>Priority Support</strong></li>
      <li><strong>5 Users</strong></li>
      <li><strong>Advanced Analytics</strong></li>
    </ul>
  </div>
  
  <div class="pricing-tier">
    <h3>Enterprise</h3>
    <p class="price"><strong>$99</strong>/month</p>
    <ul class="features">
      <li><strong>Unlimited Storage</strong></li>
      <li><strong>24/7 Support</strong></li>
      <li><strong>Unlimited Users</strong></li>
      <li><strong>Custom Solutions</strong></li>
    </ul>
  </div>
</div>

<style>
.pricing-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin: 2rem 0;
}

.pricing-tier {
  background: white;
  border: 2px solid #e9ecef;
  border-radius: 8px;
  padding: 2rem;
  text-align: center;
}

.pricing-tier.featured {
  border-color: #007bff;
  transform: scale(1.05);
  box-shadow: 0 4px 15px rgba(0,123,255,0.1);
}

.price {
  font-size: 2em;
  margin: 1rem 0;
  color: #007bff;
}

.features {
  list-style: none;
  padding: 0;
  text-align: left;
}

.features li {
  padding: 0.5rem 0;
  border-bottom: 1px solid #f8f9fa;
}

@media (max-width: 768px) {
  .pricing-tier.featured {
    transform: none;
  }
  
  .pricing-grid {
    gap: 1rem;
  }
}
</style>
```

---

## Notes

* **Semantic vs. presentational**: 
  - `<strong>` conveys importance (semantic)
  - `<b>` conveys stylistic boldness without semantic meaning (presentational)
  - CSS `font-weight: bold` is purely presentational
* **Nesting behavior**: Multiple nested `<strong>` elements indicate increasing levels of importance
* **Accessibility considerations**:
  - Screen readers may change vocal emphasis for `<strong>` content
  - Don't use `<strong>` for purely visual emphasis without semantic importance
  - Consider using ARIA attributes when dynamic content requires strong emphasis
* **Browser support**: Universally supported across all browsers
* **Common misuse**:
  - Using `<strong>` for purely visual bold styling without semantic importance
  - Overusing `<strong>` which can dilute its semantic impact
  - Confusing with `<em>` which indicates emphasis rather than importance
* **Styling flexibility**: 
  - Default bold styling can be overridden with CSS
  - Can be styled with color, background, or other visual cues
  - Maintain sufficient color contrast for accessibility
* **SEO best practices**:
  - Use for genuinely important content, not keyword stuffing
  - Search engines may interpret nested `<strong>` as indicating importance hierarchy
  - Avoid excessive use which can be seen as manipulative
* **Internationalization**: 
  - Importance conveyed by `<strong>` is culturally universal
  - Consider how emphasis is perceived in different languages and cultures
* **Performance**: Minimal performance impact as it's a simple inline element

---
