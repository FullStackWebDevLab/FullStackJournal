# HTMLElement Interface Reference

## Abstract

The HTMLElement interface represents all HTML elements within a document. It extends the Element interface and serves as the base interface for all specific HTML element types. This document provides comprehensive documentation of all properties and methods available through HTMLElement and its parent interfaces.

## Interface Hierarchy

```
EventTarget → Node → Element → HTMLElement
```

## Instance Properties

### Properties Defined on HTMLElement

#### `accessKey`
Type: `string`  
A string representing the keyboard shortcut assigned to the element for quick navigation.

#### `accessKeyLabel` (Read-only)
Type: `string`  
Returns the actual access key label rendered by the browser, which may differ from the accessKey value depending on platform conventions.

#### `anchorElement` (Read-only, Experimental, Non-standard)
Type: `Element | null`  
Returns a reference to the element's anchor element, or null if no anchor is present.

#### `attributeStyleMap` (Read-only)
Type: `StylePropertyMap`  
Provides a read-only representation of the element's inline style attribute as a StylePropertyMap object, offering programmatic access to CSS properties.

#### `autocapitalize`
Type: `string`  
Controls the automatic capitalization behavior for user text input. Valid values: `"none"`, `"off"`, `"on"`, `"characters"`, `"words"`, `"sentences"`.

#### `autocorrect`
Type: `boolean`  
Indicates whether automatic text correction should be applied to user input.

#### `autofocus`
Type: `boolean`  
Reflects the autofocus attribute, indicating whether the element should receive focus when the page loads or when a dialog/popover becomes visible.

#### `contentEditable`
Type: `string`  
Controls whether the element's content is editable. Value `"true"` enables editing, `"false"` disables it.

#### `dataset` (Read-only)
Type: `DOMStringMap`  
Provides read/write access to custom data attributes (data-*) on the element.

#### `dir`
Type: `string`  
Reflects the text directionality of the element. Possible values: `"ltr"`, `"rtl"`, `"auto"`.

#### `draggable`
Type: `boolean`  
Indicates whether the element can be dragged in drag-and-drop operations.

#### `editContext` (Experimental)
Type: `EditContext | null`  
Returns the EditContext associated with the element, or null if none exists.

#### `enterKeyHint`
Type: `string`  
Defines the action label or icon for the enter key on virtual keyboards.

#### `hidden`
Type: `string | boolean`  
Reflects the hidden attribute, controlling element visibility in the accessibility tree and rendering.

#### `inert`
Type: `boolean`  
Indicates whether the element should be ignored for user interaction, text searches, and text selection.

#### `innerText`
Type: `string`  
Represents the rendered text content of the element and its descendants. As a setter, replaces content and converts line breaks to `<br>` elements.

#### `inputMode`
Type: `string`  
Reflects the inputmode attribute, providing hints about the type of data expected for input.

#### `isContentEditable` (Read-only)
Type: `boolean`  
Returns true if the element's content is editable, false otherwise.

#### `lang`
Type: `string`  
Specifies the language of the element's content and attributes.

#### `nonce`
Type: `string`  
Returns the cryptographic nonce used by Content Security Policy to validate script and style execution.

#### `offsetHeight` (Read-only)
Type: `number`  
Returns the element's height including vertical padding and borders, relative to the layout.

#### `offsetLeft` (Read-only)
Type: `number`  
Returns the distance from the element's left border to its offsetParent's left border.

#### `offsetParent` (Read-only)
Type: `Element | null`  
Returns the element from which all offset calculations are computed.

#### `offsetTop` (Read-only)
Type: `number`  
Returns the distance from the element's top border to its offsetParent's top border.

#### `offsetWidth` (Read-only)
Type: `number`  
Returns the element's width including horizontal padding and borders, relative to the layout.

#### `outerText`
Type: `string`  
Similar to innerText but as a setter, replaces the entire element and its contents with the provided text.

#### `popover`
Type: `string`  
Controls the element's popover state via JavaScript. Valid values: `"auto"`, `"hint"`, `"manual"`. Can be used for feature detection.

#### `spellcheck`
Type: `boolean`  
Controls the spell-checking hint for the element's content.

#### `style`
Type: `CSSStyleDeclaration`  
Provides access to the element's inline style declarations, allowing programmatic manipulation of CSS properties.

#### `tabIndex`
Type: `number`  
Represents the element's position in the keyboard navigation tab order.

#### `title`
Type: `string`  
Specifies advisory information displayed as a tooltip when hovering over the element.

