# KeyboardEvent Interface Reference

## Overview

The KeyboardEvent interface describes user interaction with the keyboard, with each event representing a single interaction between the user and a key or combination of keys with modifiers. The event type (keydown, keypress, or keyup) identifies the nature of keyboard activity.

**Note:** KeyboardEvent events indicate low-level keyboard interactions without contextual meaning. For text input handling, the input event should be used instead.

**Inheritance Hierarchy:** Event → UIEvent → KeyboardEvent

## Constructor

### KeyboardEvent()

Creates a new KeyboardEvent object.

**Syntax:**
```javascript
new KeyboardEvent(type, options)
```

**Parameters:**
- `type` (string): Event name ("keydown", "keyup", or "keypress")
- `options` (object): Optional configuration including:
  - `key` (string, default ""): Sets KeyboardEvent.key value
  - `code` (string, default ""): Sets KeyboardEvent.code value
  - `location` (number, default 0): Sets KeyboardEvent.location value
  - `repeat` (boolean, default false): Sets KeyboardEvent.repeat value
  - `isComposing` (boolean, default false): Sets KeyboardEvent.isComposing value
  - `charCode` (number, default 0): Sets deprecated KeyboardEvent.charCode
  - `keyCode` (number, default 0): Sets deprecated KeyboardEvent.keyCode

## Constants

### Keyboard Location Constants

Constants identifying the keyboard region from which key events originate, accessed as KeyboardEvent.DOM_KEY_LOCATION_STANDARD and similar:

| Constant | Value | Description |
|----------|-------|-------------|
| `DOM_KEY_LOCATION_STANDARD` | 0x00 | Key not identified with a specific keyboard region; not on numeric keypad (except NumLock); not associated with left/right positioning. Examples: alphanumeric keys, NumLock, space bar |
| `DOM_KEY_LOCATION_LEFT` | 0x01 | Key located on left side of keyboard. Examples: left Control, left Command (Mac), left Shift |
| `DOM_KEY_LOCATION_RIGHT` | 0x02 | Key located on right side of keyboard. Examples: right Shift, right Alt |
| `DOM_KEY_LOCATION_NUMPAD` | 0x03 | Key located on numeric keypad or virtual key associated with numpad. NumLock excluded. Examples: numpad digits, numpad Enter, numpad decimal point |

## Instance Properties

All properties are read-only unless specified otherwise. This interface inherits properties from UIEvent and Event.

### Key Identification

**`key`** (string)
Returns the value of the pressed key, accounting for modifier key states (e.g., Shift) and keyboard locale/layout.

- Printable characters return their Unicode string representation (e.g., "a", " ", "B" with Shift)
- Control/special characters return predefined key values (e.g., "Enter", "ArrowUp", "Escape")
- Dead keys return "Dead"

**`code`** (string)
Returns the code value of the physical key represented by the event.

**Warning:** This property reflects physical key location independent of keyboard layout. Pressing the Y-position key on QWERTY returns "KeyY" regardless of whether the keyboard is QWERTZ (user expects "Z") or Dvorak (user expects "F").

Examples: "KeyA", "Enter", "ArrowUp", "ShiftLeft"

### Modifier Keys

**`altKey`** (boolean)
True if Alt (Option on macOS) was active during key event generation.

**`ctrlKey`** (boolean)
True if Ctrl was active during key event generation.

**`shiftKey`** (boolean)
True if Shift was active during key event generation.

**`metaKey`** (boolean)
True if Meta key (⌘ Command on Mac, Windows key on Windows) was active during key event generation.

### State Properties

**`repeat`** (boolean)
True if the key is held down and automatically repeating.

**`isComposing`** (boolean)
True if the event fires between compositionstart and compositionend.

