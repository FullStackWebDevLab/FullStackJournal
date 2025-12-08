# `<address>`

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

The `<address>` element provides contact information for its nearest `<article>` or `<body>` ancestor. It typically contains author, organization, or relevant contact details for the document section. The element semantically identifies contact information rather than arbitrary addresses, distinguishing it from generic location data.

---

## Syntax and Variants

+ **Standard syntax**: `<address>...</address>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain various content types
+ **No self-closing variant**: Must contain contact information
+ **No alternative forms**: Standard syntax only

---

## Attributes

+ **No specific attributes**: The `<address>` element does not have any element-specific attributes
+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, `lang`, `dir`, etc.
+ **Event handlers**: All global event attributes supported

---

## Content Model

+ **Permitted content**: Flow content, but with restrictions
+ **Allowed content**:
  - Text and character references
  - Phrasing elements: `<strong>`, `<em>`, `<span>`, etc.
  - Line breaks and structural elements
  - Contact information in various formats
+ **Restricted content**: 
  - Cannot contain heading content (`<h1>`-`<h6>`)
  - Cannot contain sectioning content (`<article>`, `<section>`, etc.)
  - Cannot contain `<address>` elements (no nesting)
  - Cannot contain other major structural elements that would change the context

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<body>` for general document contact information
  - Within `<article>` for article-specific author contact
  - Within `<footer>` elements for site or section contact details
+ **Scope determination**: Contact information applies to:
  - Entire document when placed in `<body>`
  - Specific article when placed within `<article>`
  - Nearest ancestor article or body context
+ **Unique constraints**: No nesting of `<address>` elements permitted

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - `font-style: italic` (most browsers)
  - No additional inherent visual styling
  - Inherits text properties from parent elements
+ **Semantic meaning**:
  - Indicates contact information for relevant context
  - Provides machine-readable contact data
  - Enhances document structure for assistive technologies
+ **Accessibility role**:
  - Implicit ARIA role: `group`
  - Screen readers announce as contact information
  - Helps users identify relevant contact details
+ **SEO significance**: Helps search engines identify and associate contact information with content

---

## Examples

**Basic contact information in body context:**
```html
<address>
  Contact the website authors at <a href="mailto:webmaster@example.com">webmaster@example.com</a>.
</address>
```

**Author contact within an article:**
```html
<article>
  <h1>Understanding Semantic HTML</h1>
  <p>Article content here...</p>
  
  <address>
    Written by <a href="mailto:author@example.com">John Smith</a>.<br>
    Visit us at:<br>
    Example Company<br>
    123 Main Street, Suite 100<br>
    Anytown, CA 12345
  </address>
</article>
```

**Corporate contact in footer:**
```html
<footer>
  <address>
    <strong>Acme Corporation</strong><br>
    123 Business Avenue<br>
    Suite 500<br>
    New York, NY 10001<br>
    Phone: <a href="tel:+1-555-123-4567">(555) 123-4567</a><br>
    Email: <a href="mailto:info@acme.com">info@acme.com</a>
  </address>
  
  <p>&copy; 2024 Acme Corporation. All rights reserved.</p>
</footer>
```

**Styled address with multiple contact methods:**
```html
<address class="contact-card">
  <h3>Contact Information</h3>
  <div class="contact-item">
    <span class="contact-label">Address:</span>
    <span class="contact-value">456 Innovation Drive, Tech City, TC 98765</span>
  </div>
  <div class="contact-item">
    <span class="contact-label">Phone:</span>
    <a href="tel:+1-555-987-6543" class="contact-value">(555) 987-6543</a>
  </div>
  <div class="contact-item">
    <span class="contact-label">Email:</span>
    <a href="mailto:support@company.com" class="contact-value">support@company.com</a>
  </div>
</address>

<style>
.contact-card {
  font-style: normal;
  background: #f8f9fa;
  border: 1px solid #dee2e6;
  border-radius: 8px;
  padding: 20px;
  margin: 20px 0;
}

.contact-card h3 {
  margin-top: 0;
  color: #2c3e50;
  border-bottom: 2px solid #3498db;
  padding-bottom: 8px;
}

.contact-item {
  display: flex;
  margin-bottom: 12px;
  align-items: flex-start;
}

.contact-label {
  font-weight: 600;
  min-width: 80px;
  color: #34495e;
}

.contact-value {
  flex: 1;
  color: #2c3e50;
}

.contact-value a {
  color: #2980b9;
  text-decoration: none;
}

.contact-value a:hover {
  text-decoration: underline;
  color: #1a5276;
}

@media (max-width: 768px) {
  .contact-item {
    flex-direction: column;
  }
  
  .contact-label {
    margin-bottom: 4px;
  }
}
</style>
```