#### `translate`
Type: `boolean`  
Indicates whether the element's content should be translated when the page is localized.

#### `virtualKeyboardPolicy` (Experimental)
Type: `string`  
Specifies the on-screen virtual keyboard behavior for editable elements on devices without physical keyboards.

#### `writingSuggestions`
Type: `string`  
Indicates whether browser-provided writing suggestions should be enabled within the element's scope.

### Properties Inherited from Element

#### Identification and Structure

**`assignedSlot`** (Read-only): `HTMLSlotElement | null` - The slot element containing this node in shadow DOM.

**`attributes`** (Read-only): `NamedNodeMap` - Collection of the element's attributes.

**`childElementCount`** (Read-only): `number` - Number of child elements.

**`children`** (Read-only): `HTMLCollection` - Live collection of child elements.

**`classList`** (Read-only): `DOMTokenList` - List of class attributes.

**`className`**: `string` - The element's class attribute value.

**`firstElementChild`** (Read-only): `Element | null` - First child element.

**`lastElementChild`** (Read-only): `Element | null` - Last child element.

**`id`**: `string` - The element's unique identifier.

**`localName`** (Read-only): `string` - Local part of the qualified name.

**`namespaceURI`** (Read-only): `string | null` - Namespace URI of the element.

**`nextElementSibling`** (Read-only): `Element | null` - Next sibling element.

**`previousElementSibling`** (Read-only): `Element | null` - Previous sibling element.

**`prefix`** (Read-only): `string | null` - Namespace prefix.

**`tagName`** (Read-only): `string` - Tag name of the element.

#### Content and Display

**`innerHTML`**: `string` - HTML content within the element.

**`outerHTML`**: `string` - HTML markup of the element including itself.

**`part`**: `DOMTokenList` - Part identifier(s) for CSS shadow parts.

**`slot`**: `string` - Name of the shadow DOM slot the element occupies.

#### Layout and Dimensions

**`clientHeight`** (Read-only): `number` - Inner height excluding borders and scrollbars.

**`clientLeft`** (Read-only): `number` - Width of the left border.

**`clientTop`** (Read-only): `number` - Width of the top border.

**`clientWidth`** (Read-only): `number` - Inner width excluding borders and scrollbars.

**`currentCSSZoom`** (Read-only): `number` - Effective CSS zoom level (1.0 if not rendered).

**`scrollHeight`** (Read-only): `number` - Height of scrollable content.

**`scrollLeft`**: `number` - Horizontal scroll offset.

**`scrollTop`**: `number` - Vertical scroll offset.

**`scrollWidth`** (Read-only): `number` - Width of scrollable content.

**`scrollLeftMax`** (Read-only, Non-standard): `number` - Maximum horizontal scroll offset.

**`scrollTopMax`** (Read-only, Non-standard): `number` - Maximum vertical scroll offset.

#### Shadow DOM

**`shadowRoot`** (Read-only): `ShadowRoot | null` - Open shadow root hosted by the element.

#### Experimental Properties

**`elementTiming`** (Experimental): `string` - Marks element for PerformanceElementTiming API observation.

### ARIA Properties

HTMLElement inherits extensive ARIA properties from Element for accessibility. These properties reflect ARIA attributes and support assistive technologies.

#### State and Property Attributes

**`ariaAtomic`**: `string` - Controls whether assistive technologies announce all or partial changes.

**`ariaAutoComplete`**: `string` - Indicates autocomplete behavior for input elements.

**`ariaBusy`**: `string` - Indicates if an element is being modified.

**`ariaChecked`**: `string` - Current checked state of checkboxes and radio buttons.

**`ariaCurrent`**: `string` - Indicates the current item within a set.

**`ariaDisabled`**: `string` - Indicates the element is perceivable but not operable.

**`ariaExpanded`**: `string` - Indicates expanded/collapsed state of grouping elements.

**`ariaHasPopup`**: `string` - Indicates availability and type of popup.

**`ariaHidden`**: `string` - Controls visibility to accessibility APIs.

**`ariaInvalid`**: `string` - Indicates invalid input values.

**`ariaLabel`**: `string` - Defines accessible name for the element.

**`ariaLevel`**: `string` - Hierarchical level within a structure.

**`ariaLive`**: `string` - Indicates live region update behavior.

**`ariaModal`**: `string` - Indicates whether element is modal when displayed.

**`ariaMultiline`**: `string` - Indicates if text box accepts multiple lines.

**`ariaMultiSelectable`**: `string` - Allows multiple selections from descendants.

**`ariaOrientation`**: `string` - Element orientation (horizontal, vertical, undefined).

