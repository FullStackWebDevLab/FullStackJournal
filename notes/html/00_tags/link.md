# `<link>`

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

The `<link>` tag defines a relationship between the current document and an external resource, serving as a crucial mechanism for connecting HTML documents with external assets like stylesheets, icons, preload resources, and alternative content formats. This element enables browsers to establish dependencies and apply external resources without rendering visible content within the document body.

---

## Syntax and Variants

+ The `<link>` tag is a **void element** and does not have a closing tag.
+ In HTML5, the self-closing slash is optional: `<link ...>` or `<link ... />` are both valid.
+ No alternative or legacy forms exist, though attribute requirements vary based on the relationship type being established.

---

## Attributes

The `<link>` tag supports several attributes that define its relationship and behavior:

### Required Attributes

- `href`: Specifies the URL of the linked resource. This is required for most relationship types.
- `rel`: Defines the relationship between the current document and the linked resource. This attribute is mandatory. Common values include:
  - `stylesheet`: External CSS stylesheet
  - `icon`: Favicon or site icon
  - `preload`: Indicates a resource that should be fetched early in page load
  - `preconnect`: Establishes early connection to an origin
  - `alternate`: Alternative version of the document (RSS feed, different language, etc.)
  - `canonical`: Preferred URL for duplicate content

### Optional Attributes

- `type`: Specifies the MIME type of the linked resource (e.g., `text/css` for stylesheets, `image/x-icon` for icons).
- `media`: Defines which media/device the linked resource is optimized for (e.g., `screen`, `print`, `(max-width: 600px)`).
- `sizes`: Specifies icon sizes for `rel="icon"`, using format like `16x16` or `any` for scalable icons.
- `as`: Used with `rel="preload"` to specify the content type for priority handling (e.g., `style`, `script`, `font`, `image`).
- `crossorigin`: Indicates whether the resource should be fetched with a CORS request.
- `integrity`: Contains integrity metadata for subresource integrity verification.
- `hreflang`: Indicates the language of the linked resource.
- `title`: Provides advisory information about the linked resource, particularly for alternate stylesheets.

### Global Attributes

The `<link>` tag supports limited global attributes. While `id` and `class` are supported, most presentation attributes (`style`, etc.) have no effect since the element doesn't render visible content. `data-*` attributes are supported for custom data storage.

---

## Content Model

The `<link>` element is **empty** and must not contain any content. It cannot contain text, other elements, or any child nodes. The element exists purely as a metadata reference with no renderable content of its own.

---

## Context

+ **Placement**: Must be placed within the `<head>` section of the HTML document.
+ **Parent Element**: The `<head>` element is the primary permitted parent.
+ **Usage Limits**:

  - Multiple `<link>` elements can be used to establish different relationships
  - The order of stylesheet links can affect CSS cascade priority
  - Some relationships (like `canonical`) should only appear once per document
  - Preload links should be placed early in the `<head>` for optimal performance

---

## Behavior and Semantics

+ **Rendering**: The `<link>` tag has **no visual representation** in the browser window when used for most relationships
+ **External Resource Loading**: Triggers network requests for external resources like stylesheets, fonts, and icons
+ **Performance Impact**: Can significantly affect page load performance through resource prioritization and preloading
+ **Semantic Impact**:

  - **Styling**: CSS stylesheets applied through `rel="stylesheet"` affect the entire document's presentation
  - **SEO**: Canonical links and alternate language links help search engines understand content relationships
  - **User Experience**: Icons and manifests enable home screen apps and rich mobile experiences
  - **Accessibility**: Alternate stylesheets and print stylesheets can improve accessibility across different contexts

---

## Examples

### Basic Example: Essential Links

This example shows the most common `<link>` elements for a basic webpage.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Basic Link Examples</title>
    <!-- Main stylesheet -->
    <link rel="stylesheet" href="styles/main.css">
    <!-- Favicon -->
    <link rel="icon" href="images/favicon.ico" type="image/x-icon">
    <!-- Print stylesheet -->
    <link rel="stylesheet" href="styles/print.css" media="print">
</head>
<body>
    <!-- Page content -->
