# `<title>`

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

The `<title>` element defines the document’s title or name. This title is used by user agents (browsers, bookmarks, history lists) to label the page. It is not part of the visible content of the document.

Authors should choose a title that meaningfully identifies the page even when viewed out of context (for instance, in browser tabs, bookmarks, search results).

---

## Syntax & Variants  

+ Opening tag: `<title>`  
+ Closing tag: `</title>`  
+ It is **not** a self-closing or void element; both opening and closing tags are required.
+ There is no variant or alternative form in standard HTML5.  
+ The element’s contents must be simple text (no nested markup).

---

## Attributes  

The `<title>` element does **not** have any special attributes of its own. It may accept **global attributes** (e.g. `id`, `class`, `data-*`, `aria-*`) like most other HTML elements.

---

## Content Model  

+ The content of `<title>` must be **text-only** (character data). It cannot contain elements, links, markup, or block structure.
+ Inter-element whitespace (i.e. leading or trailing spaces) is allowed, but only the textual content carries meaning.  
+ In the DOM, the `<title>` element holds a text node whose value is used as `document.title`.

---

## Context  

+ The `<title>` element must appear inside the `<head>` section of the document.
+ There must be **at most one** `<title>` element per document.
+ If a document lacks a valid `<title>`, user agents may still attempt to infer a title, but the document is less well-defined.

---

## Behavior and Semantics  

+ **Rendering / Visibility**  
  The content of `<title>` is not rendered as part of the document body. It is used only as metadata (for example, shown in browser tabs, address bar, bookmarks).

+ **Effect on Parsing / API / Document Title**  
  The text inside `<title>` becomes the document’s `title` property (accessible via `document.title` in JavaScript).
  Browsers use it to label the page in tabs or window titles.

+ **SEO, Accessibility, & User Context**  
  Search engines may use the `<title>` value in search result listings and ranking.
  Screen readers and assistive technologies use the title to announce or identify pages. The title also aids orientation in browser history and bookmarks.

+ **Fallback / Conflict Handling**  
  If multiple `<title>` elements exist, the first is generally considered authoritative, and others are ignored.
  If a `<title>` is placed outside `<head>`, user agents often relocate or interpret it as if inside `<head>` (for error correction).

---

## Examples  

**Basic document title:**

```html
<head>
  <title>My Sample Page</title>
</head>
```

**Descriptive title for SEO and context:**

```html
<head>
  <title>Introduction to Sorting Algorithms — Raymond’s Blog</title>
</head>
```

**Minimal (with only title):**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Homepage</title>
</head>
<body>
  <h1>Welcome!</h1>
</body>
</html>
```

---

## Notes

* The `<title>` element is **required** in valid HTML documents (per normative metadata content rules).
* Titles that are too long may be truncated in user interfaces (browser tabs, search results). Many tools recommend keeping titles under ~60 characters.
* The `<title>` is distinct from the `title` attribute on elements (which provides advisory information like tooltips).
* Avoid embedding markup (such as `<a>` or `<em>`) inside `<title>`; only plain text is allowed.
* When dynamically updating page title via JavaScript (e.g. `document.title = "New Title"`), ensure the text is meaningful and reflects the current context.
* For pages with multiple contexts (e.g. single-page apps), manage the title to reflect navigation state (for history, bookmarking, accessibility).

---