**`ariaPlaceholder`**: `string` - Short hint for data entry.

**`ariaPosInSet`**: `string` - Element's position in current set.

**`ariaPressed`**: `string` - Pressed state of toggle buttons.

**`ariaReadOnly`**: `string` - Indicates element is not editable but operable.

**`ariaRequired`**: `string` - Indicates required user input.

**`ariaSelected`**: `string` - Current selected state.

**`ariaSort`**: `string` - Sorting order in tables or grids.

**`ariaValueMax`**: `string` - Maximum value for range widgets.

**`ariaValueMin`**: `string` - Minimum value for range widgets.

**`ariaValueNow`**: `string` - Current value for range widgets.

**`ariaValueText`**: `string` - Human-readable value text.

#### Labeling and Description

**`ariaBrailleLabel`**: `string` - Braille label for the element.

**`ariaBrailleRoleDescription`**: `string` - Braille role description.

**`ariaDescription`**: `string` - Accessible description text.

**`ariaKeyShortcuts`**: `string` - Keyboard shortcuts for activation.

**`ariaRoleDescription`**: `string` - Human-readable role description.

#### Grid and Table Attributes

**`ariaColCount`**: `string` - Total columns in table/grid.

**`ariaColIndex`**: `string` - Column position in table/grid.

**`ariaColIndexText`**: `string` - Human-readable column index.

**`ariaColSpan`**: `string` - Columns spanned by cell.

**`ariaRowCount`**: `string` - Total rows in table/grid.

**`ariaRowIndex`**: `string` - Row position in table/grid.

**`ariaRowIndexText`**: `string` - Human-readable row index.

**`ariaRowSpan`**: `string` - Rows spanned by cell.

**`ariaSetSize`**: `string` - Total items in set.

#### Relationship Attributes (Non-standard)

**`ariaRelevant`**: `string` - Types of changes to announce in live regions.

#### Role Attribute

**`role`**: `string` - Semantic role of the element.

#### Element Reference Properties

These properties reflect element relationships specified by ID references:

**`ariaActiveDescendantElement`**: `Element | null` - Current active element in composite widgets.

**`ariaControlsElements`**: `Array<Element>` - Elements whose contents/presence are controlled.

**`ariaDescribedByElements`**: `Array<Element>` - Elements providing accessible description.

**`ariaDetailsElements`**: `Array<Element>` - Elements providing accessible details.

**`ariaErrorMessageElements`**: `Array<Element>` - Elements providing error messages.

**`ariaFlowToElements`**: `Array<Element>` - Next elements in alternate reading order.

**`ariaLabelledByElements`**: `Array<Element>` - Elements providing accessible name.

**`ariaOwnsElements`**: `Array<Element>` - Owned elements in accessibility tree.

## Instance Methods

### Methods Defined on HTMLElement

#### `attachInternals()`
Returns: `ElementInternals`  
Creates an ElementInternals object enabling the custom element to participate in HTML forms.

#### `blur()`
Returns: `void`  
Removes keyboard focus from the element.

#### `click()`
Returns: `void`  
Simulates a mouse click on the element.

#### `focus()`
Returns: `void`  
Sets keyboard focus to the element.

#### `hidePopover()`
Returns: `void`  
Hides a popover element by removing it from the top layer and applying `display: none`.

#### `showPopover()`
Returns: `void`  
Shows a popover element by adding it to the top layer and removing `display: none`.

#### `togglePopover()`
Returns: `void`  
Toggles a popover element between hidden and showing states.

### Methods Inherited from Element

#### DOM Tree Manipulation

**`after(...nodes)`**: Inserts nodes after this element in the parent's child list.

**`append(...nodes)`**: Inserts nodes at the end of this element's children.

**`before(...nodes)`**: Inserts nodes before this element in the parent's child list.

**`moveBefore(node, referenceNode)`**: Moves a node as a direct child before a reference node without re-insertion.

**`prepend(...nodes)`**: Inserts nodes at the beginning of this element's children.

**`remove()`**: Removes the element from its parent's child list.

**`replaceChildren(...nodes)`**: Replaces all children with new nodes.

**`replaceWith(...nodes)`**: Replaces the element with specified nodes.

#### Attribute Manipulation

**`getAttribute(name)`**: Returns the value of the specified attribute as a string.

**`getAttributeNames()`**: Returns an array of all attribute names.

**`getAttributeNode(name)`**: Returns the Attr node representation of the attribute.

**`getAttributeNodeNS(namespace, name)`**: Returns the Attr node for namespaced attributes.

