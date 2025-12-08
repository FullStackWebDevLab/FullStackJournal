# `<source>`

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

The `<source>` element specifies multiple media resources for `<picture>`, `<audio>`, and `<video>` elements. It enables browsers to select the most appropriate media file based on factors like format support, viewport size, screen density, or bandwidth, providing fallback options and responsive media delivery without requiring JavaScript.

---

## Syntax & Variants

+ **Standard syntax**: `<source>` (void element)
+ **Void element**: No closing tag required
+ **Self-closing variants**:
  - HTML5: `<source>`
  - XHTML: `<source />` or `<source></source>`
+ **Media resource specifier**: Always used within parent media elements

---

## Attributes

+ **Core attributes** (context-dependent):
  - `src` (required for `<audio>` and `<video>`): URL of the media resource
  - `srcset` (required for `<picture>`): Images to use in different situations
  - `type` (optional): MIME type of the resource, optionally with codecs parameter
  - `media` (optional): Media query indicating intended display environment
  - `sizes` (optional): Image sizes for different layout scenarios (`<picture>` only)
+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **Attribute combinations**:
  - For `<audio>`/`<video>`: `src` + `type` (+ `media` rarely)
  - For `<picture>`: `srcset` + `media` (+ `sizes` + `type`)

---

## Content Model

+ **Empty element**: Must not contain any content
+ **No children permitted**: Cannot contain text or other elements
+ **Void element category**: Defined as having no content model in HTML specification
+ **No fallback content**: Relies on parent element for fallback behavior

---

## Context

+ **Required parent**: Must be a direct child of `<picture>`, `<audio>`, or `<video>`
+ **Sibling order**: 
  - Multiple `<source>` elements allowed
  - Browser uses first supported source in order
  - Must come before fallback content in `<audio>`/`<video>`
+ **Invalid contexts**: Cannot be used outside of supported parent elements

---

## Behavior and Semantics

+ **Default display**: No visual representation
+ **Selection process**:
  - Browser evaluates `<source>` elements in order
  - First matching/supported source is selected
  - Evaluation stops at first valid match
  - If no sources match, falls back to next available option
+ **Semantic meaning**:
  - Represents alternative media resource
  - No direct semantic impact on accessibility
  - Selection happens at browser level, transparent to users
+ **No user interaction**: Selection is automatic based on browser capabilities and conditions

---

## Examples

**Multiple audio formats:**
```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
  <source src="audio.wav" type="audio/wav">
  Your browser does not support the audio element.
</audio>
```

**Video with codec information:**
```html
<video controls>
  <source src="video.mp4" type="video/mp4; codecs=avc1.42E01E,mp4a.40.2">
  <source src="video.webm" type="video/webm; codecs=vp8,vorbis">
  <source src="video.ogv" type="video/ogg; codecs=theora,vorbis">
</video>
```

**Picture element with art direction:**
```html
<picture>
  <source media="(min-width: 1200px)" srcset="hero-large.jpg">
  <source media="(min-width: 768px)" srcset="hero-medium.jpg">
  <source media="(min-width: 480px)" srcset="hero-small.jpg">
  <img src="hero-fallback.jpg" alt="Responsive hero image">
</picture>
```

**Responsive images with density switching:**
```html
<picture>
  <source srcset="logo@2x.png 2x, logo@3x.png 3x">
  <img src="logo.png" alt="Company logo" width="200" height="100">
</picture>
```

**Modern image formats with fallback:**
```html
<picture>
  <source type="image/avif" srcset="image.avif">
  <source type="image/webp" srcset="image.webp">
  <source type="image/jpeg" srcset="image.jpg">
  <img src="image.jpg" alt="Modern image format example">
</picture>
```

**Complex picture with multiple conditions:**
```html
<picture>
  <!-- High-resolution displays, WebP format -->
  <source media="(min-width: 1024px) and (min-resolution: 2dppx)" 
          srcset="large@2x.webp 2x, large@3x.webp 3x" 
          type="image/webp">
  
  <!-- Large screens, standard resolution -->
  <source media="(min-width: 1024px)" 
          srcset="large.jpg" 
          type="image/jpeg">
  
  <!-- Medium screens, high resolution -->
  <source media="(min-width: 768px) and (min-resolution: 2dppx)" 
          srcset="medium@2x.webp 2x" 
          type="image/webp">
  
  <!-- Medium screens -->
  <source media="(min-width: 768px)" 
          srcset="medium.jpg" 
          type="image/jpeg">
  
  <!-- Default image -->
  <img src="small.jpg" alt="Complex responsive image example">
</picture>
```

**Audio with media queries (rare use case):**
```html
<audio controls>
  <source src="audio-high.mp3" type="audio/mpeg" media="(min-width: 768px)">
  <source src="audio-low.mp3" type="audio/mpeg" media="(max-width: 767px)">
  Your browser does not support the audio element.
</audio>
```

**Video with responsive sources:**
```html
<video controls>
  <source src="video-1080p.mp4" type="video/mp4" media="(min-width: 1920px)">
  <source src="video-720p.mp4" type="video/mp4" media="(min-width: 1280px)">
  <source src="video-480p.mp4" type="video/mp4" media="(max-width: 1279px)">
  <source src="video-360p.webm" type="video/webm">
</video>
```

**Advanced picture with sizes attribute:**
```html
<picture>
  <source media="(min-width: 1200px)" 
          srcset="large-400.jpg 400w, large-800.jpg 800w, large-1200.jpg 1200w"
          sizes="(min-width: 1200px) 50vw, 100vw">
  <source media="(min-width: 768px)" 
          srcset="medium-200.jpg 200w, medium-400.jpg 400w, medium-600.jpg 600w"
          sizes="(min-width: 768px) 75vw, 100vw">
  <img src="small-400.jpg" 
       srcset="small-200.jpg 200w, small-400.jpg 400w"
       sizes="100vw"
       alt="Advanced responsive image">
</picture>
```

---

## Notes

* **Order sensitivity**: Browsers use first matching source, so order matters significantly
* **Required attributes**: 
  - For `<audio>`/`<video>`: `src` is required
  - For `<picture>`: `srcset` is required
* **MIME type importance**: `type` attribute helps browsers avoid downloading unsupported formats
* **Browser evaluation**: Browsers stop at first supported source, so place preferred formats first
* **Performance benefits**: Prevents downloading unnecessary resources
* **Common mistakes**:
  - Incorrect attribute combinations for parent element
  - Wrong order of sources (most specific to least specific)
  - Missing `type` attributes causing unnecessary downloads
  - Using `<source>` outside supported parent elements
* **Format support testing**: Browsers use MIME type and codec information to determine support
* **Mobile optimization**: Essential for delivering appropriately sized media to different devices
* **Accessibility**: `<source>` selection is automatic and doesn't affect accessibility of parent element
* **Progressive enhancement**: Well-supported in modern browsers; older browsers fall back to `<img>` or first supported format
* **CDN integration**: Often used with content delivery networks that provide automatic format conversion

---
