# `<picture>`

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

The `<picture>` element serves as a container for multiple image sources, providing art direction and responsive image capabilities. It enables developers to offer different image files based on factors like viewport size, device pixel density, screen capabilities, or user preferences, allowing for optimized image delivery and creative control over how images appear in various contexts.

---

## Syntax & Variants

+ **Standard syntax**: `<picture>...</picture>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps multiple `<source>` elements and one `<img>` element
+ **No self-closing variant**: Must contain child elements
+ **HTML5 introduction**: Added in HTML5 to address responsive image needs

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies entirely on child elements for functionality
+ **Commonly used**: `class`, `style` for container styling

---

## Content Model

+ **Required children**: 
  - One or more `<source>` elements (optional but typical)
  - One `<img>` element (required as fallback)
+ **Permitted content**:
  - Zero or more `<source>` elements
  - Exactly one `<img>` element
  - Optional script-supporting elements (`<script>`, `<template>`)
+ **Order matters**: `<source>` elements must come before the `<img>` element
+ **Fallback requirement**: `<img>` element is mandatory for backward compatibility

---

## Context

+ **Valid parents**: Any element that accepts embedded content or phrasing content
+ **Common locations**:
  - Within `<article>`, `<section>`, `<div>` for content images
  - Within `<figure>` for captioned responsive images
  - Within `<main>` for primary content images
  - In responsive layouts where art direction is needed
+ **Replaced element container**: Behaves similarly to `<img>` in document flow

---

## Behavior and Semantics

+ **Default display**: Inline-level element (same as `<img>`)
+ **Selection process**:
  - Browser evaluates `<source>` elements in order
  - First matching `<source>` is used
  - If no sources match, falls back to `<img>` element
  - Uses `srcset` and `media` attributes for decision making
+ **Semantic meaning**:
  - Indicates multiple image representations are available
  - No direct semantic impact on screen readers
  - Screen readers read the `alt` text from the `<img>` element
+ **Accessibility**: Inherits accessibility from the contained `<img>` element

---

## Examples

**Basic art direction for different viewports:**
```html
<picture>
  <source media="(min-width: 1200px)" srcset="hero-large.jpg">
  <source media="(min-width: 768px)" srcset="hero-medium.jpg">
  <img src="hero-small.jpg" alt="Mountain landscape at sunset">
</picture>
```

**High-DPI screen support:**
```html
<picture>
  <source srcset="logo@2x.png 2x, logo@3x.png 3x">
  <img src="logo.png" alt="Company logo" width="200" height="100">
</picture>
```

**Modern image format with fallback:**
```html
<picture>
  <source type="image/webp" srcset="image.webp">
  <source type="image/jp2" srcset="image.jp2">
  <img src="image.jpg" alt="Modern image format example" loading="lazy">
</picture>
```

**Complex responsive image with multiple breakpoints:**
```html
<picture>
  <source media="(min-width: 1024px)" 
          srcset="banner-large.jpg 1920w,
                  banner-medium.jpg 1024w"
          sizes="100vw">
  <source media="(min-width: 768px)" 
          srcset="banner-tablet.jpg 768w,
                  banner-tablet-2x.jpg 1536w"
          sizes="100vw">
  <img src="banner-mobile.jpg" 
       srcset="banner-mobile-2x.jpg 2x"
       alt="Product banner showing new features"
       loading="eager">
</picture>
```

**Art direction with cropping:**
```html
<picture>
  <source media="(orientation: landscape)" 
          srcset="hero-landscape.jpg">
  <img src="hero-portrait.jpg" 
       alt="Architectural building showing modern design"
       class="responsive-hero">
</picture>
```

**Multiple format support with art direction:**
```html
<picture>
  <!-- Large screens, WebP format -->
  <source media="(min-width: 1200px)" 
          type="image/webp" 
          srcset="product-large.webp">
  
  <!-- Large screens, JPEG fallback -->
  <source media="(min-width: 1200px)" 
          srcset="product-large.jpg">
  
  <!-- Medium screens, WebP format -->
  <source media="(min-width: 768px)" 
          type="image/webp" 
          srcset="product-medium.webp">
  
  <!-- Medium screens, JPEG fallback -->
  <source media="(min-width: 768px)" 
          srcset="product-medium.jpg">
  
  <!-- Default image -->
  <img src="product-small.jpg" 
       alt="Wireless headphones with noise cancellation"
       width="400" 
       height="300">
</picture>
```

**Picture within figure with caption:**
```html
<figure>
  <picture>
    <source media="(min-width: 800px)" srcset="chart-wide.png">
    <source media="(min-width: 400px)" srcset="chart-narrow.png">
    <img src="chart-mobile.png" alt="Bar chart showing monthly revenue growth">
  </picture>
  <figcaption>Monthly Revenue Growth 2024 (responsive chart)</figcaption>
</figure>
```

---

## Notes

* **Browser support**: Well-supported in all modern browsers; unsupported browsers fall back to `<img>`
* **Performance benefits**: Enables delivering appropriately sized images, reducing bandwidth usage
* **Art direction vs. resolution switching**: 
  - Use `<picture>` for art direction (different crops/compositions)
  - Use `srcset` on `<img>` for resolution switching (same image, different sizes)
* **Accessibility considerations**: 
  - Always provide meaningful `alt` text on the `<img>` element
  - The `<picture>` element itself has no semantic meaning for screen readers
* **SEO impact**: Search engines can understand and index responsive images properly
* **Common pitfalls**:
  - Forgetting the required `<img>` fallback
  - Incorrect order of `<source>` elements
  - Overly complex media queries that are hard to maintain
  - Not testing fallback behavior in older browsers
* **Progressive enhancement**: The `<picture>` element is inherently progressive—browsers that don't support it use the `<img>` fallback
* **Content delivery networks**: Often used with CDNs that provide automatic image optimization and responsive variants
* **File organization**: Maintain consistent naming conventions for different image versions to simplify management

---
