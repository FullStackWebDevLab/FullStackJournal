# CSS Selectors Comprehensive Reference

This document provides a systematic enumeration of CSS selector syntax, organized by selector type and specificity characteristics.

## Basic Selectors

### Universal Selector

+ `*`: Selects all elements in the document
  ```css
  * { margin: 0; }
  ```

### Type Selector (Element Selector)

+ `element`: Selects all elements of the specified type
  ```css
  p { color: blue; }
  div { display: block; }
  ```

### Class Selector

+ `.classname`: Selects all elements with the specified class attribute
  ```css
  .button { padding: 10px; }
  .header-title { font-size: 24px; }
  ```

### ID Selector

+ `#idname`: Selects the element with the specified id attribute (should be unique)
  ```css
  #main-header { background: navy; }
  #footer { margin-top: 50px; }
  ```

### Attribute Selectors

+ `[attr]`: Selects elements with the specified attribute
  ```css
  [disabled] { opacity: 0.5; }
  ```

+ `[attr="value"]`: Selects elements where attribute equals exact value
  ```css
  [type="text"] { border: 1px solid gray; }
  ```

+ `[attr~="value"]`: Selects elements where attribute contains value as whitespace-separated word
  ```css
  [class~="important"] { font-weight: bold; }
  ```

+ `[attr|="value"]`: Selects elements where attribute equals value or begins with value followed by hyphen
  ```css
  [lang|="en"] { direction: ltr; }
  ```

+ `[attr^="value"]`: Selects elements where attribute begins with specified value
  ```css
  [href^="https"] { color: green; }
  ```

+ `[attr$="value"]`: Selects elements where attribute ends with specified value
  ```css
  [href$=".pdf"] { background: url(pdf-icon.png); }
  ```

+ `[attr*="value"]`: Selects elements where attribute contains specified substring
  ```css
  [class*="btn"] { cursor: pointer; }
  ```

+ `[attr operator value i]`: Case-insensitive matching (add `i` flag)
  ```css
  [href*="example" i] { color: red; }
  ```

+ `[attr operator value s]`: Case-sensitive matching (add `s` flag)
  ```css
  [type="TEXT" s] { text-transform: uppercase; }
  ```

## Combinators

### Descendant Combinator

+ `A B`: Selects elements B that are descendants of element A (at any level)
  ```css
  div p { line-height: 1.6; }
  .container .item { margin: 10px; }
  ```

### Child Combinator

+ `A > B`: Selects elements B that are direct children of element A
  ```css
  ul > li { list-style: none; }
  .parent > .child { display: inline; }
  ```

### Adjacent Sibling Combinator

+ `A + B`: Selects element B that immediately follows element A (same parent)
  ```css
  h1 + p { font-size: 1.2em; }
  .item + .item { margin-top: 20px; }
  ```

### General Sibling Combinator

+ `A ~ B`: Selects all elements B that follow element A (same parent, not necessarily immediate)
  ```css
  h2 ~ p { color: gray; }
  .selected ~ .item { opacity: 0.7; }
  ```

### Column Combinator (Experimental)

+ `A || B`: Selects element B that belongs to the column represented by element A
  ```css
  col.selected || td { background: yellow; }
  ```

## Grouping Selector

### Selector List

+ `A, B, C`: Selects all elements matching A, B, or C
  ```css
  h1, h2, h3 { font-family: Arial; }
  .button, .link, .action { cursor: pointer; }
  ```

## Pseudo-classes

### Structural Pseudo-classes


#### Child-indexed

+ `:first-child`: Selects element that is the first child of its parent
  ```css
  li:first-child { font-weight: bold; }
  ```

+ `:last-child`: Selects element that is the last child of its parent
  ```css
  p:last-child { margin-bottom: 0; }
  ```

+ `:only-child`: Selects element that is the only child of its parent
  ```css
  div:only-child { text-align: center; }
  ```

+ `:nth-child(n)`: Selects element that is the nth child of its parent
  ```css
  li:nth-child(2) { color: blue; }
  li:nth-child(odd) { background: #f0f0f0; }
  li:nth-child(even) { background: white; }
  li:nth-child(3n) { font-weight: bold; }
  li:nth-child(3n+1) { color: red; }
  ```

+ `:nth-last-child(n)`: Selects element that is the nth child counting from the end
  ```css
  li:nth-last-child(2) { border-bottom: 2px solid; }
  ```

#### Type-indexed

+ `:first-of-type`: Selects first element of its type among siblings
  ```css
  p:first-of-type { font-size: 1.2em; }
  ```

+ `:last-of-type`: Selects last element of its type among siblings
  ```css
  img:last-of-type { margin-bottom: 0; }
  ```