**`getAttributeNS(namespace, name)`**: Returns the value of a namespaced attribute.

**`hasAttribute(name)`**: Returns boolean indicating if the attribute exists.

**`hasAttributeNS(namespace, name)`**: Returns boolean for namespaced attribute existence.

**`hasAttributes()`**: Returns boolean indicating if any attributes exist.

**`removeAttribute(name)`**: Removes the specified attribute.

**`removeAttributeNode(attr)`**: Removes the specified Attr node.

**`removeAttributeNS(namespace, name)`**: Removes a namespaced attribute.

**`setAttribute(name, value)`**: Sets the value of an attribute.

**`setAttributeNode(attr)`**: Adds or replaces an Attr node.

**`setAttributeNodeNS(attr)`**: Adds or replaces a namespaced Attr node.

**`setAttributeNS(namespace, name, value)`**: Sets a namespaced attribute value.

**`toggleAttribute(name, force?)`**: Toggles a boolean attribute's presence.

#### Selection and Traversal

**`closest(selectors)`**: Returns the closest ancestor matching the selector, or the element itself.

**`getElementsByClassName(names)`**: Returns live HTMLCollection of descendants with specified class names.

**`getElementsByTagName(name)`**: Returns live HTMLCollection of descendants with specified tag name.

**`getElementsByTagNameNS(namespace, name)`**: Returns live HTMLCollection of namespaced descendants.

**`matches(selectors)`**: Returns boolean indicating if element matches the selector.

**`querySelector(selectors)`**: Returns first descendant matching the selector.

**`querySelectorAll(selectors)`**: Returns NodeList of all descendants matching the selector.

#### Content Operations

**`getHTML(options?)`**: Returns DOM content as HTML string, optionally including shadow DOM.

**`setHTML(input)`** (Secure context, Experimental): Parses and sanitizes HTML, replacing element's subtree.

**`setHTMLUnsafe(html)`**: Parses HTML without sanitization, including declarative shadow roots.

**`insertAdjacentElement(position, element)`**: Inserts element at specified position relative to this element.

**`insertAdjacentHTML(position, html)`**: Parses HTML and inserts at specified position.

**`insertAdjacentText(position, text)`**: Inserts text node at specified position.

#### Layout and Geometry

**`checkVisibility(options?)`**: Returns whether element is expected to be visible based on configurable checks.

**`getBoundingClientRect()`**: Returns DOMRect describing element's size and position relative to viewport.

**`getClientRects()`**: Returns collection of rectangles for each line of text.

#### Scrolling

**`scroll(x, y)` or `scroll(options)`**: Scrolls to specified coordinates.

**`scrollBy(x, y)` or `scrollBy(options)`**: Scrolls by specified amount.

**`scrollIntoView(options?)`**: Scrolls until element is visible in viewport.

**`scrollIntoViewIfNeeded()` (Non-standard)**: Scrolls only if element is not already visible.

**`scrollTo(x, y)` or `scrollTo(options)`**: Scrolls to specified coordinates (alias for scroll).

#### Shadow DOM

**`attachShadow(options)`**: Attaches shadow DOM tree and returns ShadowRoot.

#### Animation

**`animate(keyframes, options)`**: Creates and runs an animation, returning Animation object.

**`getAnimations(options?)`**: Returns array of active Animation objects.

#### Styling

**`computedStyleMap()`**: Returns StylePropertyMapReadOnly of computed styles.

#### Fullscreen

**`requestFullscreen(options?)`**: Requests the browser to make element fullscreen.

#### Pointer Events

**`hasPointerCapture(pointerId)`**: Returns boolean indicating if element has pointer capture.

**`releasePointerCapture(pointerId)`**: Releases pointer capture for specified pointer.

**`setPointerCapture(pointerId)`**: Captures future pointer events.

**`requestPointerLock()`**: Requests pointer lock on the element.

#### Accessibility (Experimental, Non-standard)

**`ariaNotify(announcement, options?)`**: Specifies that text should be announced by screen readers.

#### Deprecated Methods

**`setCapture()`** (Non-standard, Deprecated): Redirects mouse events to element.

## Events

HTMLElement supports extensive event handling through inheritance. Events can be registered using `addEventListener()` or by assigning to `on[eventname]` properties.

### HTMLElement-Specific Events

**`change`**: Fired when value of input, select, or textarea is committed by user.

**`command`**: Fired on controlled elements via buttons with commandForElement and command values.

**`error`**: Fired when a resource fails to load.

**`load`**: Fired when a resource successfully loads.

