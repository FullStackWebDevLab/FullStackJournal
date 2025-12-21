# `<button>`

## Definition and Purpose

The `<button>` HTML element defines an interactive button control. When activated by a user (via mouse click, keyboard, touch, or assistive technology) it can perform an action, such as submitting a form, resetting a form, opening or closing dialogs/popups, or triggering a scripted behavior.

It exists to provide a semantically correct, accessible, and flexible way to create clickable controls in web documents; more powerful and versatile than older alternatives (e.g. `<input type="button">`) because it allows arbitrary content (text, images, markup) inside.

---

## Syntax and Variants

* Opening and closing tags: `<button>` … `</button>` (both start and end tags are required).
* This is **not** a void / self-closing tag. It must wrap content.

**Content model**:

* Permitted content: **phrasing content** (i.e. text, inline elements, images, icons, etc.). You may include markup inside (e.g. `<img>`, `<span>`, `<strong>`, etc.), not just plain text.
* **Restrictions**: You must not nest interactive content (like another `<button>`, or another control like a form control) inside; interactive content inside a button is disallowed per spec.
* Parent context: `<button>` may be placed wherever phrasing content is allowed (e.g. inline contexts), often inside a `<form>` but not strictly required.

---

## Attributes

Besides the standard global attributes (`id`, `class`, `style`, `data-*`, `aria-*`, etc.), `<button>` defines a number of special attributes to control behavior and form association.

Important attributes include:

* `type` (optional); defines the button's behavior. Possible values:

  * `"submit"`; submits the form associated with the button (default when inside a form or form is implied).
  * `"reset"`; resets all form controls to their initial values (if associated with a form).
  * `"button"`; no default behavior; use for custom scripting or UI logic.

* `name`; name of the button, submitted with the form data when the button is used to submit.
* `value`; the value associated with the button’s `name` when submitting form data.
* Form-association attributes (useful when button is outside the form, or you want to customize submission behavior):

  * `form`; the `id` of a `<form>` element to associate this button with even if not nested inside it.
  * `formaction`; URL to submit to when this button is used (overrides the form’s `action` attribute). Effective only for submit buttons.
  * `formenctype`; how form data should be encoded (e.g. `multipart/form-data`, `application/x-www-form-urlencoded`, `text/plain`), overrides the form's `enctype`.
  * `formmethod`; HTTP method (`get`, `post`, or `dialog`) to use when submitting, overrides form’s `method`.
  * `formnovalidate`; when present, indicates that form validation should be skipped for this submission.
  * `formtarget`; defines the browsing context (e.g. `_self`, `_blank`) where the response should be displayed. Overrides form’s `target`.

* `disabled` (Boolean); when present, disables the button: it cannot be pressed or focused.
* `autofocus` (Boolean); when present, indicates the button should get input focus when the page loads. (But only one such element per document is allowed.)
Additionally, there are newer/less common attributes related to controlling dialogs/popovers:

* `command`, `commandfor`, `popovertarget`, `popovertargetaction`: used to link the button declaratively to a controlled element (e.g. a `<dialog>` or a popover), triggering show/close/toggle behaviors without custom JS.

As with other HTML elements, global attributes and event-handling attributes (e.g. `onclick`, `onfocus`, etc.) are also supported.

---

## Examples

### Basic button (no default behavior)

```html
<button type="button">Click me</button>
```

This button does nothing by default; you’d typically attach a JavaScript event listener to respond to its `click`.

### Submit button inside a form

```html
<form action="/login" method="post">
  <label>
    Username:
    <input type="text" name="username" />
  </label>
  <label>
    Password:
    <input type="password" name="password" />
  </label>
  <button type="submit" name="action" value="login">Log In</button>
</form>
```

When clicked, the button submits the form to `/login`. The button’s `name` and `value` are included in the submitted form data.

### Button with image/icon and custom behavior

```html
<button type="button" class="icon-button">
  <img src="/icons/like.svg" alt="" aria-hidden="true" />
  <span>Like</span>
</button>
```

This illustrates that `<button>` can contain not just text but images or inline markup; offering flexibility for UI components.

### Button associated with a form but placed outside it

```html
<form id="profileForm" action="/save-profile" method="post">
  <!-- form fields -->
  <input type="text" name="fullName" />
</form>

<footer>
  <button type="submit" form="profileForm">Save Profile</button>
</footer>
```

Here, the `<button>` sits outside the `<form>` but still submits it, thanks to the `form="profileForm"` attribute.

---
