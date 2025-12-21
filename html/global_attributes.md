# HTML Global Attributes Reference

This document provides a comprehensive reference for HTML global attributes—attributes that can be applied to any HTML element.

## Core Identification and Classification

### `id`
Defines a unique identifier for an element within the entire document.
```html
<div id="main-content">Content here</div>
```
**Usage:**
- Must be unique across the entire document
- Used for linking via fragment identifiers (`#anchor`)
- Used for CSS targeting and JavaScript selection
- Case-sensitive

### `class`
Specifies one or more class names for an element (space-separated).
```html
<div class="container primary-section active">Content</div>
```
**Usage:**
- Multiple classes separated by spaces
- Used for CSS styling and JavaScript selection
- Can be applied to multiple elements
- Case-sensitive

### `style`
Contains inline CSS styling declarations for the element.
```html
<p style="color: blue; font-size: 16px;">Styled text</p>
```
**Usage:**
- Applies CSS directly to element
- Multiple declarations separated by semicolons
- Overrides external and internal stylesheets (high specificity)
- Recommended to use sparingly; prefer external CSS

## Content and Behavior

### `title`
Provides advisory information about the element (typically shown as tooltip).
```html
<abbr title="Hypertext Markup Language">HTML</abbr>
<button title="Click to submit form">Submit</button>
```
**Usage:**
- Displayed as tooltip on hover
- Enhances accessibility for unclear elements
- Not reliably accessible on touch devices

### `hidden`
Indicates the element is not yet or no longer relevant.
```html
<div hidden>This content is hidden</div>
<section hidden="until-found">Searchable hidden content</section>
```
**Values:**
- Boolean attribute (presence = true)
- `hidden` or `hidden="hidden"` — completely hidden
- `hidden="until-found"` — hidden but searchable (Experimental)

**Usage:**
- Browser won't render hidden elements
- Cannot override with CSS `display` for boolean form
- Should not hide legitimately viewable content

### `contenteditable`
Indicates whether the element content can be edited by the user.
```html
<div contenteditable="true">Editable content</div>
<p contenteditable="plaintext-only">Plain text only</p>
```
**Values:**
- `true` or empty string — element is editable
- `false` — element is not editable
- `plaintext-only` — raw text editable, formatting disabled

### `data-*`
Creates custom data attributes for storing private page/application data.
```html
<article data-columns="3" data-author="John Doe" data-category="tech">
  Article content
</article>
```
**Usage:**
- Attribute name must start with `data-`
- Followed by at least one character after hyphen
- Accessible via JavaScript `dataset` property
- All lowercase recommended
```javascript
const article = document.querySelector('article');
console.log(article.dataset.columns); // "3"
console.log(article.dataset.author);  // "John Doe"
```

## Internationalization and Language

### `lang`
Specifies the language of the element's content.
```html
<html lang="en">
<p lang="es">Hola mundo</p>
<blockquote lang="fr">Bonjour le monde</blockquote>
```
**Usage:**
- Should contain valid BCP 47 language tag
- Helps screen readers with pronunciation
- Aids search engines and translation tools
- Inherits to child elements unless overridden
- Common values: `en`, `en-US`, `es`, `fr`, `de`, `ja`, `zh`

### `dir`
Specifies the text directionality of the element's content.
```html
<p dir="ltr">Left to right text</p>
<p dir="rtl">نص من اليمين إلى اليسار</p>
<p dir="auto">Automatic direction detection</p>
```
**Values:**
- `ltr` — left to right (English, Spanish, French)
- `rtl` — right to left (Arabic, Hebrew)
- `auto` — browser determines based on content

### `translate`
Specifies whether element content should be translated when page is localized.
```html
<p translate="yes">This text should be translated</p>
<p translate="no">Brand Name™</p>
```
**Values:**
- `yes` or empty string — element will be translated
- `no` — element will not be translated

**Usage:**
- Useful for brand names, code snippets, proper nouns
- Helps translation tools identify non-translatable content

## Accessibility Attributes