**`location`** (number)
Numerical representation of key location on keyboard. See [Keyboard Location Constants](#keyboard-location-constants).

### Deprecated Properties

**`charCode`** (number) **DEPRECATED**
Unicode reference number of the key. Only used by obsolete keypress event. Use `key` instead.

**`keyCode`** (number) **DEPRECATED**
System-dependent numerical code identifying the unmodified pressed key value. Use `key` instead.

**`keyIdentifier`** (string) **NON-STANDARD, DEPRECATED**
Non-standard property deprecated in favor of `key`. Part of obsolete DOM Level 3 Events version.

## Instance Methods

This interface inherits methods from UIEvent and Event.

### getModifierState()

Returns boolean indicating if modifier key (Alt, Shift, Ctrl, Meta) was pressed during event creation.

**Syntax:**
```javascript
event.getModifierState(keyArg)
```

**Parameters:**
- `keyArg` (string): Modifier key identifier (e.g., "Control", "Shift", "Alt", "Meta", "CapsLock", "NumLock", "ScrollLock")

**Returns:** boolean

**Example:**
```javascript
document.addEventListener('keydown', (e) => {
  console.log(e.getModifierState('CapsLock')); // true if Caps Lock active
});
```

### initKeyboardEvent() **DEPRECATED**

Initializes KeyboardEvent object attributes. Deprecated; use KeyboardEvent() constructor instead.

## Event Types

Events based on KeyboardEvent type include keydown, keyup, and the deprecated keypress.

### keydown
Fired when a key is pressed.

### keyup
Fired when a key is released.

### keypress **DEPRECATED**
Fired when a character-producing key is pressed. Highly device-dependent and obsolete. Do not use.

## Event Sequence

For most keys, Gecko dispatches key events in this sequence: (1) keydown when first pressed, (2) keypress if not a modifier key, (3) keyup when released.

### Auto-repeat Behavior

When a key is held down:

1. `keydown`
2. `keypress`
3. `keydown` (repeat continues)
4. `keypress` (repeat continues)
5. ... (repeating)
6. `keyup` (on release)

The repeat property is set to true during auto-repeat events.

**Platform Variation:** On some GTK environments (e.g., Ubuntu 9.4), native key-up events are dispatched automatically during auto-repeat, resulting in interleaved keydown/keypress/keyup sequences.

### Special Cases

**Toggle Keys** (Caps Lock, Num Lock, Scroll Lock):
- Windows/Linux: Dispatch only keydown and keyup
- macOS: Caps Lock dispatches only keydown; Num Lock not supported on modern Macs

## Usage Examples

### Basic Event Handling

```javascript
document.addEventListener('keydown', (event) => {
  const keyName = event.key;
  
  if (keyName === 'Control') {
    return; // Don't alert for Control alone
  }
  
  if (event.ctrlKey) {
    alert(`Combination of ctrlKey + ${keyName}`);
  } else {
    alert(`Key pressed ${keyName}`);
  }
});

document.addEventListener('keyup', (event) => {
  if (event.key === 'Control') {
    alert('Control key was released');
  }
});
```

### Handling IME Composition

```javascript
element.addEventListener('keydown', (event) => {
  if (event.isComposing || event.keyCode === 229) {
    return; // Ignore events during IME composition
  }
  // Process key event
});
```

### Checking Modifier State

```javascript
document.addEventListener('keydown', (e) => {
  if (e.ctrlKey && e.key === 's') {
    e.preventDefault();
    console.log('Ctrl+S pressed - Save action');
  }
  
  console.log('Caps Lock:', e.getModifierState('CapsLock'));
  console.log('Num Lock:', e.getModifierState('NumLock'));
});
```

## Specification History

The KeyboardEvent interface specification underwent numerous draft versions under DOM Events Level 2 (dropped due to lack of consensus) and DOM Events Level 3. This resulted in non-standard initialization methods:
- `KeyboardEvent.initKeyEvent()` (Gecko browsers, DOM Events Level 2)
- `KeyboardEvent.initKeyboardEvent()` (others, DOM Events Level 3)

Both have been superseded by the modern KeyboardEvent() constructor.

## Browser Compatibility Notes

Firefox 65+ no longer fires keypress events for non-printable keys, with exceptions for Enter, Shift+Enter, and Ctrl+Enter (preserved for cross-browser compatibility).

**Firefox Meta Key:** In Firefox, the Windows key is reported as "OS" instead of "Meta" for certain keys (VK_LWIN, VK_RWIN on Windows; GDK_KEY_Super_L, GDK_KEY_Super_R, GDK_KEY_Hyper_L, GDK_KEY_Hyper_R on Linux).

## Specifications

- [UI Events - KeyboardEvent Interface](https://w3c.github.io/uievents/#interface-keyboardevent)
- [UI Events KeyboardEvent key Values](https://www.w3.org/TR/uievents-key/) (W3C Recommendation)
- [UI Events KeyboardEvent code Values](https://www.w3.org/TR/uievents-code/) (W3C Recommendation)

## Related Interfaces

- `Event` - Base event interface
- `UIEvent` - User interface event interface
- `InputEvent` - Text input event interface
- `CompositionEvent` - IME composition event interface

## Best Practices

1. **Prefer `key` over deprecated properties:** Use `key` instead of `keyCode` or `charCode` for identifying keys
2. **Use `code` for position-based detection:** When physical key location matters (e.g., game controls), use `code`
3. **Handle text input with `input` event:** For text entry, use `input` events rather than keyboard events
4. **Check `isComposing` for IME:** Always verify `isComposing` when handling text input in internationalized applications
5. **Avoid `keypress`:** The keypress event is deprecated and should not be used in new code
6. **Consider keyboard layout:** Remember that `key` respects user keyboard layout while `code` does not

---
