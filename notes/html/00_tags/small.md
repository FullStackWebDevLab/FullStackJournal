# `<small>`

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

The `<small>` element represents side comments, fine print, copyright notices, licensing information, and other types of text that are typically rendered in a smaller font size. It conveys semantic meaning that the enclosed content represents legal disclaimers, caveats, or secondary information rather than being purely presentational. The element should be used for content that is legally required but not the primary focus of the document.

---

## Syntax & Variants

+ **Standard syntax**: `<small>...</small>`
+ **Not void**: Requires both opening and closing tags
+ **Inline element**: Flows with surrounding text content by default
+ **No self-closing variant**: Must contain text or phrasing content
+ **Nesting permitted**: Can contain other phrasing elements

---

## Attributes

+ **No specific attributes**: The `<small>` element has no attributes specific to its function
+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **Event attributes**: Supports all standard event handlers
+ **No deprecated attributes**: All original functionality remains supported

---

## Content Model

+ **Permitted content**: Phrasing content
+ **Allowed content**:
  - Text and character references
  - Other phrasing elements: `<em>`, `<strong>`, `<span>`, etc.
  - Images and other inline elements when contextually appropriate
+ **Nesting permitted**: Can contain other semantic elements
+ **Text emphasis**: Primarily intended for textual side comments and legal text

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Footer sections for copyright and legal notices
  - Form fields for helper text and disclaimers
  - Product pages for pricing details and restrictions
  - Article footers for publication metadata
  - Navigation elements for supplemental information
+ **No structural restrictions**: Can appear anywhere phrasing content is allowed
+ **Nesting considerations**: Can be nested within most block-level and phrasing elements

---

## Behavior and Semantics

+ **Default display**: Inline element (`display: inline`)
+ **Default styling**:
  - Typically renders as smaller text: `font-size: smaller`
  - Inherits other text properties from parent elements
  - No additional spacing or layout changes
+ **Semantic meaning**:
  - Represents side comments and fine print
  - Indicates legally required disclaimers and caveats
  - Denotes secondary or supplementary information
  - Screen readers interpret as less important content
+ **Accessibility role**:
  - Screen readers may adjust reading tone or speed
  - Helps users identify supplemental information
  - Provides semantic context for text processing tools
+ **Visual hierarchy**: Creates typographic contrast for secondary content

---

## Examples

**Basic copyright notice:**
```html
<footer>
  <p><small>&copy; 2024 Company Name. All rights reserved.</small></p>
</footer>
```

**Form field with legal disclaimer:**
```html
<form>
  <label for="email">Email Address</label>
  <input type="email" id="email" name="email" required>
  <small>We'll never share your email with anyone else.</small>
</form>
```

**Pricing with restrictions:**
```html
<div class="pricing">
  <h3>Pro Plan</h3>
  <p class="price">$29<small>/month</small></p>
  <small>Billed annually. Cancel anytime.</small>
</div>
```

**Article metadata:**
```html
<article>
  <header>
    <h1>Understanding Semantic HTML</h1>
    <p>
      Published on March 15, 2024 
      <small>by Jane Developer</small>
    </p>
  </header>
  <!-- Article content -->
</article>
```

**Multiple small elements in a footer:**
```html
<footer class="site-footer">
  <nav>
    <a href="/privacy">Privacy Policy</a>
    <a href="/terms">Terms of Service</a>
    <a href="/contact">Contact Us</a>
  </nav>
  <p>
    <small>&copy; 2024 Acme Corporation. All rights reserved.</small>
    <small>Patent Pending.</small>
    <small>Prices subject to change without notice.</small>
  </p>
</footer>
```