### `tabindex`
Specifies whether element can receive focus and its sequential keyboard navigation order.
```html
<div tabindex="0">Focusable div (natural order)</div>
<div tabindex="1">Focused first</div>
<div tabindex="2">Focused second</div>
<div tabindex="-1">Programmatically focusable only</div>
```
**Values:**
- Negative value — element is focusable but not keyboard-navigable
- `0` — element is focusable in natural document order
- Positive value — element is focusable in specified order

**Best Practices:**
- Avoid positive values; disrupts natural navigation
- Use `0` for custom interactive elements
- Use `-1` for elements focused via JavaScript

### `role`
Defines semantic meaning of element for assistive technologies (ARIA).
```html
<div role="navigation">Navigation content</div>
<button role="tab">Tab button</button>
<ul role="menu">
  <li role="menuitem">Item 1</li>
</ul>
```
**Usage:**
- Part of WAI-ARIA specification
- Overrides default semantic meaning
- Common roles: `button`, `navigation`, `main`, `banner`, `complementary`

### `aria-*`
ARIA attributes that improve accessibility for assistive technologies.
```html
<button aria-label="Close dialog">×</button>
<div aria-hidden="true">Decorative content</div>
<input aria-required="true" aria-invalid="false">
```
**Common ARIA attributes:**
- `aria-label` — provides accessible label
- `aria-labelledby` — references element(s) that label this element
- `aria-describedby` — references element(s) that describe this element
- `aria-hidden` — removes element from accessibility tree
- `aria-live` — indicates content updates dynamically
- `aria-expanded` — indicates if element is expanded
- `aria-disabled` — indicates if element is disabled

## User Interaction

### `accesskey`
Specifies a keyboard shortcut to activate or focus an element.
```html
<button accesskey="s">Save</button>
<a href="#content" accesskey="c">Skip to content</a>
```
**Usage:**
- Activation varies by browser and OS:
  - Windows: Alt + key
  - Mac: Control + Option + key
  - Linux: Alt + key
- Use with caution; may conflict with browser/OS shortcuts
- Space-separated list of characters

### `draggable`
Specifies whether the element is draggable using Drag and Drop API.
```html
<div draggable="true">Drag me</div>
<img draggable="false" src="image.jpg">
```
**Values:**
- `true` — element may be dragged
- `false` — element may not be dragged
- Auto (default) — browser default behavior

### `spellcheck`
Specifies whether element should be checked for spelling errors.
```html
<textarea spellcheck="true">Check spelling here</textarea>
<input type="text" spellcheck="false">
```
**Values:**
- `true` or empty string — enable spell checking
- `false` — disable spell checking

**Usage:**
- Primarily for text input elements
- Behavior may vary by browser

## Input and Editing

### `autofocus`
Specifies that element should automatically receive focus when page loads.
```html
<input type="text" autofocus>
<button autofocus>Click me</button>
```
**Usage:**
- Boolean attribute
- Only one element per document should have autofocus
- For `<dialog>`, focuses when dialog is displayed
- Can be disruptive; use sparingly

### `inputmode`
Hints at the type of virtual keyboard to display for editable elements.
```html
<input inputmode="numeric" type="text">
<input inputmode="email" type="text">
<textarea inputmode="tel"></textarea>
```
**Values:**
- `none` — no virtual keyboard
- `text` — standard keyboard
- `decimal` — numeric with decimal point
- `numeric` — numeric keyboard
- `tel` — telephone keypad
- `search` — search-optimized keyboard
- `email` — email-optimized keyboard
- `url` — URL-optimized keyboard

### `enterkeyhint`
Hints at the action label for the enter key on virtual keyboards.
```html
<input enterkeyhint="search" type="search">
<textarea enterkeyhint="send"></textarea>
<input enterkeyhint="next" type="text">
```
**Values:**
- `enter` — standard enter
- `done` — finish and close keyboard
- `go` — navigate to target
- `next` — move to next field
- `previous` — move to previous field
- `search` — execute search
- `send` — send message/form

### `autocapitalize`
Controls whether text input is automatically capitalized.
```html
<input autocapitalize="sentences" type="text">
<textarea autocapitalize="words"></textarea>
```
**Values:**
- `none` or `off` — no capitalization
- `sentences` or `on` — capitalize first letter of sentences
- `words` — capitalize first letter of each word
- `characters` — capitalize all characters

