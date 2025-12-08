# `<iframe>`

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

The `<iframe>` (inline frame) element embeds another HTML document within the current document, creating a nested browsing context. It enables the integration of external content, third-party widgets, advertisements, maps, videos, and other web applications while maintaining isolation between the embedded content and the parent page.

---

## Syntax & Variants

+ **Standard syntax**: `<iframe>...</iframe>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain fallback content between tags
+ **No self-closing variant**: Must be properly closed
+ **Legacy support**: Supported since early HTML versions with evolving security features

---

## Attributes

+ **Core attributes**:
  - `src` (optional): URL of the page to embed
  - `srcdoc` (optional): Raw HTML content to embed directly
  - `name` (optional): Name for targeting links and forms
  - `width`/`height` (optional): Dimensions in CSS pixels or percentage
  - `loading` (optional): lazy/eager loading behavior

+ **Security and sandboxing attributes**:
  - `sandbox` (optional): Security restrictions for embedded content
  - `allow` (optional): Feature policy for specific capabilities
  - `allowfullscreen` (optional): Permit fullscreen mode
  - `referrerpolicy` (optional): Referrer policy for requests

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Deprecated attributes**:
  - `align` (use CSS instead)
  - `frameborder` (use CSS `border` instead)
  - `scrolling` (use CSS `overflow` instead)
  - `marginwidth`/`marginheight` (use CSS `margin` instead)

---

## Content Model

+ **Permitted content**: Fallback content
+ **Fallback content**: Displayed if browser doesn't support iframes or if `src` fails
+ **Text and elements**: Can contain text, images, links, or other HTML
+ **Progressive enhancement**: Fallback content provides alternative access

---

## Context

+ **Valid parents**: Any element that accepts embedded content or flow content
+ **Common locations**:
  - Within `<div>` containers for layout purposes
  - Within `<article>`, `<section>` for embedded content
  - In sidebars, widgets, and embedded applications
  - For ads, maps, videos, and social media embeds
+ **Nested browsing context**: Creates separate document environment

---

## Behavior and Semantics

+ **Default display**: Inline-level element
+ **Default styling**:
  - `display: inline`
  - `border: 2px inset` (varies by browser)
  - `width: 300px`, `height: 150px` (default dimensions)
+ **Loading behavior**:
  - Fetches and renders external document
  - Creates separate browsing context
  - Maintains isolation from parent page
+ **Semantic meaning**:
  - Represents embedded browsing context
  - Screen readers may announce as "frame" or "embedded content"
  - Provides context for nested content
+ **Accessibility**: Requires proper labeling and descriptions

---

## Examples

**Basic iframe embedding:**
```html
<iframe src="https://example.com" width="800" height="600">
  <p>Your browser does not support iframes. 
     <a href="https://example.com">Visit example.com directly</a>.</p>
</iframe>
```

**YouTube video embed:**
```html
<iframe width="560" height="315" 
        src="https://www.youtube.com/embed/dQw4w9WgXcQ" 
        title="YouTube video player" 
        frameborder="0" 
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
        allowfullscreen>
  <p>Watch the video on <a href="https://www.youtube.com/embed/dQw4w9WgXcQ">YouTube</a>.</p>
</iframe>
```

**Google Maps embed:**
```html
<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3024.550808793434!2d-74.005502124249!3d40.712744638906!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x89c25a316e12cd71%3A0x5a1b12d5e15dfcdd!2sNew%20York%2C%20NY!5e0!3m2!1sen!2sus!4v1234567890" 
        width="600" 
        height="450" 
        style="border:0;" 
        allowfullscreen="" 
        loading="lazy" 
        referrerpolicy="no-referrer-when-downgrade"
        title="Map of New York City">
  <p>View the <a href="https://www.google.com/maps/place/New+York,+NY/">map on Google Maps</a>.</p>
</iframe>
```

**Sandboxed iframe with restrictions:**
```html
<iframe src="untrusted-content.html" 
        sandbox="allow-scripts allow-same-origin"
        width="400" 
        height="300"
        title="Sandboxed content">
  <p>This content requires iframe support to display properly.</p>
</iframe>
```

**Inline HTML content with srcdoc:**
```html
<iframe srcdoc="
  <!DOCTYPE html>
  <html>
  <head><title>Embedded Content</title></head>
  <body>
    <h1>Hello from srcdoc!</h1>
    <p>This content is embedded directly in the HTML.</p>
  </body>
  </html>
" width="500" height="200" title="Embedded HTML content">
  <p>Your browser doesn't support srcdoc attribute.</p>
</iframe>
```

**Responsive iframe container:**
```html
<div class="video-container">
  <iframe src="https://player.vimeo.com/video/123456789" 
          width="640" 
          height="360" 
          frameborder="0" 
          allow="autoplay; fullscreen; picture-in-picture" 
          allowfullscreen
          title="Vimeo video player">
  </iframe>
</div>

<style>
.video-container {
  position: relative;
  padding-bottom: 56.25%; /* 16:9 aspect ratio */
  height: 0;
  overflow: hidden;
}

.video-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: none;
}
</style>
```

**Iframe with feature policies:**
```html
<iframe src="https://third-party-widget.com"
        width="300"
        height="200"
        allow="camera 'none'; microphone 'none'; geolocation 'none'"
        sandbox="allow-scripts allow-forms allow-same-origin"
        title="Third-party widget with restricted permissions">
  <p>This widget requires iframe support. 
     <a href="https://third-party-widget.com">Access the widget directly</a>.</p>
</iframe>
```

**Lazy-loaded iframe:**
```html
<iframe src="https://example.com/heavy-content" 
        width="100%" 
        height="400" 
        loading="lazy"
        title="Lazy-loaded external content">
  <p>Loading external content... 
     <a href="https://example.com/heavy-content">View content directly</a>.</p>
</iframe>
```

**Iframe with named target:**
```html
<a href="page1.html" target="content-frame">Page 1</a>
<a href="page2.html" target="content-frame">Page 2</a>
<a href="page3.html" target="content-frame">Page 3</a>

<iframe name="content-frame" 
        src="default.html" 
        width="800" 
        height="600"
        title="Content navigation frame">
  <p>Your browser doesn't support iframes for navigation.</p>
</iframe>
```

---

## Notes

* **Security considerations**: 
  - Use `sandbox` attribute to restrict embedded content capabilities
  - Be cautious with third-party content due to XSS risks
  - Implement Content Security Policy (CSP) for additional protection
* **Performance impact**: 
  - Each iframe creates separate HTTP requests and rendering context
  - Use `loading="lazy"` for below-the-fold iframes
  - Consider the cost of multiple embedded contexts
* **Cross-origin restrictions**:
  - Same-origin iframes have full access to parent context
  - Cross-origin iframes are isolated for security
  - CORS policies apply to cross-origin requests
* **Accessibility requirements**:
  - Always provide a meaningful `title` attribute
  - Include useful fallback content for unsupported scenarios
  - Ensure keyboard navigation works within iframes
* **Browser support**: Universally supported, but security features vary by browser
* **Mobile considerations**:
  - Touch events may behave differently in iframes
  - Responsive design requires proper container styling
  - Some mobile browsers restrict certain iframe features
* **SEO impact**: 
  - Search engines may not index content within iframes
  - Use iframes for supplementary content, not primary content
* **Common pitfalls**:
  - Forgetting to set `title` attribute for accessibility
  - Not providing fallback content
  - Overusing iframes for layout (use CSS instead)
  - Ignoring security implications of embedded content
  - Blocking main thread with synchronous iframe loading
* **Modern alternatives**: Consider using Web Components or `<embed>` for some use cases

---
