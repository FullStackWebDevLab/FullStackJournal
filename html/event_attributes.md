# HTML Event Attributes Comprehensive Reference

This document provides a systematic enumeration of HTML event handler attributes, organized by event category. These attributes enable inline JavaScript execution in response to user interactions and system events.

**Note:** Event handler attributes are discouraged in modern web development. Prefer `addEventListener()` in JavaScript for better separation of concerns and maintainability.

## Mouse Events

### Click Events

#### `onclick`
Fires when element is clicked (mouse button pressed and released).
```html
<button onclick="alert('Clicked!')">Click me</button>
<div onclick="handleClick(event)">Clickable div</div>
```

#### `ondblclick`
Fires when element is double-clicked.
```html
<div ondblclick="alert('Double clicked!')">Double click me</div>
<img ondblclick="enlargeImage()" src="photo.jpg">
```

#### `onauxclick`
Fires when non-primary mouse button is clicked (middle or right button).
```html
<div onauxclick="handleAuxClick(event)">Try middle/right click</div>
```

#### `oncontextmenu`
Fires when context menu is triggered (typically right-click).
```html
<div oncontextmenu="showCustomMenu(event); return false;">
  Right-click for custom menu
</div>
```

### Mouse Movement Events

#### `onmouseover`
Fires when pointer enters element or its descendants.
```html
<div onmouseover="highlight(this)">Hover over me</div>
```

#### `onmouseout`
Fires when pointer leaves element or its descendants.
```html
<div onmouseout="unhighlight(this)">Mouse leaving</div>
```

#### `onmouseenter`
Fires when pointer enters element (does not bubble to descendants).
```html
<div onmouseenter="showTooltip()">Mouse entered</div>
```

#### `onmouseleave`
Fires when pointer leaves element (does not bubble to descendants).
```html
<div onmouseleave="hideTooltip()">Mouse left</div>
```

#### `onmousemove`
Fires when pointer moves while over element.
```html
<canvas onmousemove="trackPosition(event)"></canvas>
<div onmousemove="updateCoordinates(event)">Move mouse here</div>
```

### Mouse Button Events

#### `onmousedown`
Fires when mouse button is pressed down on element.
```html
<button onmousedown="startAction()">Press me</button>
<div onmousedown="handleMouseDown(event)">Mouse down</div>
```

#### `onmouseup`
Fires when mouse button is released over element.
```html
<button onmouseup="endAction()">Release me</button>
<div onmouseup="handleMouseUp(event)">Mouse up</div>
```

### Mouse Wheel Events

#### `onwheel`
Fires when mouse wheel is rotated over element.
```html
<div onwheel="handleWheel(event)">Scroll with wheel</div>
<canvas onwheel="zoom(event)"></canvas>
```

#### `onmousewheel` (Deprecated, Non-standard)
Legacy mouse wheel event (use `onwheel` instead).
```html
<!-- Don't use this -->
<div onmousewheel="handleScroll(event)">Legacy scroll</div>
```

## Keyboard Events

#### `onkeydown`
Fires when key is pressed down.
```html
<input onkeydown="handleKeyDown(event)" type="text">
<textarea onkeydown="checkShortcut(event)"></textarea>
```
**Common usage:**
```html
<input onkeydown="if(event.key === 'Enter') submitForm()">
```

#### `onkeyup`
Fires when key is released.
```html
<input onkeyup="validateInput(this.value)" type="text">
<textarea onkeyup="updateCharCount()"></textarea>
```

#### `onkeypress` (Deprecated)
Fires when key producing character value is pressed (deprecated; use `onkeydown` instead).
```html
<!-- Deprecated - avoid using -->
<input onkeypress="handleKeyPress(event)" type="text">
```

## Form Events

### Input Events

#### `oninput`
Fires when value of input, textarea, or contenteditable element changes.
```html
<input oninput="updatePreview(this.value)" type="text">
<textarea oninput="saveAutoDraft()"></textarea>
<div contenteditable oninput="handleContentChange()">Edit me</div>
```

#### `onchange`
Fires when value changes and element loses focus (for input/select/textarea).
```html
<input onchange="validateField(this)" type="text">
<select onchange="handleSelection(this.value)">
  <option>Option 1</option>
  <option>Option 2</option>
</select>
```

