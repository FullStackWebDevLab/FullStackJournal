# HTML Roadmap

## 1. Introduction to HTML

Covered [here](./01_introduction.md)

+ HTML's purpose: defines content structure and semantics, not styling or behavior.
+ Markup language vs. programming language: uses tags to annotate content, not to create algorithms.

---

## 2. Document Structure

Covered [here](./02_document_structure.md)

+ Fundamental structure of an HTML document.
+ Essential tags: `<!DOCTYPE>`, `<html>`, `<head>`, and `<body>`.
+ Parent-child relationships and nesting rules.
+ Structural requirements: one `<head>` and one `<body>` per document.
+ Organization principles: semantic clarity and document validation.

---

## 3. Structuring Metadata in `<head>`

Covered [here](./03_head_metadata_structuring.md)

+ Essential `<head>` tags: `<title>`, `<meta>`, `<link>`, `<style>`, `<script>`, `<noscript>`, `<template>`, and `<base>`.
+ Critical declaration order: character encoding first, then viewport, then document title.
+ Resource loading sequence: CSS before JavaScript to prevent render blocking.
+ Document relationships: linking stylesheets, icons, and external resources.
+ Organization principles: minimizing render-blocking resources and strategic tag placement for performance.

---

## 4. Structuring Content in `<body>`

Covered [here](./04_body_content_structuring.md)

+ Key structural tags: headings (`<h1>`-`<h6>`), `<main>`, `<section>`, `<article>`, `<header>`, `<footer>`, `<nav>`, `<aside>`.
+ Document outline and hierarchy: logical heading structure and section nesting.
+ Content grouping and organization: block vs. inline elements and semantic coherence.
+ Layout structure: arrangement of major content sections (header, main, footer).
+ Accessibility and navigation: logical reading order and landmark regions for screen readers.

---

## 5. Text Formatting and Inline Elements

Covered [here](./05_text_formatting_and_inline_elements.md)

+ Inline semantic tags: `<strong>`, `<em>`, `<code>`, `<abbr>`, `<cite>`, `<q>`, `<sub>`, `<sup>`.
+ Block-level text tags: `<pre>` for code blocks and `<blockquote>` for quotations.
+ Text emphasis: semantic meaning (`<strong>`, `<em>`) vs. visual presentation.
+ Scientific and technical notation: using `<sub>` and `<sup>` for formulas and footnotes.
+ Semantic HTML principles: choosing elements for meaning, accessibility, and SEO.

---

## 6. Links, Images, and Multimedia

Covered [here](./06_links_images_and_multimedia.md)

+ Core media tags: `<a>`, `<img>`, `<audio>`, `<video>`, `<iframe>`, and `<picture>`.
+ Hyperlinks and navigation: internal/external links, URL paths, and accessibility.
+ Image content and optimization: responsive images, alt text, and performance.
+ Embedded media: audio/video with multiple sources, captions, and controls.
+ Media organization: using `<figure>`, `<figcaption>`, and semantic grouping.

---

## 7. Lists and Tables

Covered [here](./07_lists_and_tables.md)

+ List types: unordered (`<ul>`), ordered (`<ol>`), and definition (`<dl>`, `<dt>`, `<dd>`) lists.
+ Basic table structure: `<table>`, `<tr>`, `<td>`, and `<th>` for data grids.
+ Advanced table semantics: `<thead>`, `<tbody>`, `<tfoot>`, and `<caption>`.
+ Table accessibility: associating headers with data cells and screen reader navigation.
+ Appropriate use cases: choosing between lists and tables for different content types.

---

## 8. Semantic HTML and Landmarks

Covered [here](./08_semantic_html_and_landmarks.md)

+ Landmark elements: `<header>`, `<main>`, `<footer>`, `<nav>`, `<section>`, `<article>`, `<aside>`.
+ Text-level semantics: `<time>`, `<mark>`, and `<address>` for specific content types.
+ Interactive elements: `<details>` and `<summary>` for native accordions.
+ Content sectioning: proper use of `<section>` vs. `<article>` vs. `<div>`.
+ Semantic benefits: improved accessibility, SEO, and code maintainability.

---

## 9. Forms and User Input

Covered [here](./09_forms_and_user_input.md)

+ Core form tags: `<form>`, `<input>`, `<textarea>`, `<select>`, `<option>`, and `<button>`.
+ Form structure: grouping with `<fieldset>`, `<legend>`, and associating `<label>`.
+ Input types and controls: text, numerical, date, selection, and specialized inputs.
+ Attributes and validation: `required`, `pattern`, `min`, `max`, and `autocomplete`.
+ User experience: `<datalist>` for suggestions and proper button types (`submit`, `reset`).

---

## 10. Form Validation and User Feedback

Covered [here](./10_form_validation_and_user_feedback.md)

+ Validation attributes: `required`, `min`, `max`, `minlength`, `maxlength`, `pattern`, and `step`.
+ Input types with built-in validation: `email`, `url`, `number`, etc.
+ Browser behavior: native validation UI, preventing submission of invalid data.
+ User experience: real-time vs. on-submit validation and accessible error messages.
+ Advanced techniques: custom JavaScript validation and cross-field validation.

---

## 11. Interactive Elements

Covered [here](./11_interactive_elements.md)

+ Native modal dialogs using the `<dialog>` element and its methods.
+ Menu interfaces with the `<menu>` element for toolbars and context menus.
+ Progress indicators: `<progress>` for task completion and `<meter>` for scalar measurements.
+ Content editing via the `contenteditable` attribute.
+ User interaction patterns: form integration, event handling, and progressive enhancement.

---

## 12. Embedded Content

Covered [here](./12_embedded_content.md)

+ Graphics systems: `<canvas>` for bitmap drawing and `<svg>` for vector graphics.
+ Mathematical notation: `<math>` element for complex formulas (MathML).
+ External content: `<object>` and `<embed>` for plugin-based and legacy media.
+ Cross-platform compatibility: browser support variations and fallback strategies.
+ Performance: resource loading, memory management, and lazy loading.

---

## 13. Advanced Accessibility

Covered [here](./13_advanced_accessibility.md)

+ Keyboard navigation: `tabindex` values, logical focus order, and skip links.
+ ARIA attributes: landmark roles, live regions, form enhancements, and state indicators.
+ Screen reader optimization: semantic HTML, text alternatives, and heading structure.
+ Accessible interactive patterns: form errors, modal dialogs, and dynamic content updates.
+ Complex widget accessibility for tabs, accordions, and sliders.

---

## 14. SEO and Social Metadata

Covered [here](./14_seo_and_social_metadata.md)

+ Core SEO meta tags: `<title>`, `description`, `viewport`, and `robots`.
+ Social media metadata: Open Graph protocol and Twitter Cards.
+ Structured data: JSON-LD implementation using Schema.org vocabulary.
+ Content optimization: semantic HTML, heading hierarchy, and internal linking.
+ Technical SEO: canonical URLs, hreflang, sitemaps, and Core Web Vitals.

---
