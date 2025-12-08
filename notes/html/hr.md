# `<hr>`

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

The `<hr>` element represents a thematic break between paragraph-level elements, typically displayed as a horizontal rule. It signifies a transition or separation between different sections of content, such as a change of topic, scene, or section within a chapter, article, or other document structure.

---

## Syntax & Variants

+ **Standard syntax**: `<hr>` (void element)
+ **Void element**: No closing tag required
+ **Alternative forms**:
  - HTML5: `<hr>`
  - XHTML: `<hr />` or `<hr></hr>`
+ **Self-closing**: In XML contexts, must be self-closed as `<hr/>`

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **Commonly used**: `class`, `style` for extensive customization
+ **Deprecated attributes**: 
  - `align` (use CSS `text-align` on container or `margin` on `<hr>`)
  - `noshade` (use CSS `border-style`, `background-color`)
  - `size` (use CSS `height` or `border-width`)
  - `width` (use CSS `width`)
  - `color` (use CSS `color`, `background-color`, or `border-color`)

---

## Content Model

+ **Empty element**: Must not contain any content
+ **No children permitted**: Cannot contain text or other elements
+ **Void element category**: Defined as having no content model in HTML specification

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Between paragraphs in articles
  - Between distinct sections of content
  - Before or after major content divisions
  - Within `<blockquote>` elements to separate multiple quotes
  - In forms to separate different sections
+ **Flow content**: Treated as block-level element in document flow

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling** (varies by browser, typically):
  - `display: block`
  - `margin-top: 0.5em`
  - `margin-bottom: 0.5em`
  - `margin-left: auto`
  - `margin-right: auto`
  - `border-style: inset`
  - `border-width: 1px`
  - `height: 1px` (some browsers)
  - `background-color: gray` (some browsers)
+ **Semantic meaning**:
  - Represents a paragraph-level thematic break
  - Creates a semantic separation for assistive technologies
  - Screen readers typically announce as "separator" or "horizontal rule"
+ **Accessibility**: Conveys content structure to screen reader users

---

## Examples

**Basic thematic break:**
```html
<p>This is the first section of content discussing the initial topic.</p>

<hr>

<p>This is the second section, representing a change in subject or perspective.</p>
```

**Styled horizontal rule:**
```html
<p>Content before the styled separator.</p>

<hr class="custom-rule" style="border: 2px dashed #ccc; margin: 2em 0;">

<p>Content after the customized horizontal rule.</p>
```

**Multiple styled variants:**
```html
<article>
  <h2>Article Title</h2>
  <p>Introduction content goes here...</p>
  
  <hr class="thin-divider">
  
  <h3>First Section</h3>
  <p>Section content...</p>
  
  <hr class="thick-accent" style="height: 3px; background: linear-gradient(to right, transparent, #007acc, transparent); border: none;">
  
  <h3>Second Section</h3>
  <p>More content after a visually distinct break...</p>
  
  <hr class="dotted" style="border: none; border-top: 1px dotted #999; margin: 2em 0;">
</article>
```

**Accessible thematic breaks:**
```html
<section>
  <h2>Technical Specifications</h2>
  <p>Detailed technical information...</p>
  
  <hr aria-hidden="true">
  
  <h2>User Reviews</h2>
  <p>Customer feedback and reviews...</p>
  
  <!-- For screen readers, provide additional context -->
  <hr class="visually-hidden" aria-label="End of main content, beginning of related articles">
</section>
```

**Form section separation:**
```html
<form>
  <fieldset>
    <legend>Personal Information</legend>
    <!-- Form fields -->
  </fieldset>
  
  <hr style="margin: 2rem 0;">
  
  <fieldset>
    <legend>Payment Information</legend>
    <!-- Payment fields -->
  </fieldset>
  
  <hr class="section-divider">
  
  <fieldset>
    <legend>Preferences</legend>
    <!-- Preference fields -->
  </fieldset>
</form>
```

**Responsive horizontal rules:**
```html
<article>
  <p>First paragraph of content.</p>
  
  <hr class="responsive-rule" style="width: 80%; max-width: 400px; margin: 2em auto; border: 1px solid #e0e0e0;">
  
  <p>Second paragraph following a responsive horizontal rule that adapts to container size.</p>
</article>
```

---

## Notes

* **Semantic evolution**: In HTML4, `<hr>` was primarily presentational; in HTML5, it gained semantic meaning as a thematic break
* **CSS customization**: Default styling is minimal - extensive CSS is typically required for visual design
* **Accessibility**: Screen readers treat `<hr>` as a separator, helping users understand content structure
* **Overuse caution**: Using too many horizontal rules can create visual clutter and dilute their semantic value
* **Alternative separators**: Consider CSS `border`, `padding`, `margin`, or empty `<div>` elements for purely visual separation
* **Browser inconsistencies**: Default styling varies across browsers - always explicitly style for consistent appearance
* **Deprecated attributes**: All presentational attributes should be replaced with CSS equivalents
* **Mobile considerations**: Ensure horizontal rules don't consume excessive vertical space on mobile devices
* **Print styling**: Consider adjusting `<hr>` styles for print media to conserve ink/toner

---
