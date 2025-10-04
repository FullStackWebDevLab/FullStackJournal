# `<!DOCTYPE>`

## Key Topics

* [Definition and Purpose](#definition-and-purpose)
* [Syntax & Variants](#syntax--variants)
* [Attributes](#attributes)
* [Content Model](#content-model)
* [Context](#context)
* [Behavior and Semantics](#behavior-and-semantics)
* [Examples](#examples)
* [Notes](#notes)

---

## Definition and Purpose

The `<!DOCTYPE>` declaration is a directive placed at the very start of an HTML file that instructs the browser (or HTML parser) how to interpret the document structure. In modern HTML, its key purpose is to trigger **standards (or no-quirks) mode** rather than quirks mode.

Historically, in SGML-based HTML (e.g. HTML 4), `<!DOCTYPE>` referred to a Document Type Definition (DTD), defining grammar rules. In HTML5 and the HTML “living standard,” it no longer functions as a DTD reference.

---

## Syntax & Variants

* There is **no closing tag**; `<!DOCTYPE>` is a declaration, not an element.
* The simplest and recommended modern form is:

```html
<!DOCTYPE html>
```

* This is case-insensitive (e.g. `<!doctype html>` works)
* It must appear before the `<html>` start tag and before any other content (ideally as the very first line)

* Legacy / alternative forms include:

  * `<!DOCTYPE html SYSTEM "about:legacy-compat">` (allowed for backward compatibility)
  * Full DOCTYPEs referencing DTDs from HTML 4 / XHTML (Strict, Transitional, Frameset). For example:

    ```html
    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
        "http://www.w3.org/TR/html4/strict.dtd">
    ```

  These longer forms remain permitted in the HTML syntax, but are discouraged in new documents.

---

## Attributes

Because `<!DOCTYPE>` is a declaration (not an element), it does **not** accept attributes like `id`, `class`, `style`, etc.

The portions after `<!DOCTYPE html` in legacy forms (like PUBLIC or SYSTEM identifiers) are part of the declaration syntax, not attributes in the element-attribute sense.

---

## Content Model

* `<!DOCTYPE>` cannot contain child nodes, text, or nested tags.
* In the document’s abstract tree, it corresponds to a `DocumentType` node (in the DOM) separate from element content.

---

## Context

* It must appear before any other markup (except possibly a byte-order mark). Anything preceding it (comments, whitespace) can interfere with mode detection.
* A document should have **exactly one** DOCTYPE.
* Valid when the document is served with `text/html` or similar. In XHTML (served as XML, `application/xhtml+xml`), DOCTYPE rules differ (and may be optional).

---

## Behavior and Semantics

* **Rendering Mode**
  A correct DOCTYPE causes the browser to enter **standards mode**, ensuring consistent behavior of CSS layout, box models, and other rendering rules. Omitting or mis-forming it may push the browser into quirks mode or “almost standards” mode.

* **Visibility & Display**
  It has no visual presence, no layout, and no default CSS display. It is not part of content.

* **Semantics / Accessibility / SEO**
  It has no effect in semantic content, ARIA, or accessibility APIs. Its significance is purely for parsing and browser behavior.

* **Parser & Validation**
  Browsers do **not** fetch or enforce DTDs even if referenced; they largely ignore external DTD parts. In modern HTML, the DOCTYPE is retained only to guide rendering mode.

---

## Examples

**Minimal HTML5 document:**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Sample Page</title>
  </head>
  <body>
    <p>Hello, world!</p>
  </body>
</html>
```

**With legacy-compat string:**

```html
<!DOCTYPE html SYSTEM "about:legacy-compat">
<html>
  <head><title>Compat Example</title></head>
  <body><p>Test.</p></body>
</html>
```

**HTML 4.01 Strict (legacy example):**

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
  "http://www.w3.org/TR/html4/strict.dtd">
<html>
  <head><title>Legacy Strict</title></head>
  <body><p>Legacy content.</p></body>
</html>
```

---

## Notes

* While older DOCTYPEs referred to DTDs, modern HTML5 does **not** rely on a DTD. The DOCTYPE exists primarily for browser mode switching.
* Some legacy DOCTYPEs are still permitted for compatibility, but are discouraged in modern practice.
* Beware of whitespace, BOM, or comments before the DOCTYPE; they may trigger quirks mode in some browsers.
* Some older browsers had quirks in how they detect DOCTYPE (e.g. if an XML prolog preceded it).
* The DOCTYPE is mandatory in HTML syntax (for mode switching), though in XML syntax (XHTML) its use is more flexible.

---
