# `<dl>`

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

The `<dl>` (description list) element represents a description list, which consists of groups of terms (`<dt>`) and descriptions (`<dd>`). It is used to display name-value pairs, definitions, metadata, FAQs, and other associative relationships where each term has one or more corresponding descriptions or values.

---

## Syntax and Variants

+ **Standard syntax**: `<dl>...</dl>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps `<dt>` and `<dd>` elements in groups
+ **No self-closing variant**: Must contain description list items
+ **Association list**: Groups terms with their descriptions

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies on semantic structure rather than attributes
+ **Commonly used**: `class`, `id` for styling and scripting

---

## Content Model

+ **Permitted content**:
  - Zero or more groups, each consisting of:
    - One or more `<dt>` elements (terms)
    - Followed by one or more `<dd>` elements (descriptions)
+ **Group structure**: Each term-description group forms a logical unit
+ **Flexible grouping**: Multiple terms can share descriptions, multiple descriptions can belong to one term
+ **No other elements**: Should only contain `<dt>` and `<dd>` elements

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<article>`, `<section>` for definition content
  - In glossaries, metadata displays, and FAQ sections
  - For product specifications and key-value pairs
  - Within `<aside>` for supplementary information
+ **Flow content**: Treated as block-level element in document flow

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - `margin-top: 1em`
  - `margin-bottom: 1em`
  - `margin-left: 0`
  - `margin-right: 0`
+ **Semantic meaning**:
  - Represents a description list or association list
  - Screen readers announce the list structure and relationships
  - Conveys term-description relationships to assistive technologies
+ **Accessibility**: Provides clear semantic relationships between terms and their descriptions

---

## Examples

**Basic description list for definitions:**
```html
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language, the standard markup language for web pages</dd>
  
  <dt>CSS</dt>
  <dd>Cascading Style Sheets, used for describing the presentation of web pages</dd>
  
  <dt>JavaScript</dt>
  <dd>A programming language that enables interactive web pages</dd>
</dl>
```

**Multiple descriptions for one term:**
```html
<dl>
  <dt>API</dt>
  <dd>Application Programming Interface</dd>
  <dd>A set of rules and protocols for building software applications</dd>
  <dd>Enables communication between different software components</dd>
</dl>
```

**Multiple terms sharing a description:**
```html
<dl>
  <dt>CEO</dt>
  <dt>Chief Executive Officer</dt>
  <dd>The highest-ranking executive in a company, responsible for making major corporate decisions</dd>
  
  <dt>CTO</dt>
  <dt>Chief Technology Officer</dt>
  <dd>The executive responsible for technological development and innovation within an organization</dd>
</dl>
```

**FAQ section using description list:**
```html
<section aria-labelledby="faq-heading">
  <h2 id="faq-heading">Frequently Asked Questions</h2>
  <dl class="faq-list">
    <dt>What is your return policy?</dt>
    <dd>We offer a 30-day money-back guarantee on all products. Items must be returned in original condition with all packaging.</dd>
    
    <dt>Do you offer international shipping?</dt>
    <dd>Yes, we ship to over 50 countries worldwide. Shipping costs and delivery times vary by location.</dd>
    
    <dt>How can I track my order?</dt>
    <dd>Once your order ships, you'll receive a tracking number via email. You can also track your order through your account dashboard.</dd>
  </dl>
</section>
```

**Product specifications:**
```html
<dl class="product-specs">
  <dt>Dimensions</dt>
  <dd>12.3 × 8.8 × 0.3 inches (312 × 224 × 8 mm)</dd>
  
  <dt>Weight</dt>
  <dd>1.39 pounds (631 grams)</dd>
  
  <dt>Display</dt>
  <dd>13.3-inch Retina display</dd>
  <dd>2560 × 1600 resolution</dd>
  <dd>500 nits brightness</dd>
  
  <dt>Processor</dt>
  <dd>Apple M2 chip</dd>
  <dd>8-core CPU</dd>
  <dd>10-core GPU</dd>
  
  <dt>Memory</dt>
  <dd>8GB unified memory</dd>
  
  <dt>Storage</dt>
  <dd>256GB SSD</dd>
</dl>
```

**Metadata display:**
```html
<dl class="metadata">
  <dt>Published</dt>
  <dd><time datetime="2024-03-15">March 15, 2024</time></dd>
  
  <dt>Author</dt>
  <dd>Sarah Johnson</dd>
  <dd>Senior Technical Writer</dd>
  
  <dt>Category</dt>
  <dd>Web Development</dd>
  
  <dt>Tags</dt>
  <dd>HTML5</dd>
  <dd>Semantic Markup</dd>
  <dd>Accessibility</dd>
  
  <dt>Reading Time</dt>
  <dd>5 minutes</dd>
</dl>
```