**Styled small text with CSS:**
```html
<div class="product-card">
  <h3>Premium Widget</h3>
  <p class="price">$49.99<small>excl. tax</small></p>
  <small class="shipping-note">Free shipping on orders over $50</small>
</div>

<style>
.product-card {
  border: 1px solid #ddd;
  padding: 20px;
  border-radius: 8px;
}

.price {
  font-size: 1.5em;
  font-weight: bold;
  color: #2c3e50;
}

.price small {
  font-size: 0.7em;
  color: #7f8c8d;
  font-weight: normal;
}

.shipping-note {
  display: block;
  margin-top: 8px;
  color: #27ae60;
  font-style: italic;
}
</style>
```

**Legal disclaimer in a button:**
```html
<button class="purchase-btn">
  Buy Now - $99
  <small>30-day money-back guarantee</small>
</button>

<style>
.purchase-btn {
  padding: 12px 24px;
  background: #3498db;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 1.1em;
  display: block;
  text-align: center;
}

.purchase-btn small {
  display: block;
  font-size: 0.8em;
  opacity: 0.9;
  margin-top: 4px;
}
</style>
```

**Navigation with supplemental info:**
```html
<nav class="main-nav">
  <ul>
    <li>
      <a href="/products">Products</a>
      <small>New items weekly</small>
    </li>
    <li>
      <a href="/sale">Sale</a>
      <small>Limited time</small>
    </li>
    <li>
      <a href="/support">Support</a>
      <small>24/7 available</small>
    </li>
  </ul>
</nav>

<style>
.main-nav ul {
  list-style: none;
  padding: 0;
}

.main-nav li {
  margin-bottom: 16px;
}

.main-nav a {
  font-size: 1.2em;
  text-decoration: none;
  color: #2c3e50;
  display: block;
}

.main-nav small {
  display: block;
  color: #7f8c8d;
  margin-top: 2px;
}
</style>
```

**Accessible form with multiple small elements:**
```html
<form class="accessible-form">
  <div class="form-group">
    <label for="password">Password</label>
    <input type="password" id="password" name="password" 
           aria-describedby="password-requirements">
    <small id="password-requirements">
      Must be at least 8 characters with one number and one special character.
    </small>
  </div>
  
  <div class="form-group">
    <label>
      <input type="checkbox" name="newsletter">
      Subscribe to newsletter
    </label>
    <small>You can unsubscribe at any time.</small>
  </div>
  
  <button type="submit">Create Account</button>
  <small class="form-disclaimer">
    By creating an account, you agree to our 
    <a href="/terms">Terms of Service</a> and 
    <a href="/privacy">Privacy Policy</a>.
  </small>
</form>

<style>
.accessible-form {
  max-width: 400px;
}

.form-group {
  margin-bottom: 20px;
}

.form-group small {
  display: block;
  margin-top: 4px;
  color: #666;
}

.form-disclaimer {
  margin-top: 16px;
  text-align: center;
}
</style>
```

**Product comparison table:**
```html
<table class="comparison-table">
  <thead>
    <tr>
      <th>Feature</th>
      <th>Basic</th>
      <th>Pro</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Storage</td>
      <td>10GB</td>
      <td>100GB <small>+ backup</small></td>
    </tr>
    <tr>
      <td>Support</td>
      <td>Email only</td>
      <td>24/7 Priority <small>phone & chat</small></td>
    </tr>
    <tr>
      <td>Users</td>
      <td>1 user</td>
      <td>5 users <small>+ $5 per additional</small></td>
    </tr>
  </tbody>
</table>

<style>
.comparison-table {
  width: 100%;
  border-collapse: collapse;
}

.comparison-table th,
.comparison-table td {
  padding: 12px;
  border: 1px solid #ddd;
  text-align: left;
}

.comparison-table small {
  color: #666;
  font-style: italic;
}
</style>
```