### `autocorrect`
Controls whether input text is automatically corrected for spelling.
```html
<input autocorrect="on" type="text">
<textarea autocorrect="off"></textarea>
```
**Values:**
- `on` — enable autocorrection
- `off` — disable autocorrection

## Advanced Features

### `slot`
Assigns element to a named slot in shadow DOM.
```html
<custom-element>
  <span slot="header">Header content</span>
  <span slot="footer">Footer content</span>
</custom-element>
```
**Usage:**
- Used with Web Components
- Matches `<slot>` elements with corresponding `name` attribute
- Enables content distribution in shadow trees

### `part`
Exposes shadow DOM parts for external styling.
```html
<custom-element>
  <template shadowroot="open">
    <button part="button">Click me</button>
  </template>
</custom-element>

<style>
  custom-element::part(button) {
    background: blue;
  }
</style>
```
**Usage:**
- Space-separated list of part names
- Allows external styling of shadow DOM internals
- Used with `::part()` CSS pseudo-element

### `exportparts`
Transitively exports shadow parts from nested shadow trees.
```html
<outer-component exportparts="inner-button: button">
  <inner-component>
    <button part="inner-button">Button</button>
  </inner-component>
</outer-component>
```
**Usage:**
- Syntax: `inner-part-name: exported-name`
- Enables styling of nested component parts
- Advanced Web Components feature

### `is`
Specifies that standard HTML element should behave as customized built-in element.
```html
<button is="custom-button">Enhanced button</button>
<ul is="expanding-list">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
```
**Usage:**
- Extends existing HTML elements
- Must be registered with `customElements.define()`
- Alternative to autonomous custom elements

### `popover`
Designates element as a popover element.
```html
<div popover>Popover content</div>
<div popover="auto">Auto popover</div>
<div popover="manual">Manual popover</div>

<button popovertarget="my-popover">Toggle popover</button>
<div id="my-popover" popover>Popover content</div>
```
**Values:**
- `auto` — automatically manages open/close behavior
- `manual` — requires manual control

**Usage:**
- Hidden by default with `display: none`
- Controlled via `popovertarget` attribute or JavaScript API
- Modern alternative to dialog/modal patterns

### `inert`
Makes browser disregard user input events for the element.
```html
<div inert>
  <button>Cannot be clicked</button>
  <input type="text" placeholder="Cannot be focused">
</div>
```
**Usage:**
- Boolean attribute
- Element and descendants cannot receive focus
- Useful for disabling sections of UI
- Similar to `disabled` but for any element

### `nonce`
Cryptographic nonce for Content Security Policy (CSP).
```html
<script nonce="random123456">
  console.log('Inline script with nonce');
</script>
<style nonce="random123456">
  body { background: white; }
</style>
```
**Usage:**
- Used with CSP to allow specific inline scripts/styles
- Must be unpredictable and generated per page load
- Value should match CSP header nonce

### `anchor` (Non-standard, Experimental)
Associates positioned element with anchor element for CSS anchor positioning.
```html
<button id="anchor-btn">Anchor</button>
<div anchor="anchor-btn" style="position: absolute;">
  Positioned relative to button
</div>
```
**Usage:**
- Experimental feature
- Value is the `id` of the anchor element
- Used with CSS anchor positioning properties

### `virtualkeyboardpolicy` (Experimental)
Controls virtual keyboard behavior on editable elements.
```html
<input virtualkeyboardpolicy="auto" type="text">
<div contenteditable virtualkeyboardpolicy="manual">
  Editable content
</div>
```
**Values:**
- `auto` or empty string — show keyboard on focus/tap
- `manual` — decouples focus from keyboard state

### `writingsuggestions`
Controls browser-provided writing suggestions.
```html
<textarea writingsuggestions="true"></textarea>
<input type="text" writingsuggestions="false">
```
**Values:**
- `true` or empty string — enable writing suggestions
- `false` — disable writing suggestions

## Microdata Attributes

These attributes implement the HTML Microdata specification for structured data.

