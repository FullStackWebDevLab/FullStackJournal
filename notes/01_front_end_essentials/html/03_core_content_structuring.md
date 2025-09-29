# Core Content Structuring

When writing HTML, your goal is to organize content so that both humans and browsers can understand it. This involves headings, paragraphs, separators, and grouping elements.

---

## Headings (`<h1>`-`<h6>`)

Headings define the outline of your document, similar to chapter and section titles in a book.

* **`<h1>`**: The most important heading. Typically used once per page (like the main title).
* **`<h2>`**: Subsections under `<h1>`.
* **`<h3>`-`<h6>`**: Further nested subsections. Each level becomes less prominent.

**Example**:

```html
<h1>Main Page Title</h1>
<p>Introduction to the topic.</p>

<h2>Subsection 1</h2>
<p>Details about the first section.</p>

<h3>Sub-subsection</h3>
<p>Extra details under subsection 1.</p>
```

**Guideline**: Do not skip heading levels arbitrarily (e.g., going from `<h1>` to `<h4>`). Use them to build a logical hierarchy.

---

## Paragraphs, Line Breaks, and Horizontal Rules

### Paragraphs (`<p>`)

* Use `<p>` to enclose blocks of text.
* Browsers automatically add spacing before and after paragraphs.

```html
<p>This is a paragraph of text.</p>
<p>This is another paragraph.</p>
```

### Line Breaks (`<br>`)

* `<br>` inserts a single line break.
* Best for poems, addresses, or places where you truly need a break inside the same paragraph.

```html
<p>Line one<br>Line two<br>Line three</p>
```

### Horizontal Rule (`<hr>`)

* `<hr>` inserts a thematic break, often displayed as a horizontal line.
* Useful for dividing sections visually.

```html
<p>Introduction text here.</p>
<hr>
<p>Content after the horizontal rule.</p>
```

---

## Grouping Content: `<div>` and `<span>`

Sometimes, you need to group elements to style them or apply behavior (via CSS/JavaScript).

### `<div>` (block-level container)

* A generic container that behaves like a block.
* Often used to group larger sections of content.
* By default, it starts on a new line.

```html
<div>
  <h2>Article Section</h2>
  <p>This paragraph is grouped inside a div.</p>
</div>
```

### `<span>` (inline container)

* A generic container for inline text or elements.
* Does not start on a new line.
* Useful for styling small parts of text without breaking the flow.

```html
<p>This is <span style="color:blue;">important</span> text inside a sentence.</p>
```

**Rule of thumb**:

* Use `<div>` when grouping block elements (like paragraphs, lists, images).
* Use `<span>` when styling or marking part of inline content (like words inside a sentence).

---