+ `:only-of-type`: Selects element that is the only one of its type among siblings
  ```css
  article:only-of-type { width: 100%; }
  ```

+ `:nth-of-type(n)`: Selects nth element of its type among siblings
  ```css
  p:nth-of-type(2) { color: green; }
  div:nth-of-type(odd) { float: left; }
  ```

+ `:nth-last-of-type(n)`: Selects nth element of its type counting from the end
  ```css
  p:nth-last-of-type(1) { font-style: italic; }
  ```

### Content-based Pseudo-classes

+ `:empty`: Selects elements with no children (including text nodes)
  ```css
  div:empty { display: none; }
  ```

### User Action Pseudo-classes

+ `:hover`: Selects element when user hovers over it
  ```css
  a:hover { text-decoration: underline; }
  ```

+ `:active`: Selects element during activation (e.g., mouse click)
  ```css
  button:active { transform: scale(0.95); }
  ```

+ `:focus`: Selects element when it has input focus
  ```css
  input:focus { border-color: blue; }
  ```

+ `:focus-visible`: Selects element when focused via keyboard navigation
  ```css
  button:focus-visible { outline: 2px solid blue; }
  ```

+ `:focus-within`: Selects element when it or any descendant has focus
  ```css
  form:focus-within { box-shadow: 0 0 10px rgba(0,0,255,0.3); }
  ```

### Link Pseudo-classes

+ `:link`: Selects unvisited links
  ```css
  a:link { color: blue; }
  ```

+ `:visited`: Selects visited links
  ```css
  a:visited { color: purple; }
  ```

+ `:any-link`: Selects all links (both visited and unvisited)
  ```css
  a:any-link { text-decoration: none; }
  ```

+ `:target`: Selects element that is the target of the URL fragment
  ```css
  section:target { background: lightyellow; }
  ```

### Input Pseudo-classes

+ `:enabled`: Selects enabled form elements
  ```css
  input:enabled { background: white; }
  ```

+ `:disabled`: Selects disabled form elements
  ```css
  input:disabled { opacity: 0.5; }
  ```

+ `:read-only`: Selects elements that are not editable by user
  ```css
  input:read-only { background: #f5f5f5; }
  ```

+ `:read-write`: Selects elements that are editable by user
  ```css
  input:read-write { border: 1px solid #ccc; }
  ```

+ `:checked`: Selects checked radio buttons or checkboxes
  ```css
  input:checked { accent-color: green; }
  ```

+ `:indeterminate`: Selects form elements in indeterminate state
  ```css
  input:indeterminate { opacity: 0.5; }
  ```

+ `:default`: Selects default form element in a group
  ```css
  button:default { font-weight: bold; }
  ```

+ `:placeholder-shown`: Selects input element displaying placeholder text
  ```css
  input:placeholder-shown { font-style: italic; }
  ```

+ `:autofill`: Selects input element that has been autofilled
  ```css
  input:autofill { background: lightyellow; }
  ```

### Validation Pseudo-classes

+ `:valid`: Selects form elements that pass validation
  ```css
  input:valid { border-color: green; }
  ```

+ `:invalid`: Selects form elements that fail validation
  ```css
  input:invalid { border-color: red; }
  ```

+ `:in-range`: Selects input elements with value within specified range
  ```css
  input:in-range { border-color: green; }
  ```

+ `:out-of-range`: Selects input elements with value outside specified range
  ```css
  input:out-of-range { border-color: orange; }
  ```

+ `:required`: Selects form elements with required attribute
  ```css
  input:required { border-left: 3px solid red; }
  ```

+ `:optional`: Selects form elements without required attribute
  ```css
  input:optional { border-left: 3px solid gray; }
  ```

+ `:user-valid`: Selects valid elements after user interaction
  ```css
  input:user-valid { border-color: green; }
  ```

+ `:user-invalid`: Selects invalid elements after user interaction
  ```css
  input:user-invalid { border-color: red; }
  ```

### Tree-structural Pseudo-classes

+ `:root`: Selects document root element (typically `<html>`)
  ```css
  :root { --main-color: #06c; }
  ```

+ `:scope`: Represents reference point for selectors to match against
  ```css
  :scope > li { list-style: square; }
  ```

### Functional Pseudo-classes

+ `:is(selector-list)`: Selects elements matching any selector in the list (forgiving)
  ```css
  :is(h1, h2, h3) { line-height: 1.2; }
  :is(.button, .link):hover { opacity: 0.8; }
  ```

+ `:where(selector-list)`: Same as :is() but with zero specificity
  ```css
  :where(h1, h2, h3) { margin-top: 0; }
  ```