**Breadcrumb navigation with small:**
```html
<nav aria-label="Breadcrumb">
  <ol class="breadcrumb">
    <li><a href="/">Home</a></li>
    <li><a href="/products">Products</a></li>
    <li>
      <a href="/products/electronics">Electronics</a>
      <small>12 items</small>
    </li>
    <li aria-current="page">Smartphones</li>
  </ol>
</nav>

<style>
.breadcrumb {
  display: flex;
  list-style: none;
  padding: 0;
  gap: 8px;
}

.breadcrumb li {
  display: flex;
  align-items: center;
  gap: 4px;
}

.breadcrumb li:not(:last-child)::after {
  content: "›";
  margin-left: 8px;
  color: #999;
}

.breadcrumb small {
  font-size: 0.8em;
  color: #666;
}
</style>
```

**Testimonial with citation:**
```html
<blockquote class="testimonial">
  <p>"This product completely transformed our workflow and increased productivity by 40%."</p>
  <footer>
    — Sarah Johnson, <cite>CTO at TechCorp</cite>
    <small>Verified customer</small>
  </footer>
</blockquote>

<style>
.testimonial {
  border-left: 4px solid #3498db;
  padding-left: 20px;
  margin: 20px 0;
}

.testimonial footer {
  margin-top: 12px;
  color: #666;
}

.testimonial small {
  display: block;
  color: #27ae60;
  font-style: italic;
}
</style>
```

**Statistics with small annotations:**
```html
<div class="stats-grid">
  <div class="stat">
    <div class="stat-number">98%</div>
    <div class="stat-label">
      Customer Satisfaction
      <small>Based on 1,247 reviews</small>
    </div>
  </div>
  <div class="stat">
    <div class="stat-number">24/7</div>
    <div class="stat-label">
      Support Availability
      <small>Average response time: 2min</small>
    </div>
  </div>
  <div class="stat">
    <div class="stat-number">99.9%</div>
    <div class="stat-label">
      Uptime Guarantee
      <small>Last 12 months</small>
    </div>
  </div>
</div>

<style>
.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 24px;
  margin: 32px 0;
}

.stat {
  text-align: center;
  padding: 20px;
  background: #f8f9fa;
  border-radius: 8px;
}

.stat-number {
  font-size: 2.5em;
  font-weight: bold;
  color: #2c3e50;
  margin-bottom: 8px;
}

.stat-label {
  color: #666;
}

.stat-label small {
  display: block;
  margin-top: 4px;
  font-size: 0.8em;
  color: #999;
}
</style>
```

**Legal document with nested small elements:**
```html
<article class="legal-document">
  <header>
    <h1>Terms of Service</h1>
    <p><small>Last updated: March 15, 2024</small></p>
  </header>
  
  <section>
    <h2>1. User Responsibilities</h2>
    <p>
      You are responsible for maintaining the confidentiality of your account 
      credentials. <small>This includes not sharing your password with third parties.</small>
    </p>
  </section>
  
  <section>
    <h2>2. Payment Terms</h2>
    <p>
      All payments are due upon receipt. 
      <small>Late payments may be subject to a 1.5% monthly service charge.</small>
    </p>
  </section>
  
  <footer>
    <p>
      <small>
        &copy; 2024 Company Name. These terms are governed by the laws of the State of California.
        <small>Any disputes shall be resolved in the courts of San Francisco County.</small>
      </small>
    </p>
  </footer>
</article>

<style>
.legal-document {
  max-width: 800px;
  line-height: 1.6;
}

.legal-document h1 {
  border-bottom: 2px solid #333;
  padding-bottom: 8px;
}

.legal-document h2 {
  color: #2c3e50;
  margin-top: 32px;
}

.legal-document small {
  color: #666;
}

.legal-document small small {
  color: #888;
  font-size: 0.9em;
}
</style>
```