</body>
</html>
```

### Intermediate Example: Advanced Resource Loading

This example demonstrates performance optimization and multiple resource types.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Advanced Link Examples</title>
    <!-- Preconnect to CDN for faster resource loading -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    
    <!-- Preload critical resources -->
    <link rel="preload" href="fonts/primary.woff2" as="font" type="font/woff2" crossorigin>
    <link rel="preload" href="css/critical.css" as="style">
    
    <!-- Main stylesheets -->
    <link rel="stylesheet" href="css/main.css">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap">
    
    <!-- Multiple icon sizes for different devices -->
    <link rel="icon" href="/favicon-32x32.png" sizes="32x32" type="image/png">
    <link rel="icon" href="/favicon-192x192.png" sizes="192x192" type="image/png">
    <link rel="apple-touch-icon" href="/apple-touch-icon.png">
</head>
<body>
    <!-- Page content -->
</body>
</html>
```

### Advanced Example: SEO and Alternate Content

This example shows `<link>` elements for search engine optimization and content syndication.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>SEO Link Examples</title>
    
    <!-- Canonical URL to avoid duplicate content -->
    <link rel="canonical" href="https://example.com/article/123">
    
    <!-- RSS feed -->
    <link rel="alternate" type="application/rss+xml" title="RSS Feed" href="/rss.xml">
    
    <!-- Alternate languages -->
    <link rel="alternate" hreflang="es" href="https://example.com/es/article/123">
    <link rel="alternate" hreflang="fr" href="https://example.com/fr/article/123">
    <link rel="alternate" hreflang="x-default" href="https://example.com/article/123">
    
    <!-- PWA manifest -->
    <link rel="manifest" href="/app.webmanifest">
    
    <!-- Stylesheets with integrity checking -->
    <link rel="stylesheet" href="https://cdn.example.com/bootstrap.css" 
          integrity="sha384-abc123..." crossorigin="anonymous">
</head>
<body>
    <!-- Page content -->
</body>
</html>
```

### Specialized Example: Alternate Stylesheets and Preloading

This example demonstrates user-selectable stylesheets and advanced preloading strategies.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Specialized Link Examples</title>
    
    <!-- Default stylesheet -->
    <link rel="stylesheet" href="styles/default.css" title="Default">
    
    <!-- Alternate stylesheets (user-selectable in some browsers) -->
    <link rel="alternate stylesheet" href="styles/high-contrast.css" title="High Contrast">
    <link rel="alternate stylesheet" href="styles/large-text.css" title="Large Text">
    
    <!-- Preload critical images -->
    <link rel="preload" href="images/hero-banner.jpg" as="image" media="(min-width: 600px)">
    <link rel="preload" href="images/hero-banner-mobile.jpg" as="image" media="(max-width: 599px)">
    
    <!-- DNS prefetch for external domains -->
    <link rel="dns-prefetch" href="//analytics.example.com">
    <link rel="dns-prefetch" href="//cdn.example.com">
</head>
<body>
    <!-- Page content -->
</body>
</html>
```

---

## Notes

* **Deprecated Attributes**: 

  - `charset`: Previously used to specify character encoding of linked resource (deprecated in HTML5)
  - `rev`: Previously used for reverse relationship (deprecated in favor of using `rel` with appropriate value)
  - `target`: Was incorrectly used in some early specifications but never properly supported

* **Browser-Specific Behavior**:

  - Alternate stylesheets (`rel="alternate stylesheet"`) are only user-selectable in some browsers (Firefox supports this, while Chrome and Safari do not)
  - Preload support varies across browsers, with older browsers ignoring the `as` attribute
  - Icon sizes and formats have different support levels across browsers and devices

* **Common Pitfalls**:

  - Forgetting the `rel` attribute, which is required for the link to function properly
  - Using `rel="stylesheet"` without `type="text/css"` (while optional in HTML5, some validators may flag this)
  - Placing `<link>` elements in the `<body>` (invalid in HTML4, allowed in HTML5 but still recommended in `<head>`)
  - Overusing preload can harm performance by prioritizing non-critical resources

* **Performance Considerations**:

  - Stylesheets with `rel="stylesheet"` are render-blocking by default
  - Preload links should be used sparingly for critical resources only
  - The `media` attribute can prevent unnecessary loading of resources that won't be used
  - `preconnect` and `dns-prefetch` can improve perceived performance for third-party resources

* **Security Implications**:

  - The `integrity` attribute enables Subresource Integrity (SRI) to prevent tampered resources from being loaded
  - `crossorigin` attribute is required for CORS requests when using SRI or loading fonts from CDNs
  - Be cautious when loading resources from untrusted third-party domains

* **HTML Version Differences**:

  - HTML5 made the `type` attribute optional for CSS stylesheets
  - HTML5 introduced several new `rel` values like `preload`, `manifest`, and `dns-prefetch`
  - The `sizes` attribute was introduced in HTML5 for better icon management

---
