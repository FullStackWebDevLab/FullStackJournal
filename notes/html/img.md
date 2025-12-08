# `<img>`

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

The `<img>` element embeds images into HTML documents. It serves as a placeholder that displays graphical content referenced by a source URL, enabling the integration of photographs, illustrations, icons, diagrams, and other visual media directly within web pages without requiring external plugins or complex embedding techniques.

---

## Syntax & Variants

+ **Standard syntax**: `<img>` (void element)
+ **Void element**: No closing tag required
+ **Alternative forms**:
  - HTML5: `<img>`
  - XHTML: `<img />` or `<img></img>`
+ **Self-closing**: In XML contexts, must be self-closed as `<img/>`

---

## Attributes

+ **Core attributes**:
  - `src` (required): Specifies the image URL or path
  - `alt` (required for accessibility): Alternative text description
  - `width` (optional): Display width in CSS pixels
  - `height` (optional): Display height in CSS pixels
  - `srcset` (optional): Multiple image sources for responsive images
  - `sizes` (optional): Image display sizes for responsive layout
  - `loading` (optional): lazy/eager loading behavior
  - `decoding` (optional): async/sync/auto image decoding

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, `lang`, etc.

+ **Deprecated attributes**:
  - `align` (use CSS `float` or `vertical-align`)
  - `border` (use CSS `border`)
  - `hspace`, `vspace` (use CSS `margin`)
  - `name` (use `id` instead)
  - `longdesc` (use `aria-describedby` or link to description)

+ **Obsolete attributes**: `lowsec`, `lowsrc`

---

## Content Model

+ **Empty element**: Must not contain any content
+ **No children permitted**: Cannot contain text or other elements
+ **Void element category**: Defined as having no content model in HTML specification

---

## Context

+ **Valid parents**: Any element that accepts embedded content or phrasing content
+ **Common locations**:
  - Within `<p>` elements for inline images
  - Within `<figure>` elements for captioned images
  - Within `<a>` elements for linked images
  - Within `<div>`, `<section>`, `<article>` for layout images
  - Within list items, table cells, headers, footers
+ **Replaced element**: The image content replaces the element itself in rendering

---

## Behavior and Semantics

+ **Default display**: Inline-level replaced element
+ **Default styling**:
  - `display: inline-block` (effectively)
  - No borders, margins, or padding by default
  - Renders at intrinsic dimensions unless specified
+ **Loading behavior**:
  - Fetches and displays image from `src` URL
  - Shows broken image icon if source fails to load
  - Respects `loading="lazy"` for deferred loading
+ **Semantic meaning**:
  - Represents embedded graphical content
  - Screen readers read `alt` text (if provided)
  - Search engines index `alt` text for accessibility and SEO
+ **Accessibility**: Critical for users who cannot see images; `alt` text must convey equivalent information

---

## Examples

**Basic image with required attributes:**
```html
<img src="photo.jpg" alt="A beautiful sunset over mountains">
```

**Image with dimensions and styling:**
```html
<img src="logo.png" alt="Company Logo" width="200" height="100" class="header-logo">
```

**Responsive image with multiple sources:**
```html
<img src="image-800.jpg" 
     srcset="image-400.jpg 400w, image-800.jpg 800w, image-1200.jpg 1200w"
     sizes="(max-width: 600px) 400px, (max-width: 1200px) 800px, 1200px"
     alt="Responsive landscape photograph"
     loading="lazy">
```

**Image within figure with caption:**
```html
<figure>
  <img src="chart.png" alt="Bar chart showing quarterly sales growth: Q1 $1.2M, Q2 $1.5M, Q3 $1.8M, Q4 $2.1M">
  <figcaption>Quarterly Sales Performance 2024</figcaption>
</figure>
```

**Linked image:**
```html
<a href="large-photo.jpg">
  <img src="thumbnail.jpg" alt="View larger version of mountain landscape" width="300" height="200">
</a>
```

**Complex image with accessibility features:**
```html
<img src="infographic.png" 
     alt=""
     aria-labelledby="infographic-desc"
     class="info-graphic"
     width="600"
     height="400">
<div id="infographic-desc" class="visually-hidden">
  Infographic showing three steps: First, research phase with magnifying glass icon. 
  Second, development phase with gear icon. Third, launch phase with rocket icon.
  Each step includes percentage completion and key metrics.
</div>
```

**Image with multiple purposes:**
```html
<img src="product-3d-rotate.gif" 
     alt="3D rotation view of wireless headphones showing black matte finish, adjustable headband, and foldable design"
     width="400" 
     height="300"
     loading="eager"
     decoding="async">
```

**Image with error handling:**
```html
<img src="user-avatar.jpg" 
     alt="User profile picture"
     onerror="this.src='default-avatar.png'; this.alt='Default user avatar'"
     class="avatar">
```

---

## Notes

* **Accessibility requirement**: The `alt` attribute is required for accessibility compliance (WCAG)
* **Empty alt text**: Use `alt=""` for decorative images that don't convey meaningful content
* **Performance considerations**:
  - Use `loading="lazy"` for below-the-fold images
  - Specify `width` and `height` to prevent layout shifts
  - Use modern formats (WebP, AVIF) when possible
* **Responsive images**: `srcset` and `sizes` attributes enable browser to choose appropriate image source
* **Security**: Be cautious with user-uploaded images; validate and sanitize to prevent XSS
* **Copyright**: Ensure proper licensing for all embedded images
* **Browser support**:
  - All modern browsers support basic functionality
  - `loading="lazy"` supported in most modern browsers
  - `srcset` supported in all modern browsers
* **Common pitfalls**:
  - Missing `alt` attributes
  - Using images for text content (use actual text instead)
  - Not specifying dimensions (causes layout shifts)
  - Overly large file sizes affecting performance
* **SEO impact**: Images contribute to page load time and user experience, affecting search rankings
* **Image formats**: Choose appropriate format (JPEG for photos, PNG for transparency, SVG for vectors, WebP for modern compression)

---