**Multiple authors in article context:**
```html
<article>
  <h1>Research Paper on Web Standards</h1>
  
  <section>
    <h2>Abstract</h2>
    <p>Research content here...</p>
  </section>
  
  <address class="authors">
    <h3>Corresponding Authors</h3>
    <div class="author">
      <strong>Dr. Sarah Johnson</strong><br>
      Department of Computer Science<br>
      University of Technology<br>
      Email: <a href="mailto:s.johnson@university.edu">s.johnson@university.edu</a>
    </div>
    
    <div class="author">
      <strong>Prof. Michael Chen</strong><br>
      Institute of Web Research<br>
      Tech Institute<br>
      Email: <a href="mailto:m.chen@techinstitute.edu">m.chen@techinstitute.edu</a>
    </div>
  </address>
</article>

<style>
.authors {
  font-style: normal;
  background: #fff3cd;
  border-left: 4px solid #ffc107;
  padding: 15px;
  margin-top: 30px;
}

.authors h3 {
  margin-top: 0;
  color: #856404;
}

.author {
  margin-bottom: 15px;
  padding-bottom: 15px;
  border-bottom: 1px solid #ffeaa7;
}

.author:last-child {
  margin-bottom: 0;
  padding-bottom: 0;
  border-bottom: none;
}
</style>
```

**Business directory with multiple addresses:**
```html
<section class="business-directory">
  <h2>Our Office Locations</h2>
  
  <div class="office-grid">
    <article class="office">
      <h3>Headquarters</h3>
      <address>
        <strong>Global Solutions Inc.</strong><br>
        123 Corporate Plaza<br>
        Downtown District<br>
        New York, NY 10001<br>
        <a href="tel:+1-212-555-1000">(212) 555-1000</a>
      </address>
    </article>
    
    <article class="office">
      <h3>West Coast Office</h3>
      <address>
        <strong>Global Solutions West</strong><br>
        456 Innovation Drive<br>
        Tech Park<br>
        San Francisco, CA 94105<br>
        <a href="tel:+1-415-555-2000">(415) 555-2000</a>
      </address>
    </article>
    
    <article class="office">
      <h3>European Office</h3>
      <address>
        <strong>Global Solutions Europe</strong><br>
        789 International Avenue<br>
        Business Quarter<br>
        London, UK SE1 9GG<br>
        <a href="tel:+44-20-7946-0958">+44 20 7946 0958</a>
      </address>
    </article>
  </div>
</section>

<style>
.business-directory {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.office-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.office {
  background: white;
  border: 1px solid #e1e8ed;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.office h3 {
  margin-top: 0;
  color: #2c3e50;
  border-bottom: 2px solid #3498db;
  padding-bottom: 8px;
}

.office address {
  font-style: normal;
  line-height: 1.6;
}

.office a {
  color: #2980b9;
  text-decoration: none;
}

.office a:hover {
  text-decoration: underline;
}
</style>
```

