# `<dt>`

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

The `<dt>` (description term) element specifies a term in a description list (`<dl>`). It represents the name or label portion of a name-value pair, serving as the identifier that is being described or defined by one or more subsequent `<dd>` (description details) elements within the same description list group.

---

## Syntax and Variants

+ **Standard syntax**: `<dt>...</dt>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain phrasing content
+ **No self-closing variant**: Must contain content
+ **Pair element**: Always used in conjunction with `<dd>` within `<dl>`

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies on semantic role within description list
+ **Commonly used**: `id`, `class` for styling and linking

---

## Content Model

+ **Permitted content**: Flow content, but with no `<header>`, `<footer>`, sectioning content, or heading content descendants
+ **Allowed content**:
  - Text and phrasing content
  - Links, spans, emphasis elements
  - Images and other inline elements
+ **Restricted content**: Cannot contain block-level elements like `<div>`, `<p>`, or heading elements
+ **Inline focus**: Primarily intended for term names, not complex content

---

## Context

+ **Required parent**: Must be a direct child of `<dl>` element
+ **Sibling relationships**:
  - Must be followed by one or more `<dd>` elements in the same group
  - Can be preceded by other `<dt>` or `<dd>` elements in different groups
  - Multiple `<dt>` elements can be grouped together before `<dd>` elements
+ **Group structure**: Part of term-description groups within the `<dl>`

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - No default margins or padding
  - Typically appears on its own line
  - Font weight may be normal (varies by browser)
+ **Semantic meaning**:
  - Represents a term being defined or described
  - Screen readers announce as part of description list structure
  - Creates associative relationship with following `<dd>` elements
+ **Accessibility**: Helps screen reader users understand term-description relationships

---

## Examples

**Basic description term in glossary:**
```html
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language</dd>
  
  <dt>CSS</dt>
  <dd>Cascading Style Sheets</dd>
  
  <dt>JavaScript</dt>
  <dd>A programming language for interactive web pages</dd>
</dl>
```

**Multiple terms sharing descriptions:**
```html
<dl>
  <dt>CEO</dt>
  <dt>Chief Executive Officer</dt>
  <dd>The highest-ranking executive in a company</dd>
  
  <dt>CTO</dt>
  <dt>Chief Technology Officer</dt>
  <dd>Executive responsible for technological strategy</dd>
</dl>
```

**Styled terms with classes and IDs:**
```html
<dl class="api-documentation">
  <dt id="endpoint-get-users" class="endpoint-term">GET /api/users</dt>
  <dd>Retrieve a list of all users in the system</dd>
  
  <dt id="endpoint-post-users" class="endpoint-term">POST /api/users</dt>
  <dd>Create a new user account</dd>
  
  <dt id="endpoint-put-users" class="endpoint-term">PUT /api/users/{id}</dt>
  <dd>Update an existing user's information</dd>
</dl>
```

**Terms with inline formatting:**
```html
<dl>
  <dt><strong>Semantic HTML</strong></dt>
  <dd>HTML that introduces meaning to the web page rather than just presentation</dd>
  
  <dt><code>&lt;article&gt;</code> element</dt>
  <dd>Represents self-contained composition in a document</dd>
  
  <dt><em>Progressive Enhancement</em></dt>
  <dd>Strategy that emphasizes core content first, then enhances with additional features</dd>
</dl>
```

**Accessible terms with ARIA attributes:**
```html
<dl aria-labelledby="faq-heading">
  <dt id="q1" role="term" aria-expanded="false">
    <button onclick="toggleAnswer('a1')">
      What is your return policy?
    </button>
  </dt>
  <dd id="a1" role="definition" aria-labelledby="q1" hidden>
    We offer a 30-day money-back guarantee on all products.
  </dd>
  
  <dt id="q2" role="term" aria-expanded="false">
    <button onclick="toggleAnswer('a2')">
      Do you offer international shipping?
    </button>
  </dt>
  <dd id="a2" role="definition" aria-labelledby="q2" hidden>
    Yes, we ship to over 50 countries worldwide.
  </dd>
</dl>
```

**Terms in product specifications:**
```html
<dl class="product-specs">
  <dt class="spec-name">Dimensions</dt>
  <dd class="spec-value">12.3 × 8.8 × 0.3 inches</dd>
  
  <dt class="spec-name">Weight</dt>
  <dd class="spec-value">1.39 pounds (631 grams)</dd>
  
  <dt class="spec-name">Display</dt>
  <dd class="spec-value">13.3-inch Retina display</dd>
  <dd class="spec-value">2560 × 1600 resolution</dd>
  
  <dt class="spec-name">Processor</dt>
  <dd class="spec-value">Apple M2 chip with 8-core CPU</dd>
