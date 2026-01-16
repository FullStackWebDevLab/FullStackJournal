# Event Object Reference

## Overview

The Event interface represents an event that takes place in the DOM. An event can be triggered by user actions (such as clicking a mouse button or pressing a key), by APIs to represent asynchronous task progress, or programmatically by scripts.

The Event object serves as the base interface for all events in the DOM. Many specific event types inherit from this base interface, adding their own specialized properties and methods.

## Creating Events

### Constructor

**Event(type, options)**

Creates a new Event object.

**Parameters:**
- `type` (string): The name of the event type
- `options` (optional object):
  - `bubbles` (boolean, default: false): Whether the event bubbles through the DOM
  - `cancelable` (boolean, default: false): Whether the event can be canceled
  - `composed` (boolean, default: false): Whether the event will trigger listeners outside of a shadow root

**Example:**
```javascript
const event = new Event('build', {
  bubbles: true,
  cancelable: true
});

element.dispatchEvent(event);
```

## Instance Properties

### bubbles (Read-only)

A boolean indicating whether the event bubbles up through the DOM tree.

**Type:** Boolean  
**Example:**
```javascript
element.addEventListener('click', (event) => {
  console.log(event.bubbles); // true for click events
});
```

### cancelable (Read-only)

A boolean indicating whether the event can be canceled, meaning its default action can be prevented.

**Type:** Boolean  
**Example:**
```javascript
element.addEventListener('click', (event) => {
  if (event.cancelable) {
    event.preventDefault();
  }
});
```

### composed (Read-only)

A boolean indicating whether the event can bubble across the boundary between the shadow DOM and the regular DOM.

**Type:** Boolean  
**Example:**
```javascript
customElement.addEventListener('click', (event) => {
  console.log(event.composed); // Check if event crosses shadow boundaries
});
```

### currentTarget (Read-only)

A reference to the currently registered target for the event, which is the object to which the event is currently slated to be sent. This value can change during event propagation through retargeting.

**Type:** EventTarget  
**Example:**
```javascript
parent.addEventListener('click', (event) => {
  console.log(event.currentTarget); // Always the parent element
  console.log(event.target); // The actual clicked element
});
```

### defaultPrevented (Read-only)

Indicates whether the call to event.preventDefault() canceled the event.

**Type:** Boolean  
**Example:**
```javascript
link.addEventListener('click', (event) => {
  event.preventDefault();
  console.log(event.defaultPrevented); // true
});
```

### eventPhase (Read-only)

Indicates which phase of the event flow is being processed. The possible values are:
- `Event.NONE` (0): No event is being processed
- `Event.CAPTURING_PHASE` (1): The event is being captured
- `Event.AT_TARGET` (2): The event has reached the target
- `Event.BUBBLING_PHASE` (3): The event is bubbling

**Type:** Number  
**Example:**
```javascript
element.addEventListener('click', (event) => {
  switch(event.eventPhase) {
    case Event.CAPTURING_PHASE:
      console.log('Capturing phase');
      break;
    case Event.AT_TARGET:
      console.log('At target');
      break;
    case Event.BUBBLING_PHASE:
      console.log('Bubbling phase');
      break;
  }
});
```

### isTrusted (Read-only)

Indicates whether the event was initiated by the browser (after a user click, for instance) or by a script.

**Type:** Boolean  
**Example:**
```javascript
button.addEventListener('click', (event) => {
  if (event.isTrusted) {
    console.log('Real user click');
  } else {
    console.log('Programmatic click');
  }
});
```

### target (Read-only)

A reference to the object to which the event was originally dispatched.

**Type:** EventTarget  
**Example:**
```javascript
parent.addEventListener('click', (event) => {
  console.log(event.target); // The element that was actually clicked
});
```

### timeStamp (Read-only)

The time (in milliseconds) at which the event was created. By specification, this value is time since epoch, but browsers' definitions vary.

**Type:** Number  
**Example:**
```javascript
element.addEventListener('click', (event) => {
  console.log(event.timeStamp); // e.g., 1234567890.123
});
```

### type (Read-only)

The name identifying the type of the event.

**Type:** String  
**Example:**
```javascript
element.addEventListener('click', (event) => {
  console.log(event.type); // "click"
});
```

## Instance Methods

### composedPath()

Returns an array of objects on which listeners will be invoked. This represents the event's path through the DOM. This does not include nodes in shadow trees if the shadow root was created with its ShadowRoot.mode closed.

**Syntax:** `event.composedPath()`  
**Returns:** Array of EventTarget objects  
**Example:**
```javascript
element.addEventListener('click', (event) => {
  const path = event.composedPath();
  console.log(path); // [element, parent, body, html, document, window]
});
```

### preventDefault()

Cancels the event if it is cancelable, preventing the default action associated with the event from occurring.

**Syntax:** `event.preventDefault()`  
**Returns:** None  
**Example:**
```javascript
link.addEventListener('click', (event) => {
  event.preventDefault(); // Prevent navigation
  console.log('Link click prevented');
});

form.addEventListener('submit', (event) => {
  event.preventDefault(); // Prevent form submission
  // Handle form with JavaScript instead
});
```

