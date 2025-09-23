# HTML Roadmap: Essentials

This roadmap presents the essential concepts required to begin working effectively with HTML. It focuses on the fundamental knowledge and practices needed to build well-structured, accessible, and meaningful web pages. Learners following this roadmap should concentrate on mastering these core topics first, while learning the relevant HTML tags as they progress. The essentials form the foundation upon which more advanced skills can later be developed, ensuring a strong starting point for front-end web development.

---

## Foundations

### What is HTML and how it works

* Purpose of HTML (structure, not styling or behavior)
* Differences between markup language vs programming language
* How browsers interpret HTML (parsing, DOM)

### Document structure and standards

* `<!DOCTYPE html>` and why it’s needed
* `<html>` element and `lang` attribute (specifying document language)
* `<head>` vs `<body>`: what belongs where
* Character encoding (`<meta charset>`), viewport settings, and other head metadata

### Core content structuring

* How to structure headings (`h1`-`h6`) and their hierarchy
* Paragraphs, line breaks, horizontal rules (`<p>`, `<br>`, `<hr>`)
* Grouping content: `<div>`, `<span>` (inline vs block elements)

### Links, Images, and Multimedia basics

* Hyperlinks: `<a>` tag, `href`, internal vs external links
* Images: `<img>`, `src`, `alt`, sizing, responsive images basics
* Embedding other media: audio, video, if needed: `<audio>`, `<video>`, using `controls`, etc.

---

## Intermediate Structure and Semantics

### Lists and Tables

* Ordered vs unordered vs description lists (`<ol>`, `<ul>`, `<li>`, `<dl>`)
* Tabular data: `<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>`, captions

### Forms and User Input

* Basic input controls: `<input>` types (text, email, number, etc.), `<textarea>`, `<button>`, `<select>`
* Associating labels (`<label>` + `for` / wrapping)
* Grouping fields (`<fieldset>` / `<legend>`)
* Basic attributes: `name`, `value`, placeholder etc.

### Semantic HTML and Landmarks

* Semantic tags: `<header>`, `<footer>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>` etc.
* Other semantic elements: `<figure>` / `<figcaption>`, `<time>`, `<mark>`, `<details>` / `<summary>` etc.
* Understanding how semantics help with accessibility, SEO, maintainability

---

## Validation, Accessibility, Best Practices

### Form Validation (HTML5 built-in)

* Attributes: `required`, `type`, `min`, `max`, `pattern`, `step`
* Built-in browser validation behavior; how to use validation attributes properly

### Accessibility (a11y) fundamentals

* Use of `alt` on images, `title` / aria attributes when necessary
* Keyboard navigation: `tabindex`, focus order, visible focus states
* Semantic markup so assistive technologies can understand page structure and content
* Proper labelling of forms, inputs, error messages

### SEO and Metadata

* Meta tags in `<head>` such as description, keywords, viewport, charset
* Open Graph / social sharing metadata (if relevant)
* Proper use of headings and semantic tags so search engines can interpret structure

---