+ `:not(selector)`: Selects elements that do not match the selector
  ```css
  p:not(.intro) { font-size: 14px; }
  li:not(:last-child) { margin-bottom: 10px; }
  ```

+ `:has(selector)`: Selects elements that contain descendants matching selector (parent selector)
  ```css
  div:has(> img) { padding: 20px; }
  article:has(h2):has(p) { border: 1px solid; }
  ```

+ `:dir(direction)`: Selects elements based on text directionality
  ```css
  :dir(rtl) { text-align: right; }
  :dir(ltr) { text-align: left; }
  ```

+ `:lang(language)`: Selects elements based on language
  ```css
  :lang(en) { quotes: '"' '"'; }
  :lang(fr) { quotes: '«' '»'; }
  ```

### Display State Pseudo-classes

+ `:fullscreen`: Selects element displayed in fullscreen mode
  ```css
  :fullscreen { background: black; }
  ```

+ `:modal`: Selects element that excludes interaction with other elements
  ```css
  dialog:modal { max-width: 80vw; }
  ```

+ `:picture-in-picture`: Selects element in picture-in-picture mode
  ```css
  video:picture-in-picture { border: 2px solid blue; }
  ```

+ `:popover-open`: Selects popover element in showing state
  ```css
  [popover]:popover-open { opacity: 1; }
  ```

### Media Pseudo-classes

+ `:playing`: Selects media element currently playing
  ```css
  video:playing { border: 2px solid green; }
  ```

+ `:paused`: Selects media element that is paused
  ```css
  video:paused { opacity: 0.7; }
  ```

+ `:seeking`: Selects media element in seeking state
  ```css
  video:seeking { cursor: wait; }
  ```

+ `:buffering`: Selects media element that is buffering
  ```css
  video:buffering::after { content: 'Loading...'; }
  ```

+ `:stalled`: Selects media element with stalled playback
  ```css
  video:stalled { border: 2px solid orange; }
  ```

+ `:muted`: Selects muted media element
  ```css
  video:muted { opacity: 0.5; }
  ```

+ `:volume-locked`: Selects media element with locked volume
  ```css
  audio:volume-locked { pointer-events: none; }
  ```

### Element State Pseudo-classes

+ `:defined`: Selects custom elements that have been defined
  ```css
  my-component:defined { opacity: 1; }
  ```

+ `:open`: Selects open details or dialog elements
  ```css
  details:open { background: #f0f0f0; }
  ```

### Time-dimensional Pseudo-classes

+ `:current`: Selects element being displayed (WebVTT)
  ```css
  :current(p) { background: yellow; }
  ```

+ `:past`: Selects element that occurred in the past (WebVTT)
  ```css
  :past { opacity: 0.5; }
  ```

+ `:future`: Selects element that will occur in the future (WebVTT)
  ```css
  :future { opacity: 0.3; }
  ```

### Web Component Pseudo-classes

+ `:host`: Selects shadow host element
  ```css
  :host { display: block; }
  ```

+ `:host(selector)`: Selects shadow host if it matches selector
  ```css
  :host(.active) { border: 2px solid blue; }
  ```

+ `:host-context(selector)`: Selects shadow host if ancestor matches selector
  ```css
  :host-context(.dark-theme) { color: white; }
  ```

### Page Context Pseudo-classes

+ `:first`: Selects first page when printing
  ```css
  @page :first { margin-top: 3cm; }
  ```

+ `:left`: Selects left pages when printing
  ```css
  @page :left { margin-left: 3cm; }
  ```

+ `:right`: Selects right pages when printing
  ```css
  @page :right { margin-right: 3cm; }
  ```

+ `:blank`: Selects empty pages when printing
  ```css
  @page :blank { @top-center { content: none; } }
  ```

### Miscellaneous Pseudo-classes

+ `:local-link`: Selects links that target the current document
  ```css
  a:local-link { color: #06c; }
  ```

+ `:target-within`: Selects element if it or descendant is the URL target
  ```css
  section:target-within { background: lightyellow; }
  ```

## Pseudo-elements

Pseudo-elements create virtual elements that can be styled but don't exist in the DOM.

### Typographic Pseudo-elements

+ `::first-line`: Selects first formatted line of element
  ```css
  p::first-line { font-weight: bold; }
  ```

+ `::first-letter`: Selects first letter of element
  ```css
  p::first-letter { font-size: 2em; float: left; }
  ```

### Generated Content Pseudo-elements

+ `::before`: Inserts content before element's actual content
  ```css
  .icon::before { content: '→'; margin-right: 5px; }
  ```

