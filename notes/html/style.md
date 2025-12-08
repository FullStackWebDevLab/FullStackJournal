# `<style>`

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

The `<style>` tag contains CSS style rules that apply to the current HTML document, enabling authors to embed style information directly within the document rather than linking to external stylesheets. This element serves as a mechanism for defining document-specific styling, critical CSS, or styles that are tightly coupled with the document's structure and content.

---

## Syntax and Variants

+ The `<style>` tag requires both an opening `<style>` and closing `</style>` tag.
+ It is a non-void element that contains CSS text content.
+ No alternative or legacy forms exist, though the `type` attribute was previously required in HTML4 but is optional in HTML5 .

---

## Attributes

The `<style>` tag supports several attributes that control its behavior and scope:

**`media`**  
Specifies which media/device the styles are optimized for. Accepts media queries like:
- `screen` (default): Computer screens
- `print`: Printers and print preview
- `all`: All devices
- `(max-width: 600px)`: Specific viewport conditions
- `(orientation: landscape)`: Device orientation

**`type`**  
Specifies the MIME type of the style language. For CSS, this is `text/css`. In HTML5, this attribute is **optional** and defaults to `text/css` if omitted. Previously required in HTML4.

**`scoped`** **(Deprecated)**  
Originally intended to limit styles to the containing parent element only. This attribute was implemented in some browsers but has been **removed from the specification** and should not be used.

**`title`**  
Specifies an advisory title for the style sheet. When used, the styles become "alternate style sheets" that users can select in some browsers.

**Global Attributes:**  
The `<style>` tag supports most global attributes including `id`, `class`, `data-*`, and `nonce`. The `id` and `class` attributes are particularly useful for JavaScript targeting and CSS referencing. The `nonce` attribute is important for Content Security Policy (CSP) implementations.

**Blocking Attributes:**  
- `blocking`: Experimental attribute to indicate that certain operations should be blocked until the style sheet loads

---

## Content Model

The `<style>` element contains **text content** that must be valid CSS syntax. The content model follows these rules:

- Contains only text/CSS data; no HTML elements are permitted
- CSS rules follow standard CSS syntax with selectors, properties, and values
- Comments can be included using CSS comment syntax (`/* ... */`)
- The content is parsed as CSS, not HTML, so special characters like `<`, `>`, and `&` don't need HTML escaping
- If the `type` attribute is set to anything other than `text/css` (or omitted), the content is treated as inert data and not processed as CSS

**Restrictions:**
- Cannot contain child elements
- HTML tags within style content are treated as text, not parsed as HTML
- Script elements or other non-text content are not permitted

---

## Context

+ **Placement**: Typically placed within the `<head>` section of the HTML document, but HTML5 also allows placement in the `<body>` with specific restrictions
+ **Preferred Location**: In the `<head>` element for optimal rendering performance
+ **Body Placement**: When used in `<body>`, must follow "body-ok" content model rules and cannot be placed where phrasing content is expected
+ **Usage Limits**: 
  - Multiple `<style>` elements are permitted in a single document
  - Styles are applied in document order (cascade order)
  - No limit on the number of `<style>` elements, though performance considerations apply

---

## Behavior and Semantics

+ **Rendering**: The `<style>` tag itself has **no visual representation** in the browser window, but its CSS content affects the rendering of other elements .
+ **Default CSS**: The element typically has no default styling, though browsers may apply `display: none` to its raw content
+ **Render Blocking**: By default, CSS in `<style>` tags is **render-blocking**; the browser must parse and apply the styles before rendering content
+ **Semantic Impact**:

  - **Styling**: Directly controls visual presentation of document elements
  - **Performance**: Inline styles can improve performance for critical CSS by reducing HTTP requests
  - **Maintenance**: Embedded styles are specific to a single document, which can complicate site-wide consistency
  - **Cascade**: Styles follow standard CSS cascade rules, with specificity and source order determining precedence

---

## Examples

### Basic Example: Simple Embedded Styles

This example shows basic CSS rules within a `<style>` element.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Basic Style Example</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 20px;
        }
        
        h1 {
            color: #2c3e50;
            border-bottom: 2px solid #3498db;
        }
        
        .highlight {
            background-color: yellow;
            padding: 2px 4px;
        }
    </style>
</head>
<body>
    <h1>Styled Heading</h1>
    <p>This paragraph has <span class="highlight">highlighted text</span>.</p>