**Important Notes:**
- Only works if the event's `cancelable` property is `true`
- Does not stop event propagation
- Should be called early in the event handler

### stopPropagation()

Prevents further propagation of the current event in the capturing and bubbling phases. It does not prevent other event handlers on the same element from executing.

**Syntax:** `event.stopPropagation()`  
**Returns:** None  
**Example:**
```javascript
child.addEventListener('click', (event) => {
  event.stopPropagation();
  console.log('Child clicked');
});

parent.addEventListener('click', () => {
  console.log('Parent clicked'); // Will not execute
});
```

### stopImmediatePropagation()

Prevents all other listeners from being called, including listeners attached to the same element as well as those on elements that will be traversed later in the event flow.

**Syntax:** `event.stopImmediatePropagation()`  
**Returns:** None  
**Example:**
```javascript
button.addEventListener('click', (event) => {
  event.stopImmediatePropagation();
  console.log('First handler');
});

button.addEventListener('click', () => {
  console.log('Second handler'); // Will not execute
});
```

**Key Difference from stopPropagation():**
- `stopPropagation()`: Stops propagation to parent elements but allows other handlers on the same element to run
- `stopImmediatePropagation()`: Stops propagation to parent elements AND prevents other handlers on the same element from running

## Event Propagation

Events in the DOM follow a three-phase propagation model:

1. **Capturing Phase**: The event travels from the window down through ancestors to the target element
2. **Target Phase**: The event reaches the target element
3. **Bubbling Phase**: The event bubbles back up from the target through ancestors to the window

**Example:**
```javascript
// Capturing phase listener
parent.addEventListener('click', (event) => {
  console.log('Capturing phase');
}, true); // Note the 'true' parameter

// Bubbling phase listener (default)
parent.addEventListener('click', (event) => {
  console.log('Bubbling phase');
});
```

## Common Event Types

Events that inherit from the base Event interface include:

- **Mouse Events**: MouseEvent (click, dblclick, mousedown, mouseup, mousemove, etc.)
- **Keyboard Events**: KeyboardEvent (keydown, keyup, keypress)
- **Focus Events**: FocusEvent (focus, blur, focusin, focusout)
- **Input Events**: InputEvent (input, beforeinput)
- **Form Events**: SubmitEvent (submit)
- **UI Events**: UIEvent (load, resize, scroll)
- **Touch Events**: TouchEvent (touchstart, touchmove, touchend)
- **Animation Events**: AnimationEvent (animationstart, animationend, animationiteration)
- **Transition Events**: TransitionEvent (transitionend)
- **Drag Events**: DragEvent (drag, dragstart, drop)
- **Custom Events**: CustomEvent (user-defined events)

## Deprecated Properties and Methods

### cancelBubble (Deprecated)

A historical alias for `stopPropagation()`. Use `stopPropagation()` instead.

### returnValue (Deprecated)

A historical property for preventing default actions. Use `preventDefault()` instead.

### srcElement (Deprecated)

An alias for the `target` property. Use `target` instead.

### initEvent() (Deprecated)

Initializes the value of an Event that was created. Use the Event constructor instead.

## Browser Compatibility

The Event interface is widely supported across all modern browsers. The basic properties and methods have been available since the early days of JavaScript. However, some newer features like `composedPath()` and the `composed` property were introduced more recently for shadow DOM support.

## Best Practices

1. **Check cancelable before preventDefault()**: Always verify an event is cancelable before attempting to prevent its default action
2. **Be careful with stopPropagation()**: Stopping propagation can break event delegation patterns and other listeners
3. **Prefer stopImmediatePropagation() sparingly**: Only use when you specifically need to prevent other handlers on the same element
4. **Use event delegation**: Attach listeners to parent elements when possible for better performance
5. **Clean up listeners**: Remove event listeners when they are no longer needed to prevent memory leaks
6. **Use passive listeners**: For scroll and touch events, consider using passive listeners for better performance

## Related Interfaces

All specific event types inherit from the Event interface and add their own properties:

- `MouseEvent`: Adds clientX, clientY, button, buttons, etc.
- `KeyboardEvent`: Adds key, code, altKey, ctrlKey, shiftKey, etc.
- `TouchEvent`: Adds touches, targetTouches, changedTouches
- `CustomEvent`: Adds detail property for custom data

## Example: Complete Event Handling

```javascript
// Create and dispatch a custom event
const customEvent = new CustomEvent('userLoggedIn', {
  bubbles: true,
  cancelable: true,
  detail: { username: 'john_doe', timestamp: Date.now() }
});

// Handle the event
document.addEventListener('userLoggedIn', (event) => {
  console.log('Event type:', event.type);
  console.log('Event bubbles:', event.bubbles);
  console.log('Is trusted:', event.isTrusted);
  console.log('User data:', event.detail);
  console.log('Event path:', event.composedPath());
  
  // Prevent default if needed
  if (event.cancelable) {
    event.preventDefault();
  }
});

// Dispatch the event
document.dispatchEvent(customEvent);
```

---
