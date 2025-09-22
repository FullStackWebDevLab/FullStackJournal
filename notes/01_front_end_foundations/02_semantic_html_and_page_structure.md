# Semantic HTML & Page Structure

Semantic HTML means using HTML elements that describe their meaning in a clear, standardized way; both for humans (developers, content authors) and machines (browsers, screen readers, search engines). It is not about “what it looks like” but “what it *means*.”

---

### Why Semantic HTML Matters

* **Accessibility**: Assistive technologies like screen readers rely on semantic markup to offer structure (e.g., headings, landmarks) so users with disabilities can navigate content.
* **SEO (Search Engine Optimization)**: Search engines use headings, metadata, and meaningful tags to understand content hierarchy and relevance. Appropriate tags give them stronger signals.
* **Maintainability & Readability**: Semantic tags make your markup more expressive and easier for future developers (or you months later) to understand. Pure `div`s everywhere become harder to manage.
* **Progressive Enhancement & Robustness**: Even if CSS or JavaScript fails or is slow, semantic HTML still offers a reliable base.

---

## Core Page Structure Elements and Use

Here are important HTML elements you should be familiar with, and when to use them:

* `<html lang="…">`: Declares language; helps with accessibility and internationalization.
* `<head>`: Contains metadata, titles, links to CSS, scripts, `meta` tags (charset, viewport, description etc.). Crucial for SEO and proper rendering.
* `<title>`: Page title shown in tabs, used by search engines.
* `<meta>` tags: e.g. `meta charset="UTF-8"`, `meta name="viewport" …`, `meta name="description" …`. These affect rendering, mobile friendliness, how page appears in search.

Then, in `<body>`:

* `<header>`: For introductory content, such as site title, logo, navigation.
* `<nav>`: For navigation links (menus, table of contents etc.).
* `<main>`: The primary content of the document; there should be exactly one `<main>` per page.
* `<section>`: A thematic grouping of content, usually with its own heading. Use when content is grouped under a distinct topic.
* `<article>`: Self-contained content that could stand alone (e.g. a blog post, forum post, news article).
* `<aside>`: For content related to the main content but separate (sidebars, pull quotes, ads).
* `<footer>`: For the bottom of page or section: copyright, contact info, legalese, navigation links etc.

Also:

* **Heading tags**: `<h1>` through `<h6>`. Use one `<h1>` per page ideally, followed by `<h2>`, `<h3>`, etc. Maintain hierarchical order.
* **Paragraphs**: `<p>` for blocks of text.
* **Lists**: `<ul>` (unordered), `<ol>` (ordered), `<li>` items. Helps structure items, aids readability and navigation.
* **Links**: `<a>` tag, with `href`, accessible labelling (text), consider `rel`, etc.
* **Images**: `<img>` with `src` and, importantly, `alt` attribute to give textual description for accessibility. Avoid empty or generic alt texts.

---

## Forms and Related Elements

Forms require special attention because they combine user interaction + semantic markup:

* `<form>`: The container with attributes like `action` (where data goes), `method` (GET vs POST).
* `<label>`: Descriptive text for input fields. Always associate via `for` with the `id` of the input. This helps clicking/tapping the label focuses the input, helpful for keyboard and screen reader users.
* `<input>`: Multiple types; text, email, number, password, etc. Using the correct `type` helps built-in validation, better UX, mobile keyboard suggestions.
* `<textarea>`: For multi-line text input.
* `<select>` / `<option>`: Dropdown / choices.
* `<fieldset>` / `<legend>`: Group logically related fields with a label; improves semantics and clarity. Particularly useful in long forms.

---

## Best Practices

1. **Use the right tag for the right job**; don’t use `<div>` or `<span>` if there is a semantic element that fits better. E.g., use `<nav>` for navigation instead of a styled `<div>`.
2. **Maintain heading hierarchy**; avoid skipping heading levels; it harms structure, accessibility, SEO.
3. **Provide descriptive `alt` texts** for images; avoid empty alt unless purely decorative.
4. **Label form inputs clearly**; required attributes; types correct; group fields logically.
5. **Meta data in `<head>`** should be precise and minimal but essential; charset, viewport (for mobile), description, possibly keywords or open‐graph etc.
6. **Avoid misusing layout elements** like tables for visual layout; use semantic containers + CSS for styling / layout.
7. **Test with assistive technologies** (screen readers, keyboard navigation) to ensure that semantics actually serve users.
8. **Validate HTML** (e.g. using W3C validator) to catch misuse of tags, missing attributes, etc.

---

## Example: Combined Semantic Markup Sample

Here’s a sample HTML skeleton showing many of these principles in action:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="An example of semantic HTML structure, forms, images, links, lists, and metadata.">
  <title>Semantic HTML Example Page</title>
</head>
<body>
  <header>
    <h1>My Website Title</h1>
    <nav>
      <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <article>
      <section>
        <h2>Introduction</h2>
        <p>This section introduces the main topic with some description.</p>
      </section>

      <section>
        <h2>Features</h2>
        <ul>
          <li>Feature one</li>
          <li>Feature two</li>
          <li>Feature three</li>
        </ul>
      </section>
    </article>

    <aside>
      <h2>Related Content</h2>
      <p>Some tangentially related information, like side notes or links.</p>
    </aside>

    <article>
      <h2>Contact Form</h2>
      <form action="/submit-contact" method="post">
        <fieldset>
          <legend>Personal Info</legend>

          <label for="name">Name:</label>
          <input type="text" id="name" name="name" required>

          <label for="email">Email:</label>
          <input type="email" id="email" name="email" required>
        </fieldset>

        <fieldset>
          <legend>Message</legend>
          <label for="message">Your Message:</label>
          <textarea id="message" name="message" rows="5" required></textarea>
        </fieldset>

        <button type="submit">Send Message</button>
      </form>
    </article>

    <section>
      <h2>Gallery</h2>
      <img src="photo1.jpg" alt="A description of photo1">
      <img src="photo2.jpg" alt="A description of photo2">
    </section>
  </main>

  <footer>
    <p>&copy; 2025 My Website. All rights reserved.</p>
  </footer>
</body>
</html>
```

---