</dl>
```

**Interactive terms with JavaScript:**
```html
<dl class="interactive-glossary">
  <dt data-term="ajax" class="glossary-term">
    AJAX
    <span class="term-icon" aria-hidden="true">ℹ️</span>
  </dt>
  <dd class="glossary-definition">
    Asynchronous JavaScript and XML - a technique for creating fast and dynamic web pages.
  </dd>
  
  <dt data-term="api" class="glossary-term">
    API
    <span class="term-icon" aria-hidden="true">ℹ️</span>
  </dt>
  <dd class="glossary-definition">
    Application Programming Interface - a set of rules for building software applications.
  </dd>
</dl>

<script>
document.querySelectorAll('.glossary-term').forEach(term => {
  term.addEventListener('click', () => {
    const definition = term.nextElementSibling;
    definition.classList.toggle('active');
  });
});
</script>
```

**Metadata terms with semantic markup:**
```html
<dl class="document-metadata">
  <dt>Published</dt>
  <dd><time datetime="2024-03-15">March 15, 2024</time></dd>
  
  <dt>Author</dt>
  <dd>
    <a href="/author/sarah-johnson" rel="author">Sarah Johnson</a>
  </dd>
  
  <dt>Category</dt>
  <dd><a href="/category/web-development">Web Development</a></dd>
  
  <dt>Tags</dt>
  <dd>
    <span class="tag">HTML5</span>
    <span class="tag">Semantic</span>
    <span class="tag">Accessibility</span>
  </dd>
</dl>
```

**Complex terms with multiple inline elements:**
```html
<dl class="technical-specs">
  <dt>
    <span class="spec-label">Network Protocol</span>
    <code class="protocol-version">HTTP/2</code>
  </dt>
  <dd>Binary protocol for improved performance over HTTP/1.1</dd>
  
  <dt>
    <span class="spec-label">Security</span>
    <span class="security-badge">TLS 1.3</span>
  </dt>
  <dd>Latest encryption standard for secure communications</dd>
  
  <dt>
    <span class="spec-label">Compression</span>
    <span class="compression-method">Brotli</span>
  </dt>
  <dd>Advanced compression algorithm for smaller file sizes</dd>
</dl>
```

**Responsive terms with CSS Grid layout:**
```html
<dl class="responsive-specs">
  <dt class="spec-term">Screen Size</dt>
  <dd class="spec-detail">13.3 inches</dd>
  
  <dt class="spec-term">Resolution</dt>
  <dd class="spec-detail">2560 × 1600 pixels</dd>
  
  <dt class="spec-term">Processor</dt>
  <dd class="spec-detail">Apple M2 chip</dd>
  
  <dt class="spec-term">Memory</dt>
  <dd class="spec-detail">8GB unified memory</dd>
</dl>

<style>
.responsive-specs {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 0.75rem;
}

.spec-term {
  font-weight: 600;
  color: #333;
}

.spec-detail {
  margin: 0;
  color: #666;
}

@media (max-width: 768px) {
  .responsive-specs {
    grid-template-columns: 1fr;
  }
  
  .spec-term {
    border-bottom: 1px solid #eee;
    padding-bottom: 0.25rem;
  }
}
</style>
```

---

## Notes

* **Semantic role**: Represents the term being defined, not the definition itself
* **Content restrictions**: Should not contain block-level elements; keep content inline
* **Grouping behavior**: Multiple `<dt>` elements can be grouped before `<dd>` elements
* **Accessibility considerations**:
  - Screen readers announce the term-definition relationship
  - Ensure terms are concise and descriptive
  - Use ARIA roles carefully as they may be redundant with native semantics
* **CSS styling**:
  - Default styling is minimal
  - Can be styled as inline or block elements
  - Often used with `font-weight: bold` for visual distinction
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using outside of `<dl>` elements
  - Including block-level content within `<dt>`
  - Using for general text formatting instead of semantic terms
  - Confusing with `<dd>` element purpose
* **SEO benefits**: Helps search engines understand definitional content structure
* **Mobile usability**: Ensure adequate touch target size when terms are interactive
* **Internationalization**: Works well with different languages and writing systems

---