### Drag and Drop Events

**`drag`**, **`dragend`**, **`dragenter`**, **`dragleave`**, **`dragover`**, **`dragstart`**, **`drop`**

### Interest Invoker Events (Experimental, Non-standard)

**`interest`**: Fired when interest is shown in an interest invoker target.

**`loseinterest`**: Fired when interest is lost in an interest invoker target.

### Toggle Events

**`beforetoggle`**: Fired before popover/dialog/details visibility changes.

**`toggle`**: Fired after popover/dialog/details visibility changes.

### Events Inherited from Element

#### Input Events

**`beforeinput`**: Fired before input element value modification.

**`input`**: Fired when element value changes from user action.

#### Focus Events

**`blur`**, **`focus`**, **`focusin`**, **`focusout`**

#### Keyboard Events

**`keydown`**, **`keyup`**  
**`keypress`** (Deprecated)

#### Mouse Events

**`auxclick`**, **`click`**, **`contextmenu`**, **`dblclick`**, **`mousedown`**, **`mouseenter`**, **`mouseleave`**, **`mousemove`**, **`mouseout`**, **`mouseover`**, **`mouseup`**

**`DOMActivate`** (Deprecated)  
**`DOMMouseScroll`** (Non-standard, Deprecated)  
**`mousewheel`** (Non-standard, Deprecated)  
**`MozMousePixelScroll`** (Non-standard, Deprecated)

#### Pointer Events

**`gotpointercapture`**, **`lostpointercapture`**, **`pointercancel`**, **`pointerdown`**, **`pointerenter`**, **`pointerleave`**, **`pointermove`**, **`pointerout`**, **`pointerover`**, **`pointerrawupdate`**, **`pointerup`**

#### Touch Events

**`touchcancel`**, **`touchend`**, **`touchmove`**, **`touchstart`**  
**`gesturechange`**, **`gestureend`**, **`gesturestart`** (Non-standard)

#### Wheel Events

**`wheel`**

#### Scroll Events

**`scroll`**, **`scrollend`**  
**`scrollsnapchange`**, **`scrollsnapchanging`** (Experimental)

#### Animation Events

**`animationcancel`**, **`animationend`**, **`animationiteration`**, **`animationstart`**

#### Transition Events

**`transitioncancel`**, **`transitionend`**, **`transitionrun`**, **`transitionstart`**

#### Clipboard Events

**`copy`**, **`cut`**, **`paste`**

#### Composition Events

**`compositionend`**, **`compositionstart`**, **`compositionupdate`**

#### Fullscreen Events

**`fullscreenchange`**, **`fullscreenerror`**

#### Visibility Events

**`beforematch`**: Fired when hidden-until-found content is about to be revealed.

**`contentvisibilityautostatechange`**: Fired when content-visibility: auto elements change relevance.

#### Security Events

**`securitypolicyviolation`**: Fired when Content Security Policy is violated.

#### Script Execution Events (Non-standard, Deprecated)

**`beforescriptexecute`**, **`afterscriptexecute`**

#### WebXR Events (Experimental)

**`beforexrselect`**: Fired before WebXR select events are dispatched.

#### WebKit-Specific Events (Non-standard)

**`webkitmouseforcechanged`**, **`webkitmouseforcedown`**, **`webkitmouseforceup`**, **`webkitmouseforcewillbegin`**

## Specifications

- DOM Standard: [https://dom.spec.whatwg.org/#interface-element](https://dom.spec.whatwg.org/#interface-element)
- HTML Living Standard: [https://html.spec.whatwg.org/multipage/dom.html#htmlelement](https://html.spec.whatwg.org/multipage/dom.html#htmlelement)
- CSSOM View Module
- Pointer Events
- Fullscreen API
- DOM Parsing and Serialization

## Browser Compatibility

HTMLElement and Element interfaces have been widely supported across all major browsers since July 2015. Some specific properties and methods have varying support levels:

- Experimental features may not be available in all browsers
- Non-standard features are typically browser-specific
- Deprecated features should be avoided in new code

Consult MDN Browser Compatibility tables for specific feature support details.

## Related Interfaces

- `Element` - Parent interface
- `Node` - Grandparent interface
- `EventTarget` - Root interface
- Specific element interfaces: `HTMLDivElement`, `HTMLInputElement`, `HTMLAnchorElement`, etc.
- `Document` - Container for elements
- `ShadowRoot` - Shadow DOM root
- `CSSStyleDeclaration` - Style manipulation
- `DOMTokenList` - Class and attribute list manipulation

---
