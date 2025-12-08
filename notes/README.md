# HTML

## What Is HTML

* HTML stands for **HyperText Markup Language**.
* It is not a programming language in the traditional sense (i.e. it does not execute logic or algorithms); rather, it is a **markup language**, used to describe and structure the content of web pages.
* The primary role of HTML is to provide the “skeleton” of a webpage. It defines **what** content appears (text, images, links, lists, etc.) and **how** that content is organized logically; not necessarily how it is styled or visually rendered (styling is normally handled by CSS).
* A valid HTML document can be saved with a `.html` extension and opened in any modern web browser.

---

## Basic HTML Document Structure

A minimal HTML document follows a well-defined structure. Here is the typical skeleton:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Your Page Title</title>
  </head>
  <body>
    <!-- Visible content goes here -->
  </body>
</html>
```

* `<!DOCTYPE html>` declares the document type and ensures the browser interprets the page as HTML5.
* The `<html>` element is the **root**; all other content resides within.
* The `<head>` section contains **metadata**: information about the document, such as character encoding, document title, links to stylesheets or scripts. Content here is not displayed directly on the page.
* The `<title>` inside `<head>` defines the title shown in the browser tab/window.
* The `<body>` section holds the content that the user sees: headings, paragraphs, images, links, etc.

---

## Elements, Tags, and Attributes

### Elements and Tags

* HTML content is composed of **elements**. Each element is typically represented by a pair of **tags**: an opening tag (e.g., `<p>`) and a closing tag (e.g., `</p>`). The content goes between these tags.
* Some elements may be **empty** (self-closing); they don’t wrap content. Example: `<br>` for a line break.

### Attributes

* Tags can include **attributes** that provide additional information or modify behavior. Attributes appear in the opening tag as name-value pairs (e.g., `<img src="photo.jpg" alt="Photo">`).
* Some attributes may be boolean (present without a value) depending on context (e.g., disabled in forms).

---

## Common and Fundamental HTML Elements

Below are some of the core elements you will frequently use when building pages.

### Headings

HTML supports six levels of headings: `<h1>` (most important) through `<h6>` (least important). They help you organize content hierarchically.

Example:

```html
<h1>Main Title</h1>
<h2>Sub-section</h2>
<h3>Minor Heading</h3>
```

### Paragraphs and Text

Paragraphs are created using the `<p>` tag. Browsers render each `<p>` as a block with space before and after.
Line breaks within paragraphs (without starting a new paragraph) can be achieved via `<br>` (empty tag).

### Text Emphasis and Semantics

To emphasise text or indicate importance/semantics:

* `<strong>`; typically renders bold, indicates strong importance.
* `<em>`; typically italics, indicates emphasis (like emphasis in spoken/written text).
  There are other semantic elements: `<code>`, `<pre>`, `<blockquote>`, `<sub>`, `<sup>`, etc. Useful for code snippets, quotations, subscript/superscript, etc.

### Lists

HTML supports two major list types:

* **Unordered list**; `<ul>` with `<li>` items; good for bullet-style lists.
* **Ordered list**; `<ol>` with `<li>` items; good for ordered/sequential lists.

Example:

```html
<ul>
  <li>First point</li>
  <li>Second point</li>
</ul>

<ol>
  <li>First step</li>
  <li>Second step</li>
</ol>
```

---

## Hyperlinks, Media, and Other Common Elements

### Hyperlinks

* Use the `<a>` (anchor) tag to create links (hyperlinks) pointing to other pages/sites. The `href` attribute defines the destination.
* Example:

  ```html
  <a href="https://example.com">Visit Example</a>
  ```

### Images and Media

* You can embed images via the `<img>` tag, using attributes like `src` (source URL) and `alt` (alternative text). While not covered in detail above, HTML supports embedding of images, video, audio, and other media (especially under HTML5).
* For structured media or more advanced layout, HTML5 enhances support beyond the basics (audio, video tags, canvas, etc.).

### Forms (Brief Overview)

HTML also allows creation of interactive forms to collect user input: text fields, checkboxes, radio buttons, dropdowns, textareas, submit buttons, etc.

Forms are essential for building dynamic or interactive web applications (for login pages, data submission, surveys, contact forms, etc.).

---

## Practical Example

Here is a minimal, but complete, HTML page you can type into a text editor (e.g. Notepad, VSCode), save as `index.html`, and view in a browser.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>My First HTML Page</title>
  </head>
  <body>
    <h1>Welcome to My Website</h1>
    <p>This is my first web page written in HTML.</p>

    <h2>About Me</h2>
    <p>I am learning HTML, and this is my introduction.</p>

    <h3>Things I like</h3>
    <ul>
      <li>Programming</li>
      <li>Web development</li>
      <li>Reading books</li>
    </ul>

    <p>Here is a link to <a href="https://www.w3.org/">W3C</a>, a standards-setting organization for the web.</p>
  </body>
</html>
```

Once you save and open in a browser, you should see a simple webpage with headings, text, a list, and a clickable link.

---
