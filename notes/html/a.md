# `<a>`

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

The `<a>` (anchor) element creates hyperlinks, which are the fundamental mechanism for navigation in HTML. It enables connections between resources, allowing users to navigate between web pages, jump to specific sections within documents, trigger actions, or reference external content. The anchor element is what makes the "web" interconnected.

---

## Syntax & Variants

+ **Standard syntax**: `<a>...</a>`
+ **Not void**: Requires both opening and closing tags
+ **No self-closing variant**: Must contain content or be empty for styling purposes
+ **Legacy note**: Originally named "anchor" for both source and destination links; now primarily used for source links

---

## Attributes

+ **Core attributes**:
  - `href` (optional): Specifies the URL the link points to
  - `target` (optional): Specifies where to open the linked document
  - `download` (optional): Prompts to download the linked resource
  - `rel` (optional): Relationship between current and linked document
  - `type` (optional): MIME type of the linked resource
  - `hreflang` (optional): Language of the linked resource
  - `referrerpolicy` (optional): Which referrer to send

+ **Required attributes**: None technically required, but without `href`, it's a "placeholder" link

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, `lang`, etc.

+ **Deprecated attributes**:
  - `charset` (use HTTP Content-Type header)
  - `coords`, `shape` (for image maps)
  - `name` (use `id` instead for fragment identifiers)
  - `rev` (use `rel` instead)

---

## Content Model

+ **Permitted content**: Transparent content model (can contain phrasing content)
+ **Allowed elements**: 
  - Text and character references
  - Most phrasing elements: `<strong>`, `<em>`, `<span>`, `<img>`, `<code>`, etc.
  - Even other interactive elements in some contexts (with careful consideration)
+ **Not allowed**: Typically should not nest interactive elements (other `<a>`, `<button>`, etc.)
+ **Empty links**: Valid for CSS-styled buttons or JavaScript-enhanced links

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within `<p>`, `<li>`, `<div>`, `<span>` elements
  - Within navigation blocks (`<nav>`)
  - Within headings, paragraphs, list items
  - Within table cells, footer content, header content
+ **Wrapping restrictions**: Cannot wrap entire block-level sections in HTML5 (though browsers may handle it)

---

## Behavior and Semantics

+ **Default display**: Inline element
+ **Default styling**:
  - `color: blue` (unvisited)
  - `color: purple` (visited)
  - `text-decoration: underline`
  - `cursor: pointer`
+ **Interactive behavior**:
  - Clicking navigates to the `href` destination
  - Middle-click or Ctrl+Click opens in new tab
  - Hover shows URL in status bar (in some browsers)
+ **Semantic meaning**:
  - Creates navigational relationships
  - Screen readers announce as "link" and read the link text
  - Search engines use links for ranking and site structure
+ **Accessibility**: Focusable by default, part of tab order

---

## Examples

**Basic text link:**
```html
<a href="https://example.com">Visit Example Website</a>
```

**Link with target and title:**
```html
<a href="https://example.com" target="_blank" rel="noopener" title="Opens in new window">
  External Website
</a>
```

**Download link:**
```html
<a href="/documents/report.pdf" download="annual-report.pdf">
  Download PDF Report
</a>
```

**Email and telephone links:**
```html
<a href="mailto:contact@example.com">Email Us</a>
<a href="tel:+15551234567">Call (555) 123-4567</a>
```

**Fragment identifier (page jump):**
```html
<a href="#section2">Jump to Section 2</a>

<!-- Later in the document -->
<section id="section2">
  <h2>Section 2 Content</h2>
  <p>This is the target section.</p>
</section>
```

**Complex link with multiple elements:**
```html
<a href="/products/electronics" class="product-link">
  <img src="/images/electronics.jpg" alt="Electronics category">
  <span class="link-text">Shop Electronics</span>
  <span class="arrow">→</span>
</a>
```

**Navigation menu with links:**
```html
<nav aria-label="Main navigation">
  <ul>
    <li><a href="/" aria-current="page">Home</a></li>
    <li><a href="/about">About Us</a></li>
    <li><a href="/services">Services</a></li>
    <li><a href="/contact">Contact</a></li>
  </ul>
</nav>
```

**Accessible link with proper context:**
```html
<a href="/annual-report.pdf" class="document-link">
  <span class="visually-hidden">Download the </span>
  2024 Annual Report
  <span class="file-info">(PDF, 2.4 MB)</span>
</a>
```

**Button-style link:**
```html
<a href="/signup" class="button" role="button" aria-label="Sign up for our newsletter">
  Sign Up Now
</a>
```

**Links with different relationships:**
```html
<a href="/privacy-policy" rel="nofollow">Privacy Policy</a>
<a href="/author/john" rel="author">About the Author</a>
<a href="/license" rel="license">Creative Commons License</a>
```

---

## Notes

* **Placeholder links**: Links without `href` are valid but not navigable; often used for JavaScript-enhanced interactions
* **Security concerns**: 
  - Use `rel="noopener"` or `rel="noreferrer"` with `target="_blank"` to prevent tabnabbing
  - Validate and sanitize user-generated links to prevent XSS
* **Accessibility best practices**:
  - Use descriptive link text (avoid "click here")
  - Ensure sufficient color contrast
  - Provide focus indicators for keyboard navigation
  - Use `aria-label` for additional context when needed
* **SEO considerations**: 
  - Use `rel="nofollow"` for untrusted or paid links
  - Internal linking helps search engines understand site structure
* **Performance**: Prefetching with `rel="prefetch"` for likely navigation targets
* **URL protocols**: Support various schemes (`http:`, `https:`, `mailto:`, `tel:`, `ftp:`, etc.)
* **Fragment identifiers**: Can link to elements with `id` attributes within same document
* **Browser differences**: Handling of `:visited` styling is restricted for privacy reasons
* **Mobile considerations**: Ensure touch targets are sufficiently large (minimum 44×44px)

---
