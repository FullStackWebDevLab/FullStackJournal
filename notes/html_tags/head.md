# `<head>`

## Key Topics

+ [Definition and Purpose](#definition-and-purpose)  
+ [Syntax & Variants](#syntax--variants)  
+ [Attributes](#attributes)  
+ [Content Model](#content-model)  
+ [Context](#context)  
+ [Behavior and Semantics](#behavior-and-semantics)  
+ [Examples](#examples)  
+ [Notes](#notes)

---

## Definition and Purpose  

The `<head>` element is a container for **metadata** and document-level instructions. It holds elements that inform browsers, search engines, or other agents about the document (e.g. title, styles, scripts), rather than content to be displayed.

---

## Syntax & Variants  

+ Opening tag: `<head>`  
+ Closing tag: `</head>`  
+ It is not self-closing; it must have both opening and closing tags.  
+ In certain malformed documents or in error correction (by user agents), browser may implicitly insert a `<head>` section if it is missing.

---

## Attributes  

The `<head>` element supports **global attributes** (such as `id`, `class`, `data-*`, `aria-*`). It **does not** have its own special attributes beyond globals.  

---

## Content Model  

+ The `<head>` can contain only certain elements, not arbitrary content or body-level elements.
+ Typical permitted child elements include:
  - `<title>` (should appear exactly once)  
  - `<meta>`  
  - `<link>`  
  - `<style>`  
  - `<script>`  
  - `<base>`  
  - `<noscript>`  
+ No text nodes (besides maybe whitespace or comments) outside permitted child elements.  
+ The order among those children has some practical conventions (e.g. `<meta charset>` early).

---

## Context  

+ `<head>` must be placed immediately after the opening `<html>` tag (and before `<body>`).
+ There must be **at most one** `<head>` element.
+ If missing, browsers may implicitly create one.
+ It is valid only in HTML documents (e.g. when document is parsed as HTML). In XML / XHTML, similar rules apply, but XML syntax constraints come into play.

---

## Behavior and Semantics  

+ **Rendering / Visibility**  
  Elements inside `<head>` are not rendered as page content; they do not appear in the visual layout.

+ **Effect on parsing / document behavior**  
  - `<title>` defines the document title shown in browser tabs or windows.  
  - `<meta charset>` influences character decoding and parsing.  
  - Stylesheets and script references inside `<head>` influence resource loading, CSS cascades, and script execution order.  
  - The `<base>` element (if present) sets a base URL for all relative URLs in the document.  
  - Scripts placed in `<head>` may block parsing, unless attributes like `defer` or `async` are used.  

+ **SEO / Search Engine / Crawling**  
  Metadata inside `<head>` (meta description, meta robots, canonical links) is read by crawlers and used in indexing, ranking, and snippet generation.  

+ **Performance / Best Practices**  
  Placing critical metadata and links early helps browsers fetch resources sooner. Some suggest keeping scripts that block rendering out of `<head>` or deferring them.  

---

## Examples  

**Minimal head:**

```html
<head>
  <title>My Page</title>
</head>
```

**Typical head with metadata, styles, scripts:**

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Page</title>
  <link rel="stylesheet" href="styles.css">
  <script src="app.js" defer></script>
</head>
```

**Including `<base>` and inline style:**

```html
<head>
  <base href="https://example.com/">
  <meta charset="UTF-8">
  <title>Base Example</title>
  <style>
    body { margin: 0; }
  </style>
</head>
```

**With fallback for no JavaScript:**

```html
<head>
  <meta charset="UTF-8">
  <title>With noscript</title>
  <script src="main.js"></script>
  <noscript>
    <style>
      .js-only { display: none; }
    </style>
  </noscript>
</head>
```

---

## Notes

* The `<title>` element is required in a valid HTML head. Omitting it leads to invalid or less meaningful documents.
* Though HTML5 allows more leniency, placing `<meta charset>` early (ideally first child) is strongly recommended to avoid mis-interpretation of character encoding.
* Scripts placed without `defer` or `async` in `<head>` may block page parsing and negatively affect performance.
* Some document generators or templates may mistakenly place scripts or styles outside `<head>` or in incorrect order; this can lead to unpredictable behavior.
* The `<head>` section may grow large (many metadata tags, social media tags, favicons, etc.); organizing it thoughtfully helps maintain readability.

---