#### `onbeforeinput`
Fires before input value is modified.
```html
<input onbeforeinput="preprocessInput(event)" type="text">
<textarea onbeforeinput="filterContent(event)"></textarea>
```

### Selection Events

#### `onselect`
Fires when text is selected in input or textarea.
```html
<input onselect="handleSelection()" type="text">
<textarea onselect="showSelectionTools()"></textarea>
```

#### `onselectionchange`
Fires when text selection within element changes.
```html
<input onselectionchange="updateSelection()" type="text">
<textarea onselectionchange="trackCursor()"></textarea>
```

### Form Submission and Reset

#### `onsubmit`
Fires when form is submitted.
```html
<form onsubmit="return validateForm()">
  <input type="text" name="username">
  <button type="submit">Submit</button>
</form>
```
**Note:** Return `false` to prevent submission.

#### `onreset`
Fires when form is reset.
```html
<form onreset="confirmReset()">
  <input type="text" name="username">
  <button type="reset">Reset</button>
</form>
```

#### `oninvalid`
Fires when input element fails validation.
```html
<input oninvalid="showError(this)" type="email" required>
<input oninvalid="alert('Invalid input!')" pattern="[0-9]+" required>
```

#### `onformdata`
Fires when form data is constructed (during form submission).
```html
<form onformdata="modifyFormData(event)">
  <input name="field1">
  <button type="submit">Submit</button>
</form>
```

## Focus Events

#### `onfocus`
Fires when element receives focus.
```html
<input onfocus="highlightField(this)" type="text">
<button onfocus="showTooltip()">Focus me</button>
```

#### `onblur`
Fires when element loses focus.
```html
<input onblur="validateField(this)" type="text">
<textarea onblur="saveContent()"></textarea>
```

#### `onfocusin`
Fires when element is about to receive focus (bubbles).
```html
<div onfocusin="handleFocusIn(event)">
  <input type="text">
</div>
```

#### `onfocusout`
Fires when element is about to lose focus (bubbles).
```html
<div onfocusout="handleFocusOut(event)">
  <input type="text">
</div>
```

## Clipboard Events

#### `oncopy`
Fires when user copies content.
```html
<div oncopy="trackCopy(event)">Copy this text</div>
<p oncopy="alert('Content copied!')">Copyable content</p>
```

#### `oncut`
Fires when user cuts content.
```html
<input oncut="handleCut(event)" type="text">
<textarea oncut="trackEdit('cut')"></textarea>
```

#### `onpaste`
Fires when user pastes content.
```html
<input onpaste="processPaste(event)" type="text">
<textarea onpaste="validatePaste(event)"></textarea>
```

## Drag and Drop Events

### Source Element Events

#### `ondragstart`
Fires when user starts dragging element.
```html
<div draggable="true" ondragstart="handleDragStart(event)">
  Drag me
</div>
```

#### `ondrag`
Fires continuously while element is being dragged.
```html
<div draggable="true" ondrag="updatePosition(event)">
  Dragging...
</div>
```

#### `ondragend`
Fires when drag operation ends.
```html
<div draggable="true" ondragend="handleDragEnd(event)">
  Drag complete
</div>
```

### Target Element Events

#### `ondragenter`
Fires when dragged element enters valid drop target.
```html
<div ondragenter="highlightDropZone(event)">
  Drop zone
</div>
```

#### `ondragover`
Fires when dragged element is over valid drop target.
```html
<div ondragover="event.preventDefault()">
  Drop zone (must prevent default)
</div>
```

#### `ondragleave`
Fires when dragged element leaves valid drop target.
```html
<div ondragleave="unhighlightDropZone(event)">
  Drop zone
</div>
```

#### `ondrop`
Fires when element is dropped on valid drop target.
```html
<div ondrop="handleDrop(event); event.preventDefault()">
  Drop here
</div>
```

## Media Events

### Playback State Events

#### `onplay`
Fires when media playback starts.
```html
<video onplay="updatePlayButton()" src="video.mp4"></video>
<audio onplay="trackPlayback()" src="audio.mp3"></audio>
```

