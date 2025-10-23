# Introduction

## CSS Role in Web Development

A fundamental principle in modern web development is the separation of content from presentation. This is achieved by using a markup language, such as HTML, to define the structure and content of a page, while a separate styling language is used to control its visual appearance. This separation offers significant advantages:

* **Maintainability:** The visual design can be updated across an entire site by modifying a single style file, without touching the underlying content.
* **Accessibility:** Content remains clean and semantically structured, making it more accessible to assistive technologies.
* **Flexibility:** Different styles can be applied to the same content for various outputs, such as desktop browsers, mobile devices, or print.

---

## Basic Syntax

The syntax is built upon a clear and consistent pattern. A complete style rule consists of two main parts:

* **Selector:** This identifies which element or elements in the document you wish to style.
* **Declaration Block:** This is a set of one or more declarations contained within curly braces `{}`.

Each declaration is a combination of a **property** and a **value**, separated by a colon and ending with a semicolon.
`property: value;`

**Example:**
```css
p {
  color: blue;
  font-size: 16px;
}
```

* `p` is the **selector** (targeting all paragraph elements).
* Everything between `{` and `}` is the **declaration block**.
* `color: blue;` is a **declaration**.
* `color` is a **property**.
* `blue` is the **value**.

---

## Determining Which Rules Apply

When multiple rules could apply to the same element, a defined set of rules determines which declaration will ultimately be displayed. This process involves three key concepts:

* **The Cascade:** This refers to the system that prioritizes and combines style rules from different sources (e.g., browser defaults, user styles, author styles). It resolves conflicts based on **origin**, **specificity**, and **order**.
* **Specificity:** This is a weighting system that determines which selector is more specific and therefore takes precedence. For example, a selector targeting an element by its ID (`#main-content`) is more specific and will override a selector targeting just the element type (`div`).
* **Inheritance:** Some property values applied to a parent element are inherited by its child elements. For instance, setting a `font-family` on the `<body>` element typically means all text elements inside the body will inherit that font, unless a more specific rule overrides it.

A rule "wins" and its declaration is applied based on a hierarchy of these factors, generally in this order: **Importance** (e.g., `!important`), **Specificity**, and finally, **Source Order** (where later rules in the code can override earlier, equally specific ones).

---
