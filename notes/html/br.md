# `<br>`

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

The `<br>` element represents a line break in text content, forcing text to continue on the next line. Unlike paragraph elements that create semantic blocks with spacing, `<br>` simply produces a carriage return within the same structural unit, making it useful for maintaining specific text formatting where line breaks are meaningful to the content itself.

---

## Syntax & Variants

+ **Standard syntax**: `<br>` (void element)
+ **Void element**: No closing tag required
+ **Alternative forms**:
  - HTML5: `<br>`
  - XHTML: `<br />` or `<br></br>`
+ **Self-closing**: In XML contexts, must be self-closed as `<br/>`

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **Commonly used**: `class`, `style` for specific styling
+ **Deprecated attributes**: `clear` (use CSS `clear` property instead)

---

## Content Model

+ **Empty element**: Must not contain any content
+ **No children permitted**: Cannot contain text or other elements
+ **Void element category**: Defined as having no content model in HTML specification

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within `<p>` elements for line breaks in paragraphs
  - Within headings (`<h1>`-`<h6>`) for multi-line titles
  - Within `<address>` elements for formatted contact information
  - Within `<td>` elements for line breaks in table cells
  - Within poetic or formatted text content
+ **No parent restrictions**: Can be used anywhere phrasing content is allowed

---

## Behavior and Semantics

+ **Default display**: No visual representation itself
+ **Effect**: Causes subsequent content to start on a new line
+ **Semantic meaning**: 
  - Represents a thematic break in text content
  - Indicates where line breaks are semantically significant
  - No strong semantic meaning for accessibility tools
+ **Accessibility**: Screen readers may announce a pause or break, but behavior varies
+ **Styling**: Cannot be styled directly, but affects text flow

---

## Examples

**Basic line break in address:**
```html
<p>John Doe<br>
123 Main Street<br>
Anytown, CA 12345</p>
```

**Poetic formatting:**
```html
<p>Two roads diverged in a yellow wood,<br>
And sorry I could not travel both<br>
And be one traveler, long I stood<br>
And looked down one as far as I could</p>
```

**Multiple breaks for spacing (generally discouraged):**
```html
<p>This is the first line of text.<br><br>
This appears after two line breaks, creating extra vertical space.</p>
```

**Styled line breaks in contact information:**
```html
<address>
  <strong>Company Name</strong><br>
  <span class="street">123 Business Avenue</span><br>
  <span class="city-state">Suite 100, New York, NY 10001</span><br>
  <span class="phone">Phone: (555) 123-4567</span>
</address>
```

**Complex formatting in table cells:**
```html
<td>
  <strong>Project Manager</strong><br>
  John Smith<br>
  Email: john@example.com<br>
  Ext: 4567
</td>
```

**Multiple consecutive breaks with styling:**
```html
<div class="formatted-content">
  <h3>Meeting Agenda</h3>
  <p>1. Review quarterly reports<br>
  2. Discuss budget allocation<br><br>
  3. Team updates and announcements<br>
  4. Open floor discussion</p>
</div>
```

---

## Notes

* **Semantic misuse**: Using `<br>` for visual spacing rather than semantic line breaks is considered poor practice
* **CSS alternatives**: For visual spacing, prefer CSS margins/padding; for text formatting, consider `white-space: pre` or `pre-line`
* **Accessibility concerns**: Screen readers may not consistently handle multiple consecutive `<br>` elements
* **Deprecated `clear`**: The `clear` attribute for controlling text flow around floats was deprecated in HTML4 - use CSS `clear` property
* **Responsive design**: `<br>` elements can cause issues in responsive layouts as they create fixed line breaks
* **Common pitfall**: Overusing `<br>` for layout instead of proper CSS - this is an anti-pattern
* **HTML vs XHTML**: In HTML5, `<br>` is sufficient; in XHTML, must use `<br />`
* **Email compatibility**: Still widely used in HTML email where CSS support is limited
* **Poetry and addresses**: Appropriate use cases where line breaks are semantically meaningful to the content structure

---