#### `onplaying`
Fires when media playback is ready to start after being paused or delayed.
```html
<video onplaying="hideLoadingSpinner()" src="video.mp4"></video>
```

#### `onpause`
Fires when media playback is paused.
```html
<video onpause="updatePauseButton()" src="video.mp4"></video>
<audio onpause="savePosition()" src="audio.mp3"></audio>
```

#### `onended`
Fires when media playback reaches the end.
```html
<video onended="playNext()" src="video.mp4"></video>
<audio onended="showReplayButton()" src="audio.mp3"></audio>
```

#### `onseeking`
Fires when user starts seeking to new position.
```html
<video onseeking="showSeekingIndicator()" src="video.mp4"></video>
```

#### `onseeked`
Fires when user finishes seeking to new position.
```html
<video onseeked="hideSeekingIndicator()" src="video.mp4"></video>
```

#### `onstalled`
Fires when browser tries to load media data but data is not available.
```html
<video onstalled="handleStall()" src="video.mp4"></video>
```

#### `onsuspend`
Fires when browser intentionally stops loading media data.
```html
<video onsuspend="handleSuspend()" src="video.mp4"></video>
```

#### `onwaiting`
Fires when playback stops because next frame is not available.
```html
<video onwaiting="showBuffering()" src="video.mp4"></video>
```

### Loading Events

#### `onloadstart`
Fires when browser starts loading media.
```html
<video onloadstart="showLoader()" src="video.mp4"></video>
```

#### `onloadeddata`
Fires when media data for current playback position is loaded.
```html
<video onloadeddata="enableControls()" src="video.mp4"></video>
```

#### `onloadedmetadata`
Fires when media metadata (duration, dimensions) is loaded.
```html
<video onloadedmetadata="displayDuration()" src="video.mp4"></video>
```

#### `oncanplay`
Fires when browser can start playing media (but might need to buffer).
```html
<video oncanplay="enablePlayButton()" src="video.mp4"></video>
```

#### `oncanplaythrough`
Fires when browser estimates it can play media without buffering.
```html
<video oncanplaythrough="autoPlay()" src="video.mp4"></video>
```

#### `onprogress`
Fires periodically as browser loads media data.
```html
<video onprogress="updateProgressBar()" src="video.mp4"></video>
```

#### `onemptied`
Fires when media becomes empty (e.g., when media is reloaded).
```html
<video onemptied="handleEmpty()" src="video.mp4"></video>
```

### Media Control Events

#### `onabort`
Fires when media loading is aborted.
```html
<video onabort="handleAbort()" src="video.mp4"></video>
```

#### `onerror`
Fires when error occurs while loading media.
```html
<video onerror="handleMediaError()" src="video.mp4"></video>
<img onerror="this.src='fallback.jpg'" src="image.jpg">
```

#### `ondurationchange`
Fires when duration attribute is updated.
```html
<video ondurationchange="updateDurationDisplay()" src="video.mp4"></video>
```

#### `ontimeupdate`
Fires when playback position changes.
```html
<video ontimeupdate="updateTimeline()" src="video.mp4"></video>
```

#### `onratechange`
Fires when playback rate changes.
```html
<video onratechange="updateSpeedDisplay()" src="video.mp4"></video>
```

#### `onvolumechange`
Fires when volume changes or is muted/unmuted.
```html
<video onvolumechange="updateVolumeUI()" src="video.mp4"></video>
```

## Touch Events

#### `ontouchstart`
Fires when touch point is placed on touch surface.
```html
<div ontouchstart="handleTouchStart(event)">Touch me</div>
```

#### `ontouchmove`
Fires when touch point moves along touch surface.
```html
<canvas ontouchmove="drawTouch(event)"></canvas>
```

#### `ontouchend`
Fires when touch point is removed from touch surface.
```html
<div ontouchend="handleTouchEnd(event)">Release touch</div>
```

#### `ontouchcancel`
Fires when touch event is interrupted.
```html
<div ontouchcancel="handleTouchCancel(event)">Touch cancelled</div>
```

## Pointer Events

#### `onpointerdown`
Fires when pointer becomes active.
```html
<div onpointerdown="handlePointerDown(event)">Press here</div>
```

#### `onpointermove`
Fires when pointer changes coordinates.
```html
<canvas onpointermove="drawWithPointer(event)"></canvas>
```

