# `<dd>`

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

The `<dd>` (description details) element provides the description, definition, or value for the preceding term (`<dt>`) in a description list (`<dl>`). It represents the descriptive portion of a name-value pair, containing the explanation, details, or data that corresponds to one or more preceding terms within the same description list group.

---

## Syntax and Variants

+ **Standard syntax**: `<dd>...</dd>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain flow content
+ **No self-closing variant**: Must contain content
+ **Pair element**: Always follows `<dt>` elements within `<dl>`

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies on semantic role within description list
+ **Commonly used**: `class`, `id` for styling and scripting

---

## Content Model

+ **Permitted content**: Flow content
+ **Allowed content**:
  - Text and phrasing content
  - Paragraphs, headings, lists, and other block elements
  - Images, videos, and other embedded content
  - Interactive elements and form controls
+ **Rich content support**: Can contain complex HTML structures
+ **No restrictions**: Unlike `<dt>`, can contain any flow content

---

## Context

+ **Required parent**: Must be a direct child of `<dl>` element
+ **Sibling relationships**:
  - Must be preceded by one or more `<dt>` elements in the same group
  - Can be followed by other `<dd>` elements for multiple descriptions
  - Can be followed by new `<dt>`-`<dd>` groups
+ **Group structure**: Part of term-description groups within the `<dl>`

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - `margin-left: 40px` (indentation from the term)
  - No top or bottom margins by default
+ **Semantic meaning**:
  - Represents the description or value for preceding terms
  - Screen readers announce as the description part of term-description pairs
  - Creates associative relationship with preceding `<dt>` elements
+ **Accessibility**: Helps screen reader users understand the descriptive content associated with terms

---

## Examples

**Basic description details in glossary:**
```html
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language - the standard markup language for creating web pages</dd>
  
  <dt>CSS</dt>
  <dd>Cascading Style Sheets - used for describing the presentation of web pages</dd>
  
  <dt>JavaScript</dt>
  <dd>A programming language that enables interactive web pages and applications</dd>
</dl>
```

**Multiple descriptions for single term:**
```html
<dl>
  <dt>Cloud Computing</dt>
  <dd>The delivery of computing services over the internet</dd>
  <dd>Enables on-demand access to computing resources</dd>
  <dd>Includes services like storage, processing, and databases</dd>
</dl>
```

**Rich content in description details:**
```html
<dl>
  <dt>Progressive Enhancement</dt>
  <dd>
    <p>A web design strategy that emphasizes core webpage content first, then adds more sophisticated layers of presentation and functionality.</p>
    <p><strong>Key principles:</strong></p>
    <ul>
      <li>Basic content accessible to all browsers</li>
      <li>Enhanced functionality for capable browsers</li>
      <li>External CSS and JavaScript for presentation and behavior</li>
    </ul>
  </dd>
  
  <dt>Responsive Design</dt>
  <dd>
    <p>An approach to web design that makes web pages render well on a variety of devices and window sizes.</p>
    <div class="example">
      <strong>Example techniques:</strong>
      <code>@media queries, fluid grids, flexible images</code>
    </div>
  </dd>
</dl>
```

**Styled description details with classes:**
```html
<dl class="api-docs">
  <dt>GET /api/users</dt>
  <dd class="endpoint-description">
    Retrieves a list of all users in the system. Supports pagination and filtering.
  </dd>
  <dd class="response-example">
    <pre><code>{
  "users": [
    {"id": 1, "name": "John Doe", "email": "john@example.com"},
    {"id": 2, "name": "Jane Smith", "email": "jane@example.com"}
  ],
  "total": 2,
  "page": 1
}</code></pre>
  </dd>
  
  <dt>POST /api/users</dt>
  <dd class="endpoint-description">
    Creates a new user account. Requires authentication and valid user data.
  </dd>
</dl>
```

**Interactive description details:**
```html
<dl class="faq-list">
  <dt>What is your return policy?</dt>
  <dd id="return-policy" class="faq-answer">
    <p>We offer a 30-day money-back guarantee on all products. To be eligible for a return:</p>
    <ul>
      <li>Items must be in original condition</li>
      <li>All packaging and accessories must be included</li>
      <li>Return request must be made within 30 days of purchase</li>
    </ul>
    <button class="contact-support" onclick="openSupportChat()">
      Contact Support for Returns
    </button>
  </dd>
  
  <dt>Do you offer technical support?</dt>
  <dd id="tech-support" class="faq-answer">
    <p>Yes, we provide comprehensive technical support through multiple channels:</p>
    <div class="support-options">
      <div class="option">
        <strong>Email:</strong> support@example.com
      </div>
      <div class="option">
        <strong>Phone:</strong> 1-800-123-4567
      </div>
      <div class="option">
        <strong>Live Chat:</strong> Available 24/7
      </div>
    </div>
  </dd>
</dl>
```

**Accessible description details with ARIA:**
```html
<dl aria-labelledby="specifications-heading">
  <dt id="cpu-spec" role="term">Processor</dt>
  <dd role="definition" aria-labelledby="cpu-spec">
    Apple M2 chip with 8-core CPU, 10-core GPU, and 16-core Neural Engine
  </dd>
  
  <dt id="memory-spec" role="term">Memory</dt>
  <dd role="definition" aria-labelledby="memory-spec">
    8GB unified memory for fluid multitasking
  </dd>
  
  <dt id="storage-spec" role="term">Storage</dt>
  <dd role="definition" aria-labelledby="storage-spec">
    512GB SSD for fast data access and ample storage space
  </dd>
