# `<input>`

## Definition and Purpose

The `<input>` HTML element defines a control for user input in web forms (or more broadly, interactive controls). Depending on its configuration (especially the `type` attribute), it can generate a wide range of input controls; from text fields, checkboxes and radio buttons, to file uploads, buttons, date pickers, and more.

Its purpose is to enable documents to collect data from users in a standard, structured way. It's fundamental to building forms, user interfaces, and interactive webpages, making it one of the most versatile and frequently used HTML elements.

---

## Syntax and Variants

* Syntax:

  ```html
  <input ... >
  ```
* The `<input>` element is a **void (self-closing)** element; it does **not** contain content and does **not** have a closing tag.
* In HTML5, writing `<input>` or `<input />` are both valid (the slash is optional).
* There are **no alternative legacy forms** of `<input>` beyond perhaps historical XHTML syntax requiring self-closing slash; in modern HTML, standard syntax is used.

**Content model**:

* `<input>` must be empty; it does not accept child elements or text content.
* Because it's void, you cannot nest anything inside an `<input>` tag.

**Parent context**:

* Typically used inside a `<form>` element, though technically it can appear in any context that allows phrasing content (i.e. inline content).

---

## Attributes

The `<input>` element supports a mix of **global attributes** and many **specialized attributes** depending on context and the `type`. The key ones are:

* **`type`** (required / defaultable); defines what kind of input control is rendered. Common values: `text`, `password`, `checkbox`, `radio`, `submit`, `button`, `file`, `email`, `number`, `date`, `color`, `range`, `hidden`, `url`, etc.
* **`name`**; the name of the input, used when submitting form data to identify the field.
* **`value`**; the initial value (or submitted value for non-file inputs).
* **`placeholder`**; short hint displayed in the input when it is empty (commonly for text, email, url, etc.), to indicate expected format or content.
* **`checked`**; for inputs of type `checkbox` or `radio`; when present, makes the input pre-selected.
* **`disabled`**; when present, disables the input (user cannot interact with it).
* **`readonly`**; for text-accepting types (like `text`, `email`, `search`, etc.), indicates that the user cannot modify the value.
* **`required`**; indicates that the field must be filled (or checked) before the form can be submitted.
* **`accept`**; for file-upload (`type="file"`), a list of accepted file types/extensions.
* **`min`, `max`, `step`**; for numerical or date/time/range type inputs, define value constraints or allowed increments.
* **`form`**; associates the input with a specific `<form>` (useful if input sits outside the form tag).

In addition to these, the `<input>` element supports all **global HTML attributes** (`id`, `class`, `style`, `data-*`, `aria-*`, etc.) and standard **event-handling attributes** (e.g. `onchange`, `oninput`, etc.).

---

## Examples

### Basic text input

```html
<form action="/submit" method="post">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" placeholder="Enter your user name">
</form>
```

### Email input + required constraint + submit button

```html
<form action="/signup" method="post">
  <label for="email">Email address:</label>
  <input type="email" id="email" name="email" placeholder="you@example.com" required>
  
  <input type="submit" value="Sign Up">
</form>
```

### Checkbox group + radio + number input (mixed controls)

```html
<form action="/preferences" method="post">
  <!-- multiple selection -->
  <label>
    <input type="checkbox" name="subscribe" value="newsletter">
    Subscribe to newsletter
  </label>
  
  <!-- exclusive choice -->
  <p>Select gender:</p>
  <label><input type="radio" name="gender" value="male"> Male</label>
  <label><input type="radio" name="gender" value="female"> Female</label>
  
  <!-- numeric input with constraints -->
  <label for="age">Age (18-99):</label>
  <input type="number" id="age" name="age" min="18" max="99" step="1">
  
  <input type="submit" value="Save Preferences">
</form>
```

---