#### `onpointerup`
Fires when pointer is no longer active.
```html
<div onpointerup="handlePointerUp(event)">Release pointer</div>
```

#### `onpointercancel`
Fires when pointer event is cancelled.
```html
<div onpointercancel="handleCancel(event)">Cancelled</div>
```

#### `onpointerenter`
Fires when pointer enters element's hit test boundary.
```html
<div onpointerenter="highlightElement()">Pointer entered</div>
```

#### `onpointerleave`
Fires when pointer leaves element's hit test boundary.
```html
<div onpointerleave="unhighlightElement()">Pointer left</div>
```

#### `onpointerover`
Fires when pointer moves into element or descendant.
```html
<div onpointerover="showHoverState()">Pointer over</div>
```

#### `onpointerout`
Fires when pointer moves out of element or descendant.
```html
<div onpointerout="hideHoverState()">Pointer out</div>
```

#### `ongotpointercapture`
Fires when element receives pointer capture.
```html
<div ongotpointercapture="handleCapture()">Captured</div>
```

#### `onlostpointercapture`
Fires when pointer capture is released.
```html
<div onlostpointercapture="handleRelease()">Released</div>
```

#### `onpointerrawupdate`
Fires when pointer updates with highest frequency available.
```html
<canvas onpointerrawupdate="handleRawUpdate(event)"></canvas>
```

## Scroll Events

#### `onscroll`
Fires when element's scroll position changes.
```html
<div onscroll="handleScroll()" style="overflow: auto; height: 200px;">
  Scrollable content
</div>
<body onscroll="updateScrollPosition()">
```

#### `onscrollend`
Fires when scrolling operation completes.
```html
<div onscrollend="loadMoreContent()">Scroll to bottom</div>
```

#### `onscrollsnapchange` (Experimental)
Fires when scroll snap changes position.
```html
<div onscrollsnapchange="updateSnapIndicator()">Snap scroll</div>
```

#### `onscrollsnapchanging` (Experimental)
Fires when scroll snap is about to change position.
```html
<div onscrollsnapchanging="prepareNextSnap()">Snapping...</div>
```

## Window/Document Events

#### `onload`
Fires when element and all its resources finish loading.
```html
<body onload="initializeApp()">
<img onload="imageLoaded()" src="photo.jpg">
<iframe onload="frameLoaded()" src="page.html"></iframe>
```

#### `onresize`
Fires when element or window is resized.
```html
<body onresize="handleResize()">
<video onresize="adjustPlayerSize()" src="video.mp4"></video>
```

## Animation and Transition Events

### Animation Events

#### `onanimationstart`
Fires when CSS animation starts.
```html
<div onanimationstart="handleAnimStart()" class="animated">
  Animating element
</div>
```

#### `onanimationend`
Fires when CSS animation completes.
```html
<div onanimationend="handleAnimEnd()" class="animated">
  Animation complete
</div>
```

#### `onanimationiteration`
Fires when CSS animation iteration completes.
```html
<div onanimationiteration="countIteration()" class="animated">
  Looping animation
</div>
```

#### `onanimationcancel`
Fires when CSS animation is cancelled.
```html
<div onanimationcancel="handleAnimCancel()" class="animated">
  Cancelled animation
</div>
```

### Transition Events

#### `ontransitionstart`
Fires when CSS transition starts.
```html
<div ontransitionstart="handleTransStart()" class="transitioning">
  Transitioning element
</div>
```

#### `ontransitionend`
Fires when CSS transition completes.
```html
<div ontransitionend="handleTransEnd()" class="transitioning">
  Transition complete
</div>
```

#### `ontransitionrun`
Fires when CSS transition is created (before delay).
```html
<div ontransitionrun="handleTransRun()" class="transitioning">
  Transition queued
</div>
```

#### `ontransitioncancel`
Fires when CSS transition is cancelled.
```html
<div ontransitioncancel="handleTransCancel()" class="transitioning">
  Cancelled transition
</div>
```

## Dialog and Toggle Events

#### `onclose`
Fires when dialog is closed.
```html
<dialog onclose="handleDialogClose()">
  <p>Dialog content</p>
  <button onclick="this.closest('dialog').close()">Close</button>
</dialog>
```