**Glossary with styled description list:**
```html
<dl class="glossary">
  <dt class="term">Semantic HTML</dt>
  <dd class="definition">
    The use of HTML markup to reinforce the meaning of the content rather than just define its presentation.
    Semantic elements like <code>&lt;article&gt;</code>, <code>&lt;section&gt;</code>, and <code>&lt;nav&gt;</code>
    make the content more meaningful to both browsers and assistive technologies.
  </dd>
  
  <dt class="term">ARIA</dt>
  <dd class="definition">
    Accessible Rich Internet Applications - a set of attributes that define ways to make web content more accessible
    to people with disabilities. ARIA roles and properties provide additional semantic information to assistive technologies.
  </dd>
  
  <dt class="term">Progressive Enhancement</dt>
  <dd class="definition">
    A strategy for web design that emphasizes core webpage content first, then adds more sophisticated layers of
    presentation and functionality on top of the content as the end-user's browser and internet connection allow.
  </dd>
</dl>
```

**Accessible description list with ARIA:**
```html
<dl role="list" aria-labelledby="contact-info">
  <dt role="listitem">Email</dt>
  <dd role="listitem">
    <a href="mailto:contact@example.com">contact@example.com</a>
  </dd>
  
  <dt role="listitem">Phone</dt>
  <dd role="listitem">
    <a href="tel:+15551234567">(555) 123-4567</a>
  </dd>
  
  <dt role="listitem">Office Hours</dt>
  <dd role="listitem">Monday-Friday: 9:00 AM - 5:00 PM EST</dd>
  <dd role="listitem">Saturday: 10:00 AM - 2:00 PM EST</dd>
  
  <dt role="listitem">Address</dt>
  <dd role="listitem">
    123 Business Avenue<br>
    Suite 100<br>
    New York, NY 10001
  </dd>
</dl>
```

**Complex description list with mixed content:**
```html
<dl class="team-roles">
  <dt>
    <strong>Project Manager</strong>
    <span class="department">Operations</span>
  </dt>
  <dd>
    <p>Responsible for planning, executing, and closing projects according to strict deadlines and within budget.</p>
    <ul>
      <li>Define project scope and objectives</li>
      <li>Coordinate resources and team members</li>
      <li>Track project performance metrics</li>
    </ul>
  </dd>
  
  <dt>
    <strong>Lead Developer</strong>
    <span class="department">Engineering</span>
  </dt>
  <dd>
    <p>Oversees technical implementation and guides the development team in architectural decisions.</p>
    <ul>
      <li>Design system architecture</li>
      <li>Review code and ensure quality standards</li>
      <li>Mentor junior developers</li>
    </ul>
  </dd>
</dl>
```

**Responsive description list with CSS Grid:**
```html
<dl class="responsive-dl">
  <dt>Browser Support</dt>
  <dd>Chrome 90+</dd>
  <dd>Firefox 88+</dd>
  <dd>Safari 14+</dd>
  <dd>Edge 90+</dd>
  
  <dt>File Formats</dt>
  <dd>MP4 (H.264)</dd>
  <dd>WebM (VP9)</dd>
  <dd>MP3</dd>
  <dd>WAV</dd>
</dl>

<style>
.responsive-dl {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 0.5rem 1rem;
}

.responsive-dl dt {
  grid-column: 1;
  font-weight: bold;
}

.responsive-dl dd {
  grid-column: 2;
  margin: 0;
}
</style>
```

---

## Notes

* **Semantic purpose**: Use for term-description relationships, not for dialog or general lists
* **Grouping logic**: Each group of `<dt>` followed by `<dd>` represents one conceptual unit
* **Accessibility benefits**: 
  - Screen readers can navigate between terms and descriptions
  - Provides clear semantic relationships
  - Helps users understand associative content
* **CSS styling**: 
  - Default styling is minimal
  - Can be styled with flexbox, grid, or traditional methods
  - `display: flex` and `display: grid` work well for custom layouts
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using for general layout instead of semantic term-description pairs
  - Mixing `<dt>` and `<dd>` in incorrect order
  - Using without proper grouping structure
  - Confusing with `<ul>` or `<ol>` for non-associative content
* **SEO benefits**: Helps search engines understand definitional and metadata content
* **Mobile considerations**: Ensure adequate spacing and readability on small screens
* **Internationalization**: Works well with both LTR and RTL languages
* **Print styling**: Description lists format well in print media for glossaries and specifications

---
