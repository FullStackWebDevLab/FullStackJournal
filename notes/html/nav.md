# `<nav>`

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

The `<nav>` element represents a section of a page that contains navigation links; either within the current document or to other documents. It's designed to identify major navigation blocks, helping users and assistive technologies quickly locate and understand the primary navigation structure of a website or application.

---

## Syntax & Variants

+ **Standard syntax**: `<nav>...</nav>`
+ **Not void**: Requires both opening and closing tags
+ **No self-closing variant**: Must always contain content
+ **No legacy forms**: Introduced in HTML5, no direct equivalent in previous versions

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `lang`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **Commonly used**: `aria-label`, `aria-labelledby` for accessibility
+ **No element-specific attributes**: Relies entirely on global attributes

---

## Content Model

+ **Permitted content**: Flow content (typically lists of links)
+ **Common patterns**:
  - Unordered lists (`<ul>` with `<li>` and `<a>` elements)
  - Ordered lists (`<ol>`)
  - Standalone links (`<a>` elements)
  - Paragraphs containing links
+ **Not appropriate**: Main page content or sections unrelated to navigation

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<header>`
  - Within `<main>`
  - Within `<aside>` for secondary navigation
  - Directly in `<body>`
+ **Not required**: Not every link group needs a `<nav>` element
+ **Multiple instances**: A page may contain multiple `<nav>` elements for different navigation sections

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**: No default visual styling (appears as plain block)
+ **Semantic meaning**:
  - Identifies major navigation regions for screen readers
  - Helps search engines understand site structure
  - Enables keyboard navigation landmarks
+ **Accessibility**: Creates a navigation landmark in ARIA
+ **SEO benefit**: Helps search engines identify important navigation content

---

## Examples

**Basic navigation with list:**
```html
<nav>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/about">About</a></li>
    <li><a href="/contact">Contact</a></li>
  </ul>
</nav>
```

**Navigation with accessibility labeling:**
```html
<nav aria-label="Main navigation">
  <ul>
    <li><a href="/products">Products</a></li>
    <li><a href="/services">Services</a></li>
    <li><a href="/support">Support</a></li>
  </ul>
</nav>
```

**Complex navigation with multiple sections:**
```html
<nav aria-labelledby="main-nav-heading">
  <h2 id="main-nav-heading" class="visually-hidden">Site Navigation</h2>
  <div class="nav-container">
    <ul class="primary-nav">
      <li><a href="/">Home</a></li>
      <li>
        <a href="/products">Products</a>
        <ul class="dropdown">
          <li><a href="/products/software">Software</a></li>
          <li><a href="/products/hardware">Hardware</a></li>
        </ul>
      </li>
    </ul>
    <div class="utility-nav">
      <a href="/search">Search</a>
      <a href="/account">Account</a>
    </div>
  </div>
</nav>
```

**Breadcrumb navigation:**
```html
<nav aria-label="Breadcrumb">
  <ol>
    <li><a href="/">Home</a></li>
    <li><a href="/products">Products</a></li>
    <li><a href="/products/electronics">Electronics</a></li>
    <li>Current Page</li>
  </ol>
</nav>
```

---

## Notes

* **Not for all links**: Reserve `<nav>` for major navigation blocks, not every group of links
* **Multiple nav elements**: Use multiple `<nav>` elements when you have distinct navigation sections (main nav, footer nav, sidebar nav)
* **Accessibility**: Always provide accessible labels (`aria-label` or `aria-labelledby`) when multiple navigation regions exist
* **HTML5 only**: Not supported in HTML4 or XHTML—use `<div>` with appropriate classes in legacy documents
* **Browser support**: Well-supported in all modern browsers, including screen readers
* **Common pitfall**: Overusing `<nav>` for minor link groups—this dilutes its semantic value
* **Styling**: Requires explicit CSS for visual presentation as it has no default styling
* **Mobile considerations**: Often used as the container for responsive navigation patterns like hamburger menus

---