#### `ontoggle`
Fires when details element opens or closes.
```html
<details ontoggle="handleToggle(this.open)">
  <summary>Click to expand</summary>
  <p>Hidden content</p>
</details>
```

#### `onbeforetoggle`
Fires before toggle state changes.
```html
<details onbeforetoggle="prepareToggle(event)">
  <summary>Expandable section</summary>
  <p>Content</p>
</details>
```

#### `oncancel`
Fires when dialog or input is cancelled (ESC key).
```html
<dialog oncancel="handleCancel()">
  Press ESC to cancel
</dialog>
<input oncancel="clearSearch()" type="search">
```

## Fullscreen Events

#### `onfullscreenchange`
Fires when element enters or exits fullscreen mode.
```html
<div onfullscreenchange="updateFullscreenUI()">
  <video src="video.mp4"></video>
</div>
```

#### `onfullscreenerror`
Fires when error occurs entering/exiting fullscreen.
```html
<div onfullscreenerror="handleFullscreenError()">
  Fullscreen container
</div>
```

## Content Visibility Events

#### `oncontentvisibilityautostatechange`
Fires when content-visibility: auto state changes.
```html
<div oncontentvisibilityautostatechange="handleVisibilityChange(event)"
     style="content-visibility: auto">
  Lazy-rendered content
</div>
```

#### `onbeforematch`
Fires when hidden content is revealed due to find-in-page.
```html
<div onbeforematch="prepareContent()" hidden="until-found">
  Searchable hidden content
</div>
```

## Canvas and Context Events

#### `oncontextlost`
Fires when canvas rendering context is lost.
```html
<canvas oncontextlost="handleContextLost(event)"></canvas>
```

#### `oncontextrestored`
Fires when canvas rendering context is restored.
```html
<canvas oncontextrestored="handleContextRestored(event)"></canvas>
```

## Form Control Events

#### `oncommand`
Fires when command is invoked via invoker element.
```html
<button commandfor="my-dialog" command="show-modal"
        oncommand="handleCommand()">
  Open Dialog
</button>
```

## WebVTT and Track Events

#### `oncuechange`
Fires when active text track cues change.
```html
<video>
  <track oncuechange="handleCueChange()" src="subtitles.vtt" kind="subtitles">
</video>
```

## Slot Events

#### `onslotchange`
Fires when slot's distributed nodes change.
```html
<slot onslotchange="handleSlotChange()"></slot>
```

## Security Events

#### `onsecuritypolicyviolation`
Fires when Content Security Policy is violated.
```html
<body onsecuritypolicyviolation="logViolation(event)">
```

## Selection Events

#### `onselectstart`
Fires when user starts new selection.
```html
<div onselectstart="handleSelectionStart(event)">
  Select text here
</div>
```

## Gesture Events (Non-standard, iOS Safari)

#### `ongesturestart` (Non-standard)
Fires when two or more fingers touch screen.
```html
<div ongesturestart="handleGestureStart(event)">
  Multi-touch gesture
</div>
```

#### `ongesturechange` (Non-standard)
Fires when fingers move during multi-touch gesture.
```html
<div ongesturechange="handleGestureChange(event)">
  Gesture in progress
</div>
```

#### `ongestureend` (Non-standard)
Fires when multi-touch gesture ends.
```html
<div ongestureend="handleGestureEnd(event)">
  Gesture complete
</div>
```

## Force Touch Events (Non-standard, macOS Safari)

#### `onwebkitmouseforcewillbegin` (Non-standard)
Fires before force touch begins.
```html
<div onwebkitmouseforcewillbegin="prepareForceTouch()">
  Force touch element
</div>
```

#### `onwebkitmouseforcedown` (Non-standard)
Fires when force touch begins.
```html
<div onwebkitmouseforcedown="handleForceDown(event)">
  Force press down
</div>
```

#### `onwebkitmouseforceup` (Non-standard)
Fires when force touch ends.
```html
<div onwebkitmouseforceup="handleForceUp(event)">
  Force press up
</div>
```

#### `onwebkitmouseforcechanged` (Non-standard)
Fires when force touch pressure changes.
```html
<div onwebkitmouseforcechanged="handleForceChange(event)">
  Pressure sensitive
</div>
```

