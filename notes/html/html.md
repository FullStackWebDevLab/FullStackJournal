# `<html>`

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

The `<html>` element is the **root** element of an HTML document. It encloses all the content (except for the `<!DOCTYPE>` declaration) and establishes the document as HTML. It also provides a container for global attributes and acts as the top of the document’s element tree.  

In effect, it signals to user agents (browsers, parsers) that the document is HTML and serves as the starting point for parsing and rendering.

---

## Syntax & Variants  

+ Opening tag: `<html>`  
+ Closing tag: `</html>`  
+ It is not self-closing / void; it must have both opening and closing.  
+ There is one variant common in modern HTML with a language attribute:  

```html
<html lang="en">
  …
</html>
````

* In XHTML (or transitional HTML variants), you may see namespace declarations or XML syntax, e.g.:

```xml
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
```

But in HTML5 / modern HTML served as `text/html`, the simple `<html>` form is preferred.

---

## Attributes

The `<html>` tag can include attributes that define global settings for the document. The most important ones are:

* `lang`: Specifies the language of the document’s content. This helps search engines and screen readers interpret the text correctly. Example: `<html lang="en">`.
* `xmlns`: Defines an XML namespace. This is rarely used in standard HTML documents but may appear in XHTML contexts.
* `dir`: Indicates the direction of the text. Common values are `ltr` (left-to-right) and `rtl` (right-to-left). Example: `<html dir="rtl">`.

Additionally, `<html>` may accept **global attributes** (like `id`, `class`, `data-*`, `aria-*`, etc.).

The `lang` attribute is often considered best practice to improve accessibility and internationalization support.

---

## Content Model

* The `<html>` element’s content should consist of exactly two elements (in typical HTML documents): `<head>` and `<body>`, in that order.
* It may also include comments or processing instructions (though these are rare).
* You may place attributes, whitespace, or comments between the `<html>` tag and its child elements, but the canonical structure is:

```html
<html [attributes]>
  <head> … </head>
  <body> … </body>
</html>
```

There is no text content or direct child elements beyond those permitted (head/body) in standard HTML documents.

---

## Context

* `<html>` must be a direct child of `<!DOCTYPE>` (i.e. it follows the DOCTYPE declaration).
* There must be exactly one `<html>` element in a valid HTML document.
* It cannot be nested inside any other element or repeated.
* It is valid in documents served as HTML (e.g. `text/html`). In XML / XHTML (served as `application/xhtml+xml`), it behaves under XML rules but still serves as the root element.

---

## Behavior and Semantics

* **Rendering & Parsing**
  Browsers use the `<html>` element as the root node when building the DOM tree. Everything else (head, body, content) is parsed under it.
* **Default Display**
  It does not produce any visible output or CSS box of its own. Its display is effectively “invisible.”
* **Semantics / Accessibility / SEO**
  The `lang` attribute on `<html>` is used by screen readers, translation tools, and search engines to infer language context.
  There is no semantic content inherent to `<html>` beyond being the root container.
* **Global Scope**
  Because `<html>` is the root, any CSS or scripts targeting `html` often affect viewport-level properties (e.g. `html { height: 100%; }`).

---

## Examples

**Minimal, plain HTML:**

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Simple Page</title>
  </head>
  <body>
    <p>Hello from root!</p>
  </body>
</html>
```

**With language and directionality attributes:**

```html
<!DOCTYPE html>
<html lang="es" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Página en Español</title>
  </head>
  <body>
    <h1>Bienvenido</h1>
    <p>Este es un ejemplo.</p>
  </body>
</html>
```

**XHTML / XML style (for legacy / transitional contexts):**

```xml
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
  <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Legacy XHTML Page</title>
  </head>
  <body>
    <p>Well-formed XHTML example.</p>
  </body>
</html>
```

---

## Notes

* Although `lang` is optional per spec, omitting it reduces accessibility and localization support.
* Misordering (e.g. putting `<body>` before `<head>`) leads to unpredictable parsing and should be avoided.
* Some browsers insert implicit `<html>`, `<head>`, `<body>` tags when missing (error correction), but relying on that is bad practice.
* In CSS, selectors like `html { … }` target the root element; these can be useful for global styling (e.g. `font-size`, `background`, `height:100%`).
* In JavaScript, `document.documentElement` references the `<html>` element.

---