**Accessible address with ARIA enhancements:**
```html
<address aria-labelledby="contact-heading" class="accessible-contact">
  <h3 id="contact-heading">Customer Service Contact</h3>
  
  <div class="contact-method" role="listitem">
    <span class="method-icon" aria-hidden="true">📍</span>
    <div>
      <strong>Visit Us:</strong><br>
      123 Customer Service Lane<br>
      Support City, SC 54321
    </div>
  </div>
  
  <div class="contact-method" role="listitem">
    <span class="method-icon" aria-hidden="true">📞</span>
    <div>
      <strong>Call Us:</strong><br>
      <a href="tel:+1-800-555-HELP" aria-label="Call 1-800-555-HELP">1-800-555-HELP</a><br>
      Available 24/7
    </div>
  </div>
  
  <div class="contact-method" role="listitem">
    <span class="method-icon" aria-hidden="true">✉️</span>
    <div>
      <strong>Email Us:</strong><br>
      <a href="mailto:support@company.com">support@company.com</a><br>
      Response within 24 hours
    </div>
  </div>
</address>

<style>
.accessible-contact {
  font-style: normal;
  background: #e8f4f8;
  border: 1px solid #b8dde9;
  border-radius: 8px;
  padding: 20px;
  margin: 20px 0;
}

.accessible-contact h3 {
  margin-top: 0;
  color: #2c5e7a;
}

.contact-method {
  display: flex;
  align-items: flex-start;
  margin-bottom: 15px;
  padding: 10px;
  background: white;
  border-radius: 6px;
}

.method-icon {
  font-size: 1.5em;
  margin-right: 15px;
  min-width: 30px;
}

.contact-method:last-child {
  margin-bottom: 0;
}

.contact-method a {
  color: #2c5e7a;
  text-decoration: none;
  font-weight: 500;
}

.contact-method a:hover {
  text-decoration: underline;
}
</style>
```

**Address with social media contacts:**
```html
<address class="social-contact">
  <h3>Connect With Us</h3>
  
  <div class="contact-section">
    <h4>Physical Location</h4>
    <p>
      789 Social Media Avenue<br>
      Digital District, DD 10101
    </p>
  </div>
  
  <div class="contact-section">
    <h4>Digital Presence</h4>
    <div class="social-links">
      <a href="https://twitter.com/company" class="social-link twitter" aria-label="Follow us on Twitter">
        <span aria-hidden="true">🐦</span> Twitter
      </a>
      <a href="https://linkedin.com/company" class="social-link linkedin" aria-label="Connect on LinkedIn">
        <span aria-hidden="true">💼</span> LinkedIn
      </a>
      <a href="https://github.com/company" class="social-link github" aria-label="View our GitHub">
        <span aria-hidden="true">🐙</span> GitHub
      </a>
    </div>
  </div>
  
  <div class="contact-section">
    <h4>Direct Contact</h4>
    <p>
      Email: <a href="mailto:hello@company.com">hello@company.com</a><br>
      Support: <a href="mailto:support@company.com">support@company.com</a>
    </p>
  </div>
</address>

<style>
.social-contact {
  font-style: normal;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 12px;
  padding: 30px;
  margin: 20px 0;
}

.social-contact h3,
.social-contact h4 {
  color: white;
  margin-top: 0;
}

.social-contact h3 {
  border-bottom: 2px solid rgba(255,255,255,0.3);
  padding-bottom: 10px;
  margin-bottom: 20px;
}

.contact-section {
  margin-bottom: 25px;
}

.contact-section:last-child {
  margin-bottom: 0;
}

.social-links {
  display: flex;
  gap: 15px;
  flex-wrap: wrap;
}

.social-link {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 10px 15px;
  background: rgba(255,255,255,0.1);
  border: 1px solid rgba(255,255,255,0.3);
  border-radius: 6px;
  color: white;
  text-decoration: none;
  transition: all 0.3s ease;
}

.social-link:hover {
  background: rgba(255,255,255,0.2);
  transform: translateY(-2px);
}

.social-contact a:not(.social-link) {
  color: #a3bffa;
  text-decoration: none;
}

.social-contact a:not(.social-link):hover {
  text-decoration: underline;
}
</style>
```