</body>
</html>
```

### Intermediate Example: Media Queries and Organization

This example demonstrates media-specific styles and more complex CSS organization.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Style Example</title>
    <style>
        /* Base styles */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .sidebar {
            width: 25%;
            float: left;
        }
        
        .main-content {
            width: 75%;
            float: left;
        }
        
        /* Print styles */
        @media print {
            .sidebar, .no-print {
                display: none;
            }
            
            .main-content {
                width: 100%;
                float: none;
            }
            
            body {
                font-size: 12pt;
                color: black;
            }
        }
        
        /* Mobile styles */
        @media (max-width: 768px) {
            .sidebar, .main-content {
                width: 100%;
                float: none;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <aside class="sidebar">
            <nav>Navigation menu</nav>
        </aside>
        <main class="main-content">
            <article>Main article content</article>
        </main>
    </div>
</body>
</html>
```

### Advanced Example: CSS Variables and Complex Selectors

This example shows advanced CSS features within a `<style>` element.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Advanced Style Example</title>
    <style>
        :root {
            --primary-color: #3498db;
            --secondary-color: #2c3e50;
            --spacing-unit: 1rem;
            --border-radius: 4px;
        }
        
        .card {
            background: white;
            border-radius: var(--border-radius);
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            padding: calc(var(--spacing-unit) * 2);
            margin-bottom: var(--spacing-unit);
        }
        
        .card h2 {
            color: var(--primary-color);
            margin-top: 0;
        }
        
        /* Complex selectors */
        .card:hover {
            transform: translateY(-2px);
            transition: transform 0.2s ease;
        }
        
        /* Attribute selectors */
        input[type="text"]:focus {
            border-color: var(--primary-color);
            outline: none;
        }
        
        /* CSS Grid */
        .grid-layout {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: var(--spacing-unit);
        }
    </style>
</head>
<body>
    <div class="grid-layout">
        <div class="card">
            <h2>Card Title</h2>
            <p>Card content with advanced styling.</p>
            <input type="text" placeholder="Focus me to see effect">
        </div>
    </div>
</body>
</html>
```

### Specialized Example: CSP and Scoped Styles (Historical)

This example shows security considerations and the deprecated scoped attribute.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Security and Scoped Styles</title>
    <!-- Example of CSP nonce usage -->
    <style nonce="abc123">
        .secure-style {
            color: green;
        }
    </style>
</head>
<body>
    <section>
        <!-- Deprecated scoped attribute (do not use in production) -->
        <style scoped>
            /* This style was meant to only apply to the parent section */
            .scoped-style {
                background: #f0f0f0;
                padding: 10px;
            }
        </style>
        <div class="scoped-style">
            This would have been scoped to this section only (attribute deprecated)
        </div>
    </section>
    
    <div class="secure-style">
        This uses styles with CSP protection
    </div>
</body>
</html>
```

---

## Notes

* **Deprecated Attributes**: 

  - `scoped`: This attribute was removed from the specification after poor browser support and complexity issues. Use CSS methodologies like BEM or CSS-in-JS instead for component scoping.

* **Performance Implications**:

  - Large `<style>` blocks can delay rendering as they must be parsed before content display
  - Critical CSS in `<style>` tags can improve perceived performance by avoiding external resource requests
  - Multiple small `<style>` tags throughout a document can harm maintainability and performance

* **Security Considerations**:

  - The `nonce` attribute is crucial for Content Security Policy (CSP) to prevent inline style injection attacks
  - Without proper CSP, inline styles can be vulnerable to XSS attacks if user content is not properly sanitized
  - Consider using hashes instead of nonces for static content

* **Common Pitfalls**:

  - Forgetting that CSS within `<style>` follows the same cascade rules as external CSS
  - Placing massive CSS frameworks inline, which defeats caching benefits
  - Using deprecated attributes like `scoped` that are no longer supported
  - Not considering the render-blocking nature of `<style>` elements

* **Browser Quirks**:

  - Some older browsers had limits on the size of `<style>` content
  - The `type` attribute was required in HTML4 but is optional in HTML5
  - Browser dev tools typically display `<style>` content in their CSS inspectors
  - Dynamic modifications to `<style>` content can trigger style recalculations

* **Best Practices**:

  - Use `<style>` for document-specific styles and critical CSS only
  - Place `<style>` elements in the `<head>` for optimal rendering performance
  - Use external stylesheets for site-wide styles to leverage browser caching
  - Consider build processes that extract critical CSS into `<style>` tags
  - Implement CSP with nonces or hashes for security

---
