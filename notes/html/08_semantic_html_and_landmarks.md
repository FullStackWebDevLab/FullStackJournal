# Semantic HTML and Landmarks

Semantic HTML involves using HTML elements that convey meaning and structure, rather than just presentation. This practice is fundamental for accessibility, SEO, and maintainable code.

---

## Document Landmark Structure

Landmarks are specific semantic elements that define major sections of a page, allowing assistive technologies to navigate them efficiently.

* **Primary Landmarks:**
    * `<header>`: Represents introductory content, typically containing a logo, site name, and main navigation. It can be used at the document level or within sectioning elements.
    * `<main>`: Encapsulates the dominant, unique content of the document. **There must be only one `<main>` element per page** that is not nested within another sectioning element like `<article>` or `<aside>`. This is the most critical landmark for screen reader users.
    * `<footer>`: Contains information about its containing section, such as author, copyright, or related links.
    * `<nav>`: Defines a major block of navigation links. It should be reserved for primary navigation, not every group of links.
* **Supporting Landmarks:** `<section>`, `<article>`, and `<aside>` also create landmark regions, which are used to segment the `<main>` content or other areas.
* **Proper Nesting:** Landmarks should be nested logically. For example, a `<header>` and `<footer>` are often direct children of the `<body>`, while `<article>` elements reside within `<main>`.

---

## Content Sectioning Semantics

Choosing the right sectioning element is key to creating a meaningful document outline.

* **`<section>` vs. `<article>` vs. `<div>`:**
    * **`<section>`:** Groups thematically related content that typically deserves a heading. Use it to break a page or article into logical chapters or groups.
    * **`<article>`:** Represents a self-contained composition that is independently distributable or reusable (e.g., a forum post, a news article, a blog entry, a widget). If it would make sense in an RSS feed on its own, it's an `<article>`.
    * **`<div>`:** A neutral container with no semantic meaning. Use it purely for styling or scripting when no other semantic element is appropriate.
* **`<aside>`:** Represents content that is tangentially related to the content around it, often presented as a sidebar. When used within an `<article>`, it should be specifically related to that article.
* **Document Outlines:** Each sectioning element (`<article>`, `<section>`, `<aside>`, `<nav>`) starts a new section in the document outline. A heading (`<h1>`-`<h6>`) should be used within these elements to define their purpose.

---

## Text-Level Semantics

Inline semantic elements add meaning to phrases and words within a block of text.

* **Common Inline Elements:**
    * `<time>`: Represents a specific time or date. Use the `datetime` attribute to provide a machine-readable value, which is excellent for search engines and user agents.
        ```html
        <time datetime="2023-10-27">October 27, 2023</time>
        ```
    * `<mark>`: Highlights text for reference or notation purposes due to its relevance in the surrounding context. It is semantic, unlike a `<span>` with a yellow background.
    * `<address>`: Provides contact information for its nearest `<article>` or `<body>` ancestor. It should not be used for arbitrary postal addresses unless they are the page's contact info.

---

## Interactive Semantics

HTML provides native elements for common interactive patterns without requiring JavaScript.

* **`<details>` and `<summary>`:** These elements create a native disclosure widget where the content is visible only when the widget is toggled open.
    ```html
    <details>
      <summary>Frequently Asked Question</summary>
      <p>The answer to the question is revealed here.</p>
    </details>
    ```
* **Native Accordion Patterns:** This combination creates an accessible accordion pattern by default. The open/closed state is managed by the browser, including keyboard navigation and screen reader announcements.
* **Progressive Enhancement:** You can enhance these native elements with JavaScript for more complex behaviors (e.g., closing other sections when one opens), but the core functionality remains without any scripting.

---

## Semantic Benefits and Implementation

The advantages of using semantic HTML are extensive and impactful.

* **Screen Reader Navigation:** Screen readers can provide users with a list of landmarks, allowing them to jump directly to the `<main>` content, `<nav>`, or other regions, dramatically improving the experience for users with disabilities.
* **SEO Advantages:** Search engines use semantic markup to better understand the content's structure and meaning, which can positively influence ranking.
* **Code Maintainability:** Semantic code is more readable and predictable. Developers can quickly understand the structure, making the codebase easier to maintain and debug.
* **Future-Proofing:** As the web evolves, semantic markup ensures your content is structured in a way that user agents and future technologies can reliably interpret.
* **Graceful Degradation:** Semantic elements are treated as anonymous `<div>` elements in older browsers, so they will not break your layout. A simple CSS rule (`article, section, aside, nav, header, footer { display: block; }`) ensures they are styled correctly.

By consistently applying semantic HTML principles, you build a foundation for a more accessible, discoverable, and robust web experience.

---