+ `::after`: Inserts content after element's actual content
  ```css
  .external::after { content: ' ↗'; }
  ```

### Selection Pseudo-elements

+ `::selection`: Selects portion of element highlighted by user
  ```css
  ::selection { background: yellow; color: black; }
  ```

+ `::target-text`: Selects text scrolled to via text fragment
  ```css
  ::target-text { background: yellow; }
  ```

### Input Pseudo-elements

+ `::placeholder`: Selects placeholder text in input elements
  ```css
  input::placeholder { color: #999; font-style: italic; }
  ```

+ `::file-selector-button`: Selects button in file input elements
  ```css
  input[type="file"]::file-selector-button { 
    background: blue; 
    color: white; 
  }
  ```

### List Pseudo-elements

+ `::marker`: Selects marker box of list item
  ```css
  li::marker { color: red; font-weight: bold; }
  ```

### Dialog Pseudo-elements

+ `::backdrop`: Selects backdrop displayed behind modal elements
  ```css
  dialog::backdrop { background: rgba(0,0,0,0.5); }
  ```

### Details Pseudo-elements

+ `::details-content`: Selects content element of details element
  ```css
  details::details-content { padding: 10px; }
  ```

### Web Components Pseudo-elements

+ `::slotted(selector)`: Selects slotted elements in shadow DOM
  ```css
  ::slotted(p) { color: blue; }
  ```

+ `::part(name)`: Selects shadow part exposed for styling
  ```css
  custom-element::part(button) { background: blue; }
  ```

### Media Pseudo-elements

+ `::cue`: Selects WebVTT cues for styling
  ```css
  video::cue { color: yellow; }
  ```

+ `::cue(selector)`: Selects specific WebVTT cues
  ```css
  video::cue(v[voice="narrator"]) { color: blue; }
  ```

### Grammar and Spelling Pseudo-elements

+ `::spelling-error`: Selects text with spelling errors
  ```css
  ::spelling-error { text-decoration: red wavy underline; }
  ```

+ `::grammar-error`: Selects text with grammar errors
  ```css
  ::grammar-error { text-decoration: green wavy underline; }
  ```

### View Transition Pseudo-elements

+ `::view-transition`: Root of view transition overlay
  ```css
  ::view-transition { pointer-events: none; }
  ```

+ `::view-transition-group(name)`: Contains snapshot of single view transition element
  ```css
  ::view-transition-group(header) { animation-duration: 0.5s; }
  ```

+ `::view-transition-image-pair(name)`: Contains old and new snapshots
  ```css
  ::view-transition-image-pair(main) { isolation: isolate; }
  ```

+ `::view-transition-old(name)`: Represents old state snapshot
  ```css
  ::view-transition-old(card) { animation: fade-out 0.3s; }
  ```

+ `::view-transition-new(name)`: Represents new state snapshot
  ```css
  ::view-transition-new(card) { animation: fade-in 0.3s; }
  ```

## Specificity Reference

Specificity is calculated as a four-part value (a, b, c, d):

- **a**: Inline styles (1 if present, 0 otherwise)
- **b**: Number of ID selectors
- **c**: Number of class selectors, attribute selectors, and pseudo-classes
- **d**: Number of type selectors and pseudo-elements

### Specificity Examples

```css
* { }                   /* 0,0,0,0 */
li { }                  /* 0,0,0,1 */
ul li { }               /* 0,0,0,2 */
ul ol+li { }            /* 0,0,0,3 */
h1 + *[rel=up] { }      /* 0,0,1,1 */
ul ol li.active { }     /* 0,0,1,3 */
li.active.item { }      /* 0,0,2,1 */
#header { }             /* 0,1,0,0 */
#header .nav { }        /* 0,1,1,0 */
style="" attribute      /* 1,0,0,0 */
```

### Specificity Rules

1. Inline styles have highest specificity
2. ID selectors are more specific than classes
3. Classes are more specific than elements
4. `:where()` has zero specificity
5. `!important` overrides all specificity (avoid when possible)
6. When specificity is equal, last rule wins

## Best Practices

1. **Prefer classes over IDs** for styling (reserve IDs for JavaScript)
2. **Use semantic selectors** that describe content, not appearance
3. **Keep specificity low** to make styles easier to override
4. **Avoid universal selector** for performance-critical styles
5. **Use `:is()` and `:where()`** to simplify complex selectors
6. **Leverage attribute selectors** for form elements and states
7. **Use pseudo-classes** to handle interactive states
8. **Minimize descendant selectors** to improve performance
9. **Avoid `!important`** except for utility classes or overriding third-party CSS
10. **Group related selectors** using selector lists for maintainability