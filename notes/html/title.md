# `<title>`

## Definition and Purpose

The `<title>` HTML element defines the title of an HTML document. It represents the name of the document that is used by user agents (browsers) and external systems: browsers display it in the title bar or tab, search engines may display it as the page’s link headline, and bookmark/favorite features often default to it.

Its purpose is to provide a concise and meaningful identifier for the document; useful for users, accessibility tools, search engines, and navigation when the document is viewed outside its original page context (e.g. as a bookmark, search result, browser tab, etc.).

---

## Syntax and Variants

* Opening and closing tags: `<title>` ... `</title>`
* This is **not** a void/self-closing tag; both start and end tags are required.

**Content model**:

* Permitted content: **plain text only** (that is, character data). No nested HTML tags or markup inside `<title>`; any tags inside will be treated literally as text.
* It cannot contain inter-element whitespace only (i.e. the specification expects actual text, not empty or pure whitespace).

**Parent constraint**:

* The `<title>` element must appear within the `<head>` section of the HTML document.
* A document must not contain more than one `<title>` element.

---

## Attributes

* The `<title>` element supports only **global attributes** (e.g. `id`, `class`, `lang`, `dir`, `data-*`, `aria-*`, etc.); there are no additional special attributes for `<title>`.
* There are **no required attributes** beyond the tag itself; the element depends on its content (text) rather than attributes.

---

## Examples

### Simple/basic usage

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My First Web Page</title>
  </head>
  <body>
    <p>Hello, world!</p>
  </body>
</html>
```

### More descriptive title (good for usability / SEO)

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Understanding the HTML <title> Tag; Web Tutorial</title>
  </head>
  <body>
    <h1>Welcome to the tutorial</h1>
    <!-- Content ... -->
  </body>
</html>
```

### Context-aware / dynamic / state-reflecting title (e.g. error state)

```html
<!DOCTYPE html>
<html>
  <head>
    <title>2 errors (Checkout) My E-Commerce Site</title>
  </head>
  <body>
    <h1>Checkout Errors</h1>
    <p>Please correct the errors below and resubmit.</p>
    <!-- More content ... -->
  </body>
</html>
```

---