</dl>
```

**Description details with embedded media:**
```html
<dl class="tutorial-steps">
  <dt>Step 1: Environment Setup</dt>
  <dd>
    <p>Install Node.js and npm on your system:</p>
    <pre><code># Download from nodejs.org
# Verify installation
node --version
npm --version</code></pre>
    <div class="note">
      <strong>Note:</strong> We recommend using Node.js version 16 or higher.
    </div>
  </dd>
  
  <dt>Step 2: Project Initialization</dt>
  <dd>
    <p>Create a new project directory and initialize it:</p>
    <pre><code>mkdir my-project
cd my-project
npm init -y</code></pre>
    <img src="terminal-screenshot.png" alt="Terminal showing project initialization commands">
  </dd>
</dl>
```

**Multiple description details with different content types:**
```html
<dl class="product-info">
  <dt>Smartphone X200</dt>
  <dd class="product-image">
    <img src="smartphone-x200.jpg" alt="Smartphone X200 front and back views">
  </dd>
  <dd class="product-description">
    <p>Flagship smartphone with advanced camera system and all-day battery life.</p>
    <div class="features">
      <span class="feature-tag">5G Ready</span>
      <span class="feature-tag">Wireless Charging</span>
      <span class="feature-tag">IP68 Waterproof</span>
    </div>
  </dd>
  <dd class="product-specs">
    <ul>
      <li>6.7-inch OLED Display</li>
      <li>Triple Camera System (108MP main)</li>
      <li>5000mAh Battery</li>
      <li>256GB Storage</li>
    </ul>
  </dd>
</dl>
```

**Responsive description details with CSS Grid:**
```html
<dl class="responsive-dl">
  <dt>Customer Support</dt>
  <dd class="support-info">
    <div class="support-channel">
      <strong>Phone:</strong> 1-800-123-4567
    </div>
    <div class="support-channel">
      <strong>Email:</strong> support@company.com
    </div>
    <div class="support-channel">
      <strong>Live Chat:</strong> Available 24/7
    </div>
  </dd>
  
  <dt>Business Hours</dt>
  <dd class="hours-info">
    <div class="hours-day">
      <span>Monday-Friday:</span>
      <span>9:00 AM - 6:00 PM EST</span>
    </div>
    <div class="hours-day">
      <span>Saturday:</span>
      <span>10:00 AM - 4:00 PM EST</span>
    </div>
    <div class="hours-day">
      <span>Sunday:</span>
      <span>Closed</span>
    </div>
  </dd>
</dl>

<style>
.responsive-dl {
  display: grid;
  grid-template-columns: 200px 1fr;
  gap: 1rem;
  align-items: start;
}

.responsive-dl dt {
  font-weight: bold;
  margin: 0;
}

.responsive-dl dd {
  margin: 0;
}

@media (max-width: 768px) {
  .responsive-dl {
    grid-template-columns: 1fr;
  }
  
  .responsive-dl dt {
    border-bottom: 2px solid #007acc;
    padding-bottom: 0.5rem;
  }
}
</style>
```

**Description details with form elements:**
```html
<dl class="settings-group">
  <dt>Notification Preferences</dt>
  <dd class="setting-controls">
    <div class="checkbox-group">
      <label>
        <input type="checkbox" name="email-notifications" checked>
        Email notifications
      </label>
      <label>
        <input type="checkbox" name="push-notifications">
        Push notifications
      </label>
      <label>
        <input type="checkbox" name="sms-notifications">
        SMS notifications
      </label>
    </div>
    <button class="save-settings">Save Preferences</button>
  </dd>
  
  <dt>Privacy Settings</dt>
  <dd class="setting-controls">
    <div class="radio-group">
      <label>
        <input type="radio" name="privacy-level" value="public" checked>
        Public profile
      </label>
      <label>
        <input type="radio" name="privacy-level" value="friends">
        Friends only
      </label>
      <label>
        <input type="radio" name="privacy-level" value="private">
        Private
      </label>
    </div>
  </dd>
</dl>
```

---

## Notes

* **Semantic role**: Represents the description or value for preceding terms
* **Content flexibility**: Can contain any flow content, including complex structures
* **Multiple descriptions**: Multiple `<dd>` elements can follow a single `<dt>` or group of `<dt>` elements
* **Accessibility considerations**:
  - Screen readers associate descriptions with their preceding terms
  - Ensure descriptions are meaningful and complete
  - Use ARIA roles carefully as native semantics are usually sufficient
* **CSS styling**:
  - Default left margin provides visual indentation
  - Can be extensively styled for custom layouts
  - Often used with CSS Grid or Flexbox for responsive designs
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using outside of `<dl>` elements
  - Placing before `<dt>` elements
  - Using for general content instead of term descriptions
  - Overlooking the semantic relationship with preceding terms
* **SEO benefits**: Helps search engines understand definitional and descriptive content
* **Mobile usability**: Ensure adequate spacing and readability on small screens
* **Internationalization**: Works well with different languages and writing systems

---
