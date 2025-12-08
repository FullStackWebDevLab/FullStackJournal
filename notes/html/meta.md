# `<meta>` HTML Tag

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

The `<meta>` tag defines metadata about an HTML document; data about the document's data that isn't displayed on the page itself but is machine-parsable . This metadata serves critical functions for browsers, search engines, and other web services by specifying character sets, page descriptions, keywords, authors, viewport settings, and pragma directives.

---

## Syntax & Variants

+ The `<meta>` tag is a **void element** and does not have a closing tag .
+ In HTML5, the self-closing slash is optional: `<meta ...>` or `<meta ... />` are both valid.
+ Legacy forms include using `http-equiv="content-type"` for character encoding, largely superseded by the `charset` attribute in HTML5 .

---

## Attributes

The `<meta>` tag supports several important attributes that define its purpose and functionality:

**`charset`**  
Specifies the character encoding for the HTML document. Common values include `UTF-8` (most widely used), `ISO-8859-1`, and others. This attribute provides a simpler alternative to the older `http-equiv="Content-Type"` method.

**`name`**  
Defines the name of the metadata property. Common values include:
- `viewport`: Controls viewport size and scaling for responsive design
- `description`: Provides a page description for search engines
- `author`: Specifies the page author
- `keywords`: Lists keywords related to page content (largely ignored by modern search engines)
- `robots`: Instructs search engine crawlers on indexing behavior

**`content`**  
Contains the value associated with the `name` or `http-equiv` attribute. This attribute is required when either `name` or `http-equiv` is specified.

**`http-equiv`**  
Provides pragma directives that emulate HTTP headers. Common values include:
- `refresh`: Defines automatic page refresh or redirect intervals
- `content-type`: Specifies document type and character encoding (largely superseded by `charset`)
- `default-style`: Indicates the preferred stylesheet
- `content-security-policy`: Defines Content Security Policy rules

**`media`**  
Specifies which media/device the linked resource is optimized for. This attribute is primarily relevant when used with `name="theme-color"` to define different theme colors for various screen sizes.

**Attribute Requirements:**
- Exactly one of `name`, `http-equiv`, or `charset` must be set
- The `content` attribute is mandatory when using `name` or `http-equiv`
- No attributes are strictly required, but the element is useless without at least `charset`, `name`, or `http-equiv`

**Global Attributes:**  
The `<meta>` tag supports all global attributes including `id`, `class`, `style`, `data-*`, and `aria-*` attributes, though many of these have limited practical use since the element doesn't render visible content.

---

## Content Model

The `<meta>` element is **empty** and must not have any content . It cannot contain text, other elements, or any child nodes.

---

## Context

+ **Placement**: Must be placed within the `<head>` section of the HTML document .
+ **Parent Element**: The `<head>` element is the primary permitted parent .
+ **Usage Limits**: 
  - A document should not contain more than one `<meta>` element with a `charset` attribute .
  - Some specific metadata names, like `application-name` and `description`, should not be used more than once per document .

---

## Behavior and Semantics

+ **Rendering**: The `<meta>` tag has **no visual representation** in the browser window and does not affect layout or styling.
+ **Default CSS**: No default CSS settings are applied.
+ **Semantic Impact**: 
  - **SEO**: Provides search engines with page descriptions, which can influence click-through rates from search results. The `keywords` meta tag, however, is largely ignored by modern search engines like Google.
  - **Accessibility**: Proper use of the `viewport` meta tag is crucial for responsive design, ensuring content is accessible and usable on mobile devices.
  - **Browser Instructions**: Directs browser behavior, such as character encoding interpretation, page refresh intervals, and viewport control.

---

## Examples

### Basic Example: Essential Metadata

This example shows the most common meta tags for a basic webpage.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="A beginner's guide to HTML and CSS.">
    <meta name="author" content="Jane Doe">
    <title>Page Title</title>
</head>
<body>
    <!-- Page content goes here -->
</body>
</html>
```

### Intermediate Example: Search Engine and Refresh Directives

This example includes directives for search engine crawling and an automatic page refresh.

```html
<head>
    <meta charset="UTF-8">
    <meta name="description" content="Free Web tutorials for HTML and CSS">
    <meta name="robots" content="index, follow">
    <!-- Refreshes the page after 30 seconds. -->
    <meta http-equiv="refresh" content="30">
    <title>Web Tutorials</title>
</head>
```

### Advanced Example: Complex Redirect and Social Media

This example demonstrates a timed redirect to another URL.

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- Redirects to a new page after 3 seconds -->
    <meta http-equiv="refresh" content="3;url=https://www.example.com/new-page">
    <title>Redirecting...</title>
</head>
```

---

## Notes

* **Deprecated/Unsupported Forms**: 

  - The `meta keywords` tag (`<meta name="keywords" ...>`) is **no longer used** by Google Search and has no effect on ranking.
  - The `next` and `prev` `rel` attributes in `<link>` tags are also ignored by Google.

* **Differences Across HTML Versions**:

  - In HTML5, the `charset` attribute was introduced as a simpler alternative to `<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">`.
  - HTML5 formally defines the `<meta>` element as a void element, clarifying that it cannot have content.

* **Common Pitfalls**:

  - Placing `<meta>` tags outside the `<head>` section, which is invalid.
  - Using the `keywords` meta tag for SEO as a primary strategy, which is ineffective with modern search engines.
  - Forgetting the `content` attribute when using `name` or `http-equiv`.

* **Browser Quirks**:

  - The viewport meta tag is not a web standard but is consistently implemented by all major browsers due to its critical importance for mobile rendering.
  - For a page redirect, using an HTTP `301` server-side redirect is more reliable than `http-equiv="refresh"`, which is not supported uniformly and can be confusing for users.

---