## Event Handler Best Practices

### Why Avoid Inline Event Handlers?

1. **Separation of Concerns** — HTML should define structure, not behavior
2. **Maintainability** — JavaScript in one place is easier to update
3. **Reusability** — Event listeners can be attached to multiple elements
4. **Security** — Inline handlers are blocked by strict Content Security Policy
5. **Debugging** — Easier to debug code in JavaScript files
6. **Multiple Listeners** — Can attach multiple handlers to same event
7. **Testing** — Easier to unit test separate JavaScript functions

### Modern Alternative: addEventListener()

```javascript
// Instead of:
<button onclick="handleClick()">Click</button>

// Use:
<button id="myButton">Click</button>
<script>
  document.getElementById('myButton').addEventListener('click', handleClick);
</script>
```

### Advantages of addEventListener()

```javascript
// Multiple handlers
element.addEventListener('click', handler1);
element.addEventListener('click', handler2);

// Event options
element.addEventListener('scroll', handler, {
  passive: true,    // Better scroll performance
  once: true,       // Remove after first trigger
  capture: true     // Capture phase instead of bubble
});

// Easy removal
element.removeEventListener('click', handler);

// Arrow functions
element.addEventListener('click', (event) => {
  console.log('Clicked!', event.target);
});
```

## Event Object Properties

When using event handlers, the event object provides useful information:

```javascript
function handleEvent(event) {
  event.type          // Event type: 'click', 'keydown', etc.
  event.target        // Element that triggered event
  event.currentTarget // Element with event listener attached
  event.timeStamp     // When event occurred
  event.bubbles       // Whether event bubbles
  event.cancelable    // Whether event can be cancelled
  
  // Mouse events
  event.clientX       // X coordinate
  event.clientY       // Y coordinate
  event.button        // Which mouse button
  
  // Keyboard events
  event.key           // Key value: 'Enter', 'a', 'ArrowLeft'
  event.code          // Physical key: 'KeyA', 'Enter'
  event.shiftKey      // Shift key pressed
  event.ctrlKey       // Ctrl key pressed
  event.altKey        // Alt key pressed
  event.metaKey       // Meta/Cmd key pressed
  
  // Form events
  event.target.value  // Input value
  
  // Prevent default behavior
  event.preventDefault();
  
  // Stop event propagation
  event.stopPropagation();
  event.stopImmediatePropagation();
}
```

## Common Event Patterns

### Form Validation
```html
<!-- Inline (discouraged) -->
<form onsubmit="return validateForm()">

<!-- Better approach -->
<form id="myForm">
<script>
  document.getElementById('myForm').addEventListener('submit', (e) => {
    if (!isValid()) {
      e.preventDefault();
      showErrors();
    }
  });
</script>
```

### Keyboard Shortcuts
```html
<!-- Inline (discouraged) -->
<input onkeydown="if(event.key === 'Enter') submit()">

<!-- Better approach -->
<input id="searchInput">
<script>
  document.getElementById('searchInput').addEventListener('keydown', (e) => {
    if (e.key === 'Enter') {
      performSearch();
    }
  });
</script>
```

### Preventing Default Behavior
```html
<!-- Inline -->
<a href="#" onclick="doSomething(); return false;">Link</a>

<!-- Better -->
<a href="#" id="specialLink">Link</a>
<script>
  document.getElementById('specialLink').addEventListener('click', (e) => {
    e.preventDefault();
    doSomething();
  });
</script>
```

## Browser Compatibility Notes

- Most event attributes have excellent browser support
- Experimental events (marked above) have limited support
- Non-standard events work only in specific browsers
- Always provide fallbacks for cutting-edge features
- Test across browsers, especially mobile devices
- Touch events may not work on non-touch devices
- Pointer events are preferred over touch events for cross-device compatibility

## Summary

While HTML event attributes are supported and functional, modern web development strongly favors JavaScript event listeners using `addEventListener()`. Reserve inline event handlers for:

- Quick prototypes and demos
- Simple examples in documentation
- Situations where external JavaScript is unavailable

For production code, always use `addEventListener()` for better maintainability, security, and flexibility.