### `itemscope`
Creates an item and defines its scope.
```html
<div itemscope itemtype="https://schema.org/Person">
  <span itemprop="name">John Doe</span>
  <span itemprop="jobTitle">Software Engineer</span>
</div>
```

### `itemtype`
Specifies vocabulary URL that defines item properties.
```html
<article itemscope itemtype="https://schema.org/Article">
  <h1 itemprop="headline">Article Title</h1>
</article>
```

### `itemprop`
Adds a property to an item.
```html
<div itemscope itemtype="https://schema.org/Product">
  <span itemprop="name">Product Name</span>
  <span itemprop="price">$29.99</span>
</div>
```

### `itemid`
Provides unique global identifier for an item.
```html
<div itemscope itemtype="https://schema.org/Book" itemid="urn:isbn:978-0-123456-78-9">
  <span itemprop="title">Book Title</span>
</div>
```

### `itemref`
Associates properties from elsewhere in document with the item.
```html
<div itemscope itemtype="https://schema.org/Person" itemref="address">
  <span itemprop="name">Jane Doe</span>
</div>
<div id="address">
  <span itemprop="address">123 Main St</span>
</div>
```

## Deprecated/Legacy Attributes

### `xml:lang` (Deprecated)
Legacy XHTML language specification attribute.
```html
<p xml:lang="en">English text</p>
```
**Note:** Use `lang` attribute instead.

### `xml:base` (Deprecated)
Legacy XHTML base URI specification.
**Note:** Kept for compatibility only; avoid in new documents.

## Event Handler Attributes

Global event handler attributes can be applied to any element. They are discouraged in favor of JavaScript event listeners.

### Common Event Handlers
```html
<!-- Mouse Events -->
<div onclick="handleClick()">Click me</div>
<div ondblclick="handleDoubleClick()">Double click</div>
<div onmouseenter="handleEnter()">Hover me</div>
<div onmouseleave="handleLeave()">Stop hovering</div>

<!-- Keyboard Events -->
<input onkeydown="handleKeyDown(event)">
<input onkeyup="handleKeyUp(event)">
<input oninput="handleInput(event)">

<!-- Focus Events -->
<input onfocus="handleFocus()" onblur="handleBlur()">

<!-- Form Events -->
<form onsubmit="handleSubmit(event)">
  <input onchange="handleChange(event)">
</form>

<!-- Media Events -->
<video onplay="handlePlay()" onpause="handlePause()"></video>

<!-- Drag Events -->
<div ondragstart="handleDragStart(event)" draggable="true">Drag me</div>
<div ondrop="handleDrop(event)" ondragover="handleDragOver(event)">Drop here</div>
```

**Best Practice:** Use `addEventListener()` in JavaScript instead:
```javascript
element.addEventListener('click', handleClick);
element.addEventListener('input', handleInput);
```

## Usage Best Practices

1. **Use semantic HTML first** — don't rely on attributes to add meaning that should come from element choice
2. **Prefer external CSS** over inline `style` attributes for maintainability
3. **Use `class` over `id`** for styling; reserve `id` for JavaScript and unique anchoring
4. **Keep `id` values unique** across the entire document
5. **Use `data-*` attributes** for custom data; don't invent non-standard attributes
6. **Add `lang` attribute** to improve accessibility and SEO
7. **Use ARIA attributes** when semantic HTML is insufficient
8. **Avoid inline event handlers** — use JavaScript event listeners instead
9. **Test keyboard navigation** when using `tabindex`
10. **Use `hidden` appropriately** — don't hide content that should be visible to screen readers

## Accessibility Considerations

- Always provide `alt` text for images (element-specific, but crucial)
- Use `aria-label` or `aria-labelledby` for elements without visible labels
- Ensure `role` attributes match element behavior
- Test with screen readers to verify ARIA implementation
- Maintain logical `tabindex` order for keyboard navigation
- Use `lang` attribute to help screen readers pronounce content correctly
- Don't rely on `title` attribute for critical information (poor mobile support)

## Browser Compatibility Notes

- Most global attributes have excellent browser support
- Experimental attributes (marked above) may have limited support
- Always check [Can I Use](https://caniuse.com) for specific features
- Provide fallbacks for cutting-edge features
- Test across different browsers and assistive technologies
