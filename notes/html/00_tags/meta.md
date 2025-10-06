# `<meta>`

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

The `<meta>` element provides **metadata** about the HTML document; that is, data about the document (e.g. its character encoding, description, viewport hints, or HTTP-equivalent headers).

Metadata is not rendered on the page itself, but informs browsers, search engines, and other agents how to interpret or represent the document.

One of its roles is to emulate HTTP headers (e.g. content type, refresh) when server headers are not available.

---

## Syntax & Variants  

+ `<meta>` is an **empty/self-closing** element. It does not have a separate closing tag (no `</meta>`).
+ In HTML (served as `text/html`), it’s typically written as:

  ```html
  <meta …>
  ```

Some authors include a trailing slash (e.g. `<meta … />`) for XHTML compatibility, though not required in HTML5.

* There are variations depending on purpose:

  * `<meta charset="…">`; declares document character encoding
  * `<meta name="…">` + `content="…"`; generic metadata (description, author, viewport, etc.)
  * `<meta http-equiv="…">` + `content="…"`; HTTP header equivalents (refresh, content-type, etc.)
  * `<meta property="…">` + `content="…">`; often used for Open Graph / social metadata (Facebook, Twitter)

---

## Attributes

Here are the main attributes used with `<meta>`:

* **`charset`**
  Declares the character encoding (e.g. `UTF-8`) for the document. If present, it is the only attribute.

* **`name`**
  Defines the metadata name (e.g. `description`, `viewport`, `author`, `robots`) for which `content` gives the value.

* **`content`**
  The value associated with the `name` or `http-equiv` or other metadata. Required (unless `charset` is used).

* **`http-equiv`**
  Lets you simulate certain HTTP headers (e.g. `refresh`, `content-type`) directly in HTML.

* **`property`**
  For metadata vocabularies like Open Graph (social metadata). Common in `<meta>` tags for rich linking.

Additionally, `<meta>` supports **global attributes** (e.g. `id`, `class`, `data-*`, `aria-*`).

---

## Content Model

* As an empty element, `<meta>` contains **no child content**; it cannot wrap text or other elements.
* In the DOM, it appears as a metadata node (or element) under the `<head>` of the document.

---

## Context

* `<meta>` tags must appear inside the `<head>` section of an HTML document.
* You can have multiple `<meta>` elements (each for different metadata) in the same document.
* It is not permitted inside `<body>` (in normative HTML structure).
* In XHTML or XML serialization, syntax may include self-closing slash (e.g. `<meta … />`).

---

## Behavior and Semantics

* **Rendering / Visibility**: The `<meta>` tag does not produce any visible output in the rendered document.
* **Effect on parsing / layout**:

  * The `charset` meta influences character decoding early during parse, which affects correct interpretation of later text.
  * The `viewport` meta (via `name="viewport"`) impacts how content is scaled or displayed on mobile devices.
  * The `http-equiv="refresh"` can cause a timed reload or redirect of the document.
* **SEO / Search Engine / Crawling**

  * `meta name="description"` may be used as the snippet shown in search results.
  * `meta name="robots"` gives directives to search crawlers (e.g. `noindex`, `nofollow`, `nosnippet`).
  * The `keywords` meta tag is largely ignored by modern search engines.
* **Fallback / Ignorance**
  Agents (browsers, crawlers) may ignore `<meta>` tags they don’t recognize or support.

---

## Examples

**Character encoding:**

```html
<meta charset="UTF-8">
```

**Page description & author:**

```html
<meta name="description" content="A tutorial on the meta tag in HTML.">
<meta name="author" content="John Doe">
```

**Viewport for responsive design:**

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**Refresh / redirect:**

```html
<meta http-equiv="refresh" content="10; url=https://example.com/new-page.html">
```

**Open Graph / social media metadata:**

```html
<meta property="og:title" content="My Web Page">
<meta property="og:description" content="An overview of my page">
<meta property="og:image" content="https://example.com/image.png">
<meta property="og:url" content="https://example.com/page.html">
```

**Combined head snippet:**

```html
<head>
  <meta charset="UTF-8">
  <meta name="description" content="Tutorial on meta tag.">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="robots" content="index, follow">
  <meta property="og:title" content="Meta Tag Tutorial">
  <title>Meta Tag Guide</title>
</head>
```

---

## Notes

* In HTML5, the `charset` attribute is new; older HTML versions did not support it.
* The `scheme` attribute (from historical HTML) is no longer used.
* Overusing `http-equiv="refresh"` (especially with very short intervals) can harm usability and accessibility.
* The `keywords` meta tag is obsolete for SEO; major search engines no longer use it in ranking.
* Mis-ordering or placing `<meta charset>` too late may lead to misdecoded characters.
* When using Open Graph meta tags, use `property="og:…"` rather than `name` to align with standards.
* Agents will ignore unknown or unsupported meta names or properties silently.

---
