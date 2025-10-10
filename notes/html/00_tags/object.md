# `<object>`

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

The `<object>` element represents an external resource that can be treated as an image, nested browsing context, or resource to be handled by a plugin. It provides a flexible mechanism for embedding various types of content with robust fallback capabilities, supporting everything from images and PDFs to custom plugin content while maintaining accessibility and progressive enhancement.

---

## Syntax & Variants

+ **Standard syntax**: `<object>...</object>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain parameters and fallback content
+ **No self-closing variant**: Must be properly closed
+ **Versatile embedder**: Supports multiple content types through same element

---

## Attributes

+ **Core attributes**:
  - `data` (optional): URL of the resource to embed
  - `type` (optional): MIME type of the resource
  - `width`/`height` (optional): Dimensions in CSS pixels
  - `name` (optional): Name for form submission or scripting
  - `form` (optional): Associates object with a form

+ **Plugin-specific attributes**:
  - `typemustmatch` (optional): Requires `type` to match resource content

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Deprecated attributes**:
  - `archive` (resource archives)
  - `classid` (class identifier)
  - `codebase` (base path)
  - `codetype` (code MIME type)
  - `declare` (declaration only)

---

## Content Model

+ **Permitted content**:
  - Zero or more `<param>` elements (must come first)
  - Flow content as fallback (if external resource not supported)
  - Transparent content model when used with `data` attribute
+ **Fallback hierarchy**: Browser tries each option in order until one works
+ **Parameter support**: `<param>` elements configure plugin behavior

---

## Context

+ **Valid parents**: Any element that accepts embedded content or flow content
+ **Common locations**:
  - Within `<div>` containers for embedded resources
  - Within `<figure>` for captioned embedded content
  - In forms for complex input types
  - For PDFs, images, and other document types
+ **Embedded content**: Treated as replaced element when successful

---

## Behavior and Semantics

+ **Default display**: Inline-level element
+ **Default styling**:
  - `display: inline`
  - No intrinsic dimensions
  - Appearance depends on embedded content type
+ **Loading behavior**:
  - Browser attempts to handle resource based on MIME type
  - Falls back to nested content if resource cannot be handled
  - Can use plugins or native browser capabilities
+ **Semantic meaning**:
  - Represents embedded external resource
  - Screen readers announce based on content type and fallbacks
  - Provides context for embedded content
+ **Accessibility**: Fallback content provides accessibility support

---

## Examples

**Basic PDF embedding with fallback:**
```html
<object data="document.pdf" type="application/pdf" width="800" height="600">
  <p>Your browser doesn't support PDF embedding. 
     <a href="document.pdf">Download the PDF</a> instead.</p>
</object>
```

**Image with fallback text:**
```html
<object data="chart.svg" type="image/svg+xml" width="400" height="300">
  <img src="chart.png" alt="Bar chart showing quarterly results">
  <p>Access the <a href="data.csv">raw data</a> in CSV format.</p>
</object>
```

**Flash content with parameters (legacy):**
```html
<object data="game.swf" type="application/x-shockwave-flash" width="550" height="400">
  <param name="movie" value="game.swf">
  <param name="quality" value="high">
  <param name="allowFullScreen" value="true">
  <embed src="game.swf" type="application/x-shockwave-flash" width="550" height="400">
  <p>This content requires Flash Player. 
     <a href="game.html">Play the HTML5 version</a> instead.</p>
</object>
```

**Video with multiple fallbacks:**
```html
<object data="video.mp4" type="video/mp4" width="640" height="360">
  <object data="video.webm" type="video/webm" width="640" height="360">
    <object data="video.ogv" type="video/ogg" width="640" height="360">
      <video controls width="640" height="360">
        <source src="video.mp4" type="video/mp4">
        <source src="video.webm" type="video/webm">
        <p>Your browser doesn't support HTML5 video. 
           <a href="video.mp4">Download the video</a>.</p>
      </video>
    </object>
  </object>
</object>
```

**Embedded HTML page:**
```html
<object data="widget.html" type="text/html" width="300" height="200">
  <iframe src="widget.html" width="300" height="200">
    <p>View the <a href="widget.html">widget page directly</a>.</p>
  </iframe>
</object>
```

**SVG with script interaction:**
```html
<object data="interactive-diagram.svg" 
        type="image/svg+xml" 
        width="500" 
        height="400"
        id="svg-object">
  <img src="diagram.png" alt="System architecture diagram">
</object>

<script>
document.getElementById('svg-object').addEventListener('load', function() {
  const svgDoc = this.getSVGDocument();
  // Manipulate SVG content here
});
</script>
```

**Form-associated object:**
```html
<form id="data-form">
  <object data="configurator.swf" 
          type="application/x-shockwave-flash" 
          width="400" 
          height="300"
          name="configurator"
          form="data-form">
    <p>Use the <a href="configurator.html">HTML configurator</a> instead.</p>
  </object>
  <button type="submit">Submit Configuration</button>
</form>
```

**Responsive PDF container:**
```html
<div class="pdf-container">
  <object data="presentation.pdf" 
          type="application/pdf" 
          width="100%" 
          height="600"
          aria-label="Company presentation PDF">
    <div class="pdf-fallback">
      <p>PDF viewer not available. Alternative options:</p>
      <ul>
        <li><a href="presentation.pdf">Download PDF</a></li>
        <li><a href="presentation.html">View HTML version</a></li>
        <li><a href="presentation.txt">Plain text version</a></li>
      </ul>
    </div>
  </object>
</div>

<style>
.pdf-container {
  position: relative;
  width: 100%;
  max-width: 900px;
  margin: 0 auto;
}

.pdf-container object {
  border: 1px solid #ddd;
  border-radius: 4px;
}
</style>
```

**Custom MIME type with typemustmatch:**
```html
<object data="custom-format.cst" 
        type="application/x-custom-format"
        typemustmatch
        width="400" 
        height="300">
  <p>This content requires a custom viewer. 
     <a href="custom-format.cst">Download the file</a> and open with the appropriate application.</p>
</object>
```

---

## Notes

* **Progressive enhancement**: The nested fallback structure provides excellent degradation
* **Modern usage**: Primarily used for PDF embedding and as a container for other embed methods
* **Browser support**: Well-supported but actual content rendering depends on available handlers
* **Accessibility benefits**: 
  - Fallback content provides accessible alternatives
  - Screen readers can access nested text content
  - Better than `<embed>` for accessibility
* **Security considerations**:
  - Embedded content runs with same origin privileges
  - Cross-origin restrictions apply
  - Consider Content Security Policy for embedded resources
* **Performance**: 
  - Each object creates separate rendering context
  - Resource loading can block page rendering
* **Common use cases**:
  - PDF document embedding
  - SVG with script interaction
  - Legacy plugin content with fallbacks
  - Multi-format resource delivery
* **Comparison with alternatives**:
  - More robust than `<embed>` due to fallback support
  - More flexible than `<iframe>` for non-HTML content
  - Better accessibility than plugin-based embeds
* **Common pitfalls**:
  - Forgetting to include meaningful fallback content
  - Not specifying `type` attribute
  - Assuming all browsers can handle specific MIME types
  - Overlooking accessibility of embedded content
* **Future considerations**: Moving toward native HTML5 elements for most media types

---
