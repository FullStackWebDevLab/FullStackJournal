# `<figure>`

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

The `<figure>` element represents self-contained content that is referenced from the main content flow, but that can be moved away from that primary flow without affecting the document's meaning. It typically encapsulates images, diagrams, code snippets, illustrations, or other content that is referenced as a single unit, optionally with a caption provided by a `<figcaption>` element.

---

## Syntax & Variants

+ **Standard syntax**: `<figure>...</figure>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps content and optional `<figcaption>`
+ **No self-closing variant**: Must contain content
+ **HTML5 introduction**: Added in HTML5 to provide semantic grouping for referenced content

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies on semantic meaning rather than specific attributes
+ **Commonly used**: `class`, `id` for styling and scripting

---

## Content Model

+ **Permitted content**:
  - One optional `<figcaption>` element (must be first or last child)
  - Flow content (images, code blocks, videos, audio, etc.)
  - Any combination of the above
+ **Required content**: Must contain at least one content element (cannot be empty)
+ **Caption placement**: `<figcaption>` can be either the first or last direct child

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<article>`, `<section>`, `<main>` for content illustrations
  - Within `<div>` containers in various layout contexts
  - Directly within `<body>` for standalone figures
  - In technical documentation, tutorials, and educational content
+ **Flow content**: Treated as block-level element in document flow
+ **No nesting restrictions**: Can contain other `<figure>` elements in some contexts

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - `margin-top: 1em`
  - `margin-bottom: 1em`
  - `margin-left: 40px`
  - `margin-right: 40px`
+ **Semantic meaning**:
  - Represents self-contained, referenced content
  - Creates a semantic grouping for assistive technologies
  - Screen readers may announce as "figure" or group the content
  - Indicates content that is supplementary to main flow
+ **Accessibility**: Helps screen reader users understand content relationships and structure

---

## Examples

**Basic image with caption:**
```html
<figure>
  <img src="chart.png" alt="Bar chart showing quarterly sales data">
  <figcaption>Figure 1: Quarterly Sales Performance 2024</figcaption>
</figure>
```

**Code snippet figure:**
```html
<figure>
  <figcaption>Listing 1: JavaScript function for calculating Fibonacci sequence</figcaption>
  <pre><code>
function fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}
  </code></pre>
</figure>
```

**Multiple images in one figure:**
```html
<figure>
  <img src="before.jpg" alt="Room before renovation">
  <img src="after.jpg" alt="Room after renovation">
  <figcaption>Figure 2: Comparison of room before and after renovation</figcaption>
</figure>
```

**Complex figure with multiple content types:**
```html
<figure class="technical-diagram" id="figure-3">
  <img src="network-architecture.png" alt="Diagram showing three-tier network architecture">
  <div class="diagram-legend">
    <span class="web-tier">Web Tier</span>
    <span class="app-tier">Application Tier</span>
    <span class="data-tier">Data Tier</span>
  </div>
  <figcaption>Figure 3: Three-tier network architecture diagram showing web servers, application servers, and database servers with load balancing</figcaption>
</figure>
```

**Quote as figure:**
```html
<figure>
  <blockquote cite="https://example.com/source">
    <p>The only way to do great work is to love what you do.</p>
  </blockquote>
  <figcaption>— Steve Jobs, <cite>Stanford Commencement Speech 2005</cite></figcaption>
</figure>
```

**Video with caption:**
```html
<figure>
  <video controls width="640">
    <source src="tutorial.mp4" type="video/mp4">
    <source src="tutorial.webm" type="video/webm">
    Your browser does not support the video tag.
  </video>
  <figcaption>Video 1: Step-by-step tutorial for assembling the product</figcaption>
</figure>
```

**Accessible figure with ARIA attributes:**
```html
<figure aria-labelledby="fig4-caption" role="figure">
  <img src="infographic.png" alt="" role="img">
  <figcaption id="fig4-caption">
    Figure 4: Environmental impact infographic showing carbon emissions by sector. 
    Transportation accounts for 28%, electricity production for 27%, industry for 22%, 
    and other sources for the remaining 23%.
  </figcaption>
</figure>
```

**Nested figures for detailed illustrations:**
```html
<figure>
  <img src="complete-system.jpg" alt="Complete computer system overview">
  <figcaption>Figure 5: Complete computer system architecture</figcaption>
  
  <figure class="sub-figure">
    <img src="cpu-detail.jpg" alt="CPU architecture detail">
    <figcaption>Figure 5a: CPU internal architecture showing cores and cache</figcaption>
  </figure>
  
  <figure class="sub-figure">
    <img src="memory-detail.jpg" alt="Memory hierarchy detail">
    <figcaption>Figure 5b: Memory hierarchy showing registers, cache, and RAM</figcaption>
  </figure>
</figure>
```

---

## Notes

* **Semantic purpose**: Use for content that is referenced from main text and could be moved to appendix without affecting understanding
* **Not for decorative images**: Use `<div>` or direct `<img>` for purely decorative images
* **Caption requirement**: While `<figcaption>` is optional, it's recommended for providing context and accessibility
* **Accessibility benefits**: 
  - Provides semantic grouping for screen readers
  - Allows proper association between content and its caption
  - Helps users understand content relationships
* **Styling considerations**: Default margins may need adjustment for specific layouts
* **Cross-browser support**: Well-supported in all modern browsers
* **SEO impact**: Helps search engines understand content relationships and context
* **Common mistakes**:
  - Using for layout purposes rather than semantic grouping
  - Placing `<figcaption`> in the middle of content (must be first or last)
  - Using multiple `<figcaption>` elements (only one permitted)
  - Creating empty `<figure>` elements
* **Referencing in text**: Often referenced by number from surrounding content (e.g., "as shown in Figure 1")
* **Print considerations**: Figures may be moved to different pages in print layouts without affecting readability

---
