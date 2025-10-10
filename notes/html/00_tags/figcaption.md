# `<figcaption>`

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

The `<figcaption>` element represents a caption or legend describing the rest of the contents of its parent `<figure>` element. It provides contextual information, explanations, credits, or references for the content contained within the figure, establishing a semantic relationship between the caption and the figure content for both visual users and assistive technologies.

---

## Syntax and Variants

+ **Standard syntax**: `<figcaption>...</figcaption>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain text and inline elements
+ **No self-closing variant**: Must contain content
+ **HTML5 introduction**: Added in HTML5 alongside `<figure>` to provide semantic captioning
+ **Single instance**: Only one `<figcaption>` allowed per `<figure>`

---

## Attributes

+ **Global attributes only**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional
+ **No element-specific attributes**: Relies on semantic relationship with parent `<figure>`
+ **Commonly used**: `class`, `id` for styling and scripting

---

## Content Model

+ **Permitted content**: Flow content
+ **Allowed elements**:
  - Text and character references
  - Phrasing content: `<a>`, `<strong>`, `<em>`, `<span>`, `<code>`, etc.
  - Some interactive elements in appropriate contexts
+ **Not recommended**: Block-level elements (though technically allowed in flow content)
+ **Text-heavy**: Primarily intended for textual descriptions and labels

---

## Context

+ **Required parent**: Must be a direct child of a `<figure>` element
+ **Position restrictions**: Must be either the first or last child of its parent `<figure>`
+ **Single instance**: Only one `<figcaption>` element permitted per `<figure>`
+ **Invalid contexts**: Cannot be used outside of a `<figure>` element

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - `text-align: center` (in some browsers)
  - `font-style: italic` (in some browsers)
  - Typically inherits font properties from parent
+ **Semantic meaning**:
  - Represents a caption for its parent `<figure>`
  - Creates an explicit association between caption and figure content
  - Screen readers announce the relationship between figure and caption
  - Helps establish content hierarchy and relationships
+ **Accessibility**: 
  - Provides essential context for figure content
  - Screen readers may read caption before or after figure content
  - Establishes programmatic relationship with parent figure

---

## Examples

**Basic image caption:**
```html
<figure>
  <img src="landscape.jpg" alt="Mountain range at sunrise">
  <figcaption>Figure 1: The Himalayan mountain range during golden hour</figcaption>
</figure>
```

**Caption as first child:**
```html
<figure>
  <figcaption>Chart 2: Monthly user growth metrics for 2024</figcaption>
  <img src="growth-chart.png" alt="Line chart showing steady user growth">
</figure>
```

**Caption with inline formatting:**
```html
<figure>
  <img src="code-screenshot.png" alt="JavaScript code example">
  <figcaption>
    <strong>Listing 3:</strong> React component demonstrating 
    <code>useState</code> hook usage with proper cleanup
  </figcaption>
</figure>
```

**Complex caption with citations and links:**
```html
<figure>
  <img src="historical-map.jpg" alt="Ancient Roman empire map">
  <figcaption>
    <strong>Map 4:</strong> The Roman Empire at its greatest extent in 117 AD. 
    Source: <a href="https://example.com/atlas">Historical Atlas of Ancient Rome</a>, 
    based on data from <cite>The Cambridge Ancient History</cite>.
  </figcaption>
</figure>
```

**Caption with accessibility enhancements:**
```html
<figure aria-labelledby="fig5-caption">
  <img src="infographic.png" alt="Data visualization of climate change impacts">
  <figcaption id="fig5-caption">
    Figure 5: Global temperature anomalies from 1880 to 2020. 
    The chart shows a clear warming trend beginning in the late 20th century, 
    with the most rapid increase occurring since 1980. Data source: NASA GISS.
  </figcaption>
</figure>
```

**Multiple figures with consistent caption styling:**
```html
<figure class="technical-diagram">
  <img src="system-architecture.png" alt="Three-tier web application architecture">
  <figcaption class="diagram-caption">
    Diagram 6: System architecture showing load balancers, web servers, 
    application servers, and database clusters with failover capabilities.
  </figcaption>
</figure>

<figure class="technical-diagram">
  <img src="data-flow.png" alt="Data flow between microservices">
  <figcaption class="diagram-caption">
    Diagram 7: Data flow sequence between authentication service, 
    user profile service, and notification service using message queues.
  </figcaption>
</figure>
```

**Caption with numbered reference and description:**
```html
<figure>
  <figcaption>
    <span class="figure-number">Figure 8</span>: 
    <span class="figure-description">Comparison of algorithm performance metrics. 
    The left chart shows time complexity, while the right chart displays 
    memory usage across different input sizes.</span>
  </figcaption>
  <div class="comparison-charts">
    <img src="time-complexity.png" alt="Time complexity comparison chart">
    <img src="memory-usage.png" alt="Memory usage comparison chart">
  </div>
</figure>
```

**Video with detailed caption:**
```html
<figure>
  <video controls width="800">
    <source src="tutorial.mp4" type="video/mp4">
    <source src="tutorial.webm" type="video/webm">
  </video>
  <figcaption>
    Video 9: Step-by-step assembly tutorial for the Model X device. 
    This demonstration covers initial setup, calibration, and safety 
    precautions. Total runtime: 4 minutes, 32 seconds.
  </figcaption>
</figure>
```

---

## Notes

* **Position importance**: The placement (first or last child) affects reading order for screen readers
* **Required context**: Only meaningful when used within a `<figure>` element
* **Accessibility critical**: Provides essential context that may not be apparent from the figure content alone
* **Single instance**: Only one `<figcaption>` per `<figure>` is allowed by specification
* **Styling flexibility**: No default styling constraints—can be extensively customized with CSS
* **SEO benefits**: Captions provide additional context that search engines can use for understanding content
* **Common mistakes**:
  - Using outside of `<figure>` element
  - Including multiple `<figcaption>` elements in one `<figure>`
  - Placing in the middle of figure content (must be first or last)
  - Writing overly verbose or unclear captions
  - Using for decorative text rather than descriptive content
* **Best practices**:
  - Keep captions concise but informative
  - Use consistent numbering or labeling systems
  - Include citations and credits when appropriate
  - Ensure captions provide value beyond what's visible in the figure
  - Consider reading order when choosing caption position
* **Browser support**: Well-supported in all modern browsers as part of HTML5

---
