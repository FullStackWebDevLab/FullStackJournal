# `MediaQueryList`

## Overview

`MediaQueryList` is a Web API interface that represents the result of evaluating a CSS media query in JavaScript. It allows developers to:

* Check whether a media query matches the current environment.
* Listen for changes when the media query result changes.
* Build responsive behavior using JavaScript.

A `MediaQueryList` object is created using `window.matchMedia()`.

---

## Creation of a MediaQueryList

```javascript
const mql = window.matchMedia("(max-width: 768px)");
```

`matchMedia()` returns a `MediaQueryList` object that contains the evaluation result of the specified media query.

---

## Interface Hierarchy

`MediaQueryList` inherits from `EventTarget`.
Therefore, it also supports generic event methods such as `addEventListener()` and `removeEventListener()`.

---

## Properties

### 1) `matches` (read-only)

**Type:** boolean

**Description:**
Indicates whether the document currently satisfies the media query.

* `true` → the media query matches.
* `false` → the media query does not match.

**Example:**

```javascript
if (mql.matches) {
  console.log("The media query matches.");
}
```

---

### 2) `media` (read-only)

**Type:** string

**Description:**
Returns the serialized media query string associated with the object.

**Example:**

```javascript
console.log(mql.media);
```

---

### 3) `onchange`

**Type:** function | null

**Description:**
Event handler property that is invoked when the media query result changes.

This property is an alternative to `addEventListener("change", ...)`.

**Example:**

```javascript
mql.onchange = (event) => {
  console.log(event.matches);
};
```

---

## Methods

### 1) `addEventListener(type, listener)`

**Inherited from:** EventTarget

**Description:**
Registers an event listener for the `change` event.

**Recommended approach** for modern code.

**Example:**

```javascript
mql.addEventListener("change", (event) => {
  console.log("Query changed:", event.matches);
});
```

---

### 2) `removeEventListener(type, listener)`

**Inherited from:** EventTarget

**Description:**
Removes a previously registered event listener.

**Example:**

```javascript
function handler(e) {
  console.log(e.matches);
}

mql.addEventListener("change", handler);
mql.removeEventListener("change", handler);
```

---

### 3) `addListener(callback)` (deprecated)

**Description:**
Registers a callback function to be invoked when the media query result changes.

* Kept only for backward compatibility.
* Should not be used in new code.

**Example:**

```javascript
mql.addListener((e) => {
  console.log(e.matches);
});
```

---

### 4) `removeListener(callback)` (deprecated)

**Description:**
Removes a callback registered with `addListener()`.

**Example:**

```javascript
function listener(e) {
  console.log(e.matches);
}

mql.addListener(listener);
mql.removeListener(listener);
```

---

## Events

### `change` Event

**Description:**
Triggered when the evaluation result of the media query changes.

For example, resizing the viewport across a breakpoint triggers this event.

**Event object type:** `MediaQueryListEvent`

**Event properties:**

* `matches`: boolean indicating whether the query matches.
* `media`: string representing the media query.

**Example:**

```javascript
mql.addEventListener("change", (event) => {
  if (event.matches) {
    console.log("Condition is true.");
  } else {
    console.log("Condition is false.");
  }
});
```

---

## Typical Use Cases

* Responsive design logic in JavaScript.
* Detecting screen size, orientation, or user preferences.
* Synchronizing UI behavior with CSS breakpoints.

`MediaQueryList` is especially useful because it allows event-driven detection of media query changes instead of manual polling.

---

## Key Best Practices

1. Prefer `addEventListener("change")` over `addListener()`.
2. Use `matches` for immediate state checks.
3. Combine CSS media queries with JavaScript logic for robust responsiveness.

---