**Responsive address layout:**
```html
<address class="responsive-address">
  <div class="address-header">
    <h3>Corporate Headquarters</h3>
    <p class="address-subtitle">Main Office and Executive Team</p>
  </div>
  
  <div class="address-grid">
    <div class="address-item">
      <div class="address-icon">🏢</div>
      <div class="address-content">
        <strong>Office Address</strong>
        <p>123 Corporate Tower<br>Business District<br>Metropolis, MP 12345</p>
      </div>
    </div>
    
    <div class="address-item">
      <div class="address-icon">📞</div>
      <div class="address-content">
        <strong>Phone Numbers</strong>
        <p>
          Main: <a href="tel:+1-555-123-4567">(555) 123-4567</a><br>
          Fax: <a href="tel:+1-555-123-4568">(555) 123-4568</a>
        </p>
      </div>
    </div>
    
    <div class="address-item">
      <div class="address-icon">✉️</div>
      <div class="address-content">
        <strong>Email Contacts</strong>
        <p>
          General: <a href="mailto:info@company.com">info@company.com</a><br>
          Support: <a href="mailto:support@company.com">support@company.com</a>
        </p>
      </div>
    </div>
    
    <div class="address-item">
      <div class="address-icon">🕒</div>
      <div class="address-content">
        <strong>Business Hours</strong>
        <p>
          Monday-Friday: 9AM-6PM<br>
          Saturday: 10AM-4PM<br>
          Sunday: Closed
        </p>
      </div>
    </div>
  </div>
</address>

<style>
.responsive-address {
  font-style: normal;
  background: white;
  border: 1px solid #e1e8ed;
  border-radius: 12px;
  padding: 0;
  margin: 20px 0;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0,0,0,0.05);
}

.address-header {
  background: #2c3e50;
  color: white;
  padding: 25px;
  text-align: center;
}

.address-header h3 {
  margin: 0 0 8px 0;
  color: white;
  font-size: 1.5em;
}

.address-subtitle {
  margin: 0;
  opacity: 0.8;
  font-size: 0.9em;
}

.address-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 0;
}

.address-item {
  display: flex;
  align-items: flex-start;
  padding: 25px;
  border-bottom: 1px solid #f1f3f4;
}

.address-item:nth-child(odd) {
  background: #fafbfc;
}

.address-item:last-child {
  border-bottom: none;
}

.address-icon {
  font-size: 1.8em;
  margin-right: 15px;
  min-width: 40px;
}

.address-content strong {
  display: block;
  margin-bottom: 8px;
  color: #2c3e50;
  font-size: 1.1em;
}

.address-content p {
  margin: 0;
  line-height: 1.6;
  color: #5f6368;
}

.address-content a {
  color: #3498db;
  text-decoration: none;
}

.address-content a:hover {
  text-decoration: underline;
}

@media (max-width: 768px) {
  .address-grid {
    grid-template-columns: 1fr;
  }
  
  .address-item {
    padding: 20px;
  }
  
  .address-header {
    padding: 20px;
  }
}

@media (max-width: 480px) {
  .address-item {
    flex-direction: column;
    text-align: center;
  }
  
  .address-icon {
    margin-right: 0;
    margin-bottom: 10px;
  }
}
</style>
```

---

## Notes

* **Scope limitation**: Contact information applies to the nearest `<article>` or `<body>` ancestor, not arbitrary document sections
* **Content restrictions**: Cannot contain heading elements, sectioning content, or nested `<address>` elements
* **Common misuse**: 
  - Using for arbitrary postal addresses without contact context
  - Placing in incorrect context (e.g., within `<nav>` or `<aside>` without proper association)
  - Including non-contact information within the element
* **Styling considerations**:
  - Default italic styling can be overridden with CSS
  - No inherent layout properties beyond block display
  - Responsive design patterns recommended for complex contact information
* **Accessibility best practices**:
  - Use clear, structured contact information
  - Include multiple contact methods when possible
  - Ensure proper contrast ratios for styled addresses
  - Use semantic markup within the address when appropriate
* **Browser support**: Universally supported across all modern browsers
* **HTML5 changes**: 
  - Scope explicitly defined to nearest `<article>` or `<body>`
  - Content model restrictions clarified
  - Semantic meaning strengthened for machine readability
* **SEO impact**: Helps search engines identify and associate contact information with organizations and authors
* **Internationalization**: Consider different address formats and contact methods for global audiences
* **Mobile optimization**: Ensure clickable elements (phone numbers, emails) are easily tappable on touch devices

---