**Pricing tier with multiple small annotations:**
```html
<div class="pricing-tier featured">
  <header>
    <h3>Enterprise</h3>
    <div class="price">
      $199<small>/month</small>
    </div>
    <small>Billed annually</small>
  </header>
  
  <ul class="features">
    <li>Unlimited users</li>
    <li>500GB storage</li>
    <li>Priority support <small>15min response time</small></li>
    <li>Custom integrations <small>up to 5 included</small></li>
    <li>Advanced analytics <small>with custom reports</small></li>
  </ul>
  
  <footer>
    <button class="cta-button">Start Free Trial</button>
    <small>14-day trial, no credit card required</small>
  </footer>
</div>

<style>
.pricing-tier {
  border: 2px solid #e9ecef;
  border-radius: 12px;
  padding: 32px;
  text-align: center;
}

.pricing-tier.featured {
  border-color: #3498db;
  background: #f8fbff;
}

.price {
  font-size: 3em;
  font-weight: bold;
  color: #2c3e50;
  margin: 16px 0;
}

.price small {
  font-size: 0.4em;
  color: #7f8c8d;
  font-weight: normal;
}

.features {
  list-style: none;
  padding: 0;
  margin: 24px 0;
  text-align: left;
}

.features li {
  padding: 8px 0;
  border-bottom: 1px solid #f0f0f0;
}

.features small {
  color: #666;
  font-style: italic;
}

.cta-button {
  width: 100%;
  padding: 12px;
  background: #3498db;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 1.1em;
  margin-bottom: 12px;
}
</style>
```

**Accessibility-enhanced small text:**
```html
<div class="notification">
  <h3>Security Update Available</h3>
  <p>
    A new security patch is ready for installation. 
    <small class="sr-only">
      This update addresses critical vulnerabilities and is recommended for all users.
    </small>
  </p>
  <button>Install Update</button>
  <small aria-hidden="true">Recommended</small>
</div>

<style>
.sr-only {
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

.notification {
  border: 1px solid #e3f2fd;
  background: #f3f8ff;
  padding: 20px;
  border-radius: 8px;
  margin: 20px 0;
}

.notification small[aria-hidden="true"] {
  color: #2196f3;
  font-weight: bold;
}
</style>
```

---

## Notes

* **Semantic vs. Presentational use**:
  - Should be used for semantically "small print" content, not just small text
  - Avoid using purely for visual size reduction without semantic meaning
  - Use CSS `font-size` for purely presentational size changes

* **Nesting behavior**:
  - Multiple `<small>` elements can further reduce semantic importance
  - Visual rendering typically shows progressively smaller text
  - Screen readers interpret nested small as increasingly secondary content

* **Accessibility considerations**:
  - Screen readers may treat content as less important
  - Provides semantic context for assistive technologies
  - Should not be used to hide important information
  - Consider using `aria-label` or `aria-describedby` for complex cases

* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using `<small>` purely for visual styling without semantic need
  - Overusing small text, making content difficult to read
  - Hiding important information in small print
  - Using for entire paragraphs when only parts need emphasis

* **Styling flexibility**:
  - Can be styled with CSS to override default smaller size
  - Should maintain visual distinction from surrounding text
  - Can be combined with other semantic elements for layered meaning

* **Legal and compliance**:
  - Essential for required legal disclaimers and terms
  - Helps meet regulatory requirements for clear communication
  - Should not be used to obscure important contractual terms

* **Best practices**:
  - Use for legally required disclaimers and caveats
  - Apply to supplementary information, not primary content
  - Ensure text remains readable (consider minimum font sizes)
  - Maintain adequate color contrast for accessibility
  - Use sparingly to maintain effectiveness

* **Mobile considerations**:
  - Ensure small text remains readable on mobile devices
  - Consider responsive font sizing for different screen sizes
  - Test touch targets if small text is interactive

* **SEO implications**:
  - Search engines understand semantic meaning of small elements
  - Content within small is still indexed and considered
  - Should not be used for keyword stuffing or hidden text

* **Alternative approaches**:
  - Use CSS classes for purely visual size reduction
  - Use `<span>` with appropriate ARIA roles for custom semantics
  - Use `<footer>` for section-level supplementary content
  - Consider progressive disclosure for complex legal text

---
