# Window Object Comprehensive Reference

## Overview

The Window interface represents a browser window containing a DOM document. It is the global object in browser JavaScript environments, meaning all global variables are properties of the window object, and all global functions are methods of it.

In a tabbed browser, each tab has its own Window object. The global `window` variable always represents the tab in which the code is running.

**Inheritance Chain:**
```
EventTarget → Window
```

## Key Concepts

### Global Object
The Window object serves as the global scope for JavaScript in browsers. Any variable declared globally becomes a property of the window object.

**Example:**
```javascript
var globalVar = 'Hello';
console.log(window.globalVar); // "Hello"

function globalFunc() {
  return 'World';
}
console.log(window.globalFunc()); // "World"
```

### Self-Reference
The Window object contains a reference to itself through the `window` property.

**Example:**
```javascript
console.log(window === window.window); // true
console.log(window === this); // true (in global scope)
```

## Instance Properties

### Navigation and Location

#### closed (Read-only)
A boolean indicating whether the window is closed.

**Type:** Boolean  
**Example:**
```javascript
const popup = window.open('https://example.com');
console.log(popup.closed); // false
popup.close();
console.log(popup.closed); // true
```

#### document (Read-only)
Returns a reference to the document contained in the window.

**Type:** Document  
**Example:**
```javascript
console.log(window.document.title);
window.document.getElementById('myElement');
```

#### frameElement (Read-only)
Returns the element in which the window is embedded, or null if not embedded.

**Type:** Element or null  
**Example:**
```javascript
// In an iframe
console.log(window.frameElement); // Returns the <iframe> element
// In a top-level window
console.log(window.frameElement); // null
```

#### frames (Read-only)
Returns an array-like object of subframes in the current window.

**Type:** WindowProxy[]  
**Example:**
```javascript
console.log(window.frames.length); // Number of iframes
console.log(window.frames[0]); // First iframe's window
```

#### history (Read-only)
Returns a reference to the History object.

**Type:** History  
**Example:**
```javascript
window.history.back();
window.history.forward();
window.history.go(-2);
```

#### length (Read-only)
Returns the number of frames in the window.

**Type:** Number  
**Example:**
```javascript
console.log(window.length); // Same as window.frames.length
```

#### location
Gets or sets the current URL of the window.

**Type:** Location  
**Example:**
```javascript
console.log(window.location.href); // Current URL
window.location.href = 'https://example.com'; // Navigate
window.location.reload(); // Reload page
```

#### name
Gets or sets the name of the window.

**Type:** String  
**Example:**
```javascript
window.name = 'myWindow';
console.log(window.name); // "myWindow"
```

#### navigation (Read-only)
Returns the Navigation object for the Navigation API.

**Type:** Navigation  
**Example:**
```javascript
window.navigation.navigate('/new-page');
```

#### navigator (Read-only)
Returns a reference to the Navigator object.

**Type:** Navigator  
**Example:**
```javascript
console.log(window.navigator.userAgent);
console.log(window.navigator.language);
console.log(window.navigator.onLine);
```

#### opener
Returns a reference to the window that opened this window.

**Type:** Window or null  
**Example:**
```javascript
const popup = window.open('page.html');
// In popup window:
console.log(window.opener); // Reference to parent window
```

#### origin (Read-only)
Returns the origin of the global scope, serialized as a string.

**Type:** String  
**Example:**
```javascript
console.log(window.origin); // "https://example.com"
```

#### parent (Read-only)
Returns a reference to the parent window or subframe.

**Type:** Window  
**Example:**
```javascript
// In iframe
window.parent.postMessage('Hello', '*');
```

#### self (Read-only)
Returns a reference to the window object itself.

**Type:** Window  
**Example:**
```javascript
console.log(window.self === window); // true
```

#### top (Read-only)
Returns the topmost window in the window hierarchy.

**Type:** Window  
**Example:**
```javascript
// Even in nested iframes
console.log(window.top); // Always the top-level window
```

### Dimensions and Screen

#### devicePixelRatio (Read-only)
Returns the ratio between physical pixels and device-independent pixels.

**Type:** Number  
**Example:**
```javascript
console.log(window.devicePixelRatio); // 2 on Retina displays
```

#### innerHeight (Read-only)
Returns the height of the content area including scrollbar if rendered.

**Type:** Number  
**Example:**
```javascript
console.log(window.innerHeight); // e.g., 768
```

#### innerWidth (Read-only)
Returns the width of the content area including scrollbar if rendered.

**Type:** Number  
**Example:**
```javascript
console.log(window.innerWidth); // e.g., 1024
```

#### outerHeight (Read-only)
Returns the height of the entire browser window.

**Type:** Number  
**Example:**
```javascript
console.log(window.outerHeight); // Includes browser chrome
```

#### outerWidth (Read-only)
Returns the width of the entire browser window.

**Type:** Number  
**Example:**
```javascript
console.log(window.outerWidth); // Includes browser chrome
```

#### screen (Read-only)
Returns a reference to the Screen object.

**Type:** Screen  
**Example:**
```javascript
console.log(window.screen.width); // Screen width
console.log(window.screen.height); // Screen height
console.log(window.screen.availWidth); // Available width
```

#### screenX / screenLeft (Read-only)
Returns the horizontal distance from the left edge of the screen.

**Type:** Number  
**Example:**
```javascript
console.log(window.screenX);
console.log(window.screenLeft); // Same as screenX
```

#### screenY / screenTop (Read-only)
Returns the vertical distance from the top edge of the screen.

**Type:** Number  
**Example:**
```javascript
console.log(window.screenY);
console.log(window.screenTop); // Same as screenY
```

#### scrollX / pageXOffset (Read-only)
Returns the number of pixels scrolled horizontally.

**Type:** Number  
**Example:**
```javascript
console.log(window.scrollX);
console.log(window.pageXOffset); // Alias
```

#### scrollY / pageYOffset (Read-only)
Returns the number of pixels scrolled vertically.

**Type:** Number  
**Example:**
```javascript
console.log(window.scrollY);
console.log(window.pageYOffset); // Alias
```

#### visualViewport (Read-only)
Returns the VisualViewport object representing the visual viewport.

**Type:** VisualViewport  
**Example:**
```javascript
console.log(window.visualViewport.width);
console.log(window.visualViewport.scale);
```

### Browser UI Elements

#### locationbar (Read-only)
Returns the locationbar object.

**Type:** BarProp  
**Example:**
```javascript
console.log(window.locationbar.visible);
```

#### menubar (Read-only)
Returns the menubar object.

**Type:** BarProp  
**Example:**
```javascript
console.log(window.menubar.visible);
```

#### personalbar (Read-only)
Returns the personalbar object.

**Type:** BarProp

#### scrollbars (Read-only)
Returns the scrollbars object.

**Type:** BarProp

#### statusbar (Read-only)
Returns the statusbar object.

**Type:** BarProp

#### toolbar (Read-only)
Returns the toolbar object.

**Type:** BarProp

### Storage and Data

#### caches (Read-only, Secure Context)
Returns the CacheStorage object for offline storage.

**Type:** CacheStorage  
**Example:**
```javascript
window.caches.open('my-cache').then(cache => {
  cache.add('/data.json');
});
```

#### cookieStore (Read-only, Secure Context)
Returns the CookieStore object for managing cookies.

**Type:** CookieStore  
**Example:**
```javascript
window.cookieStore.get('sessionId').then(cookie => {
  console.log(cookie.value);
});
```

#### crypto (Read-only)
Returns the Crypto object for cryptographic operations.

**Type:** Crypto  
**Example:**
```javascript
const array = new Uint32Array(10);
window.crypto.getRandomValues(array);
```

#### indexedDB (Read-only)
Returns an IDBFactory object for IndexedDB access.

**Type:** IDBFactory  
**Example:**
```javascript
const request = window.indexedDB.open('myDatabase', 1);
request.onsuccess = (event) => {
  const db = event.target.result;
};
```

#### localStorage (Read-only)
Returns the local storage object for persistent storage.

**Type:** Storage  
**Example:**
```javascript
window.localStorage.setItem('key', 'value');
console.log(window.localStorage.getItem('key'));
window.localStorage.removeItem('key');
window.localStorage.clear();
```

#### sessionStorage
Returns the session storage object for session-scoped storage.

**Type:** Storage  
**Example:**
```javascript
window.sessionStorage.setItem('tempData', 'value');
console.log(window.sessionStorage.getItem('tempData'));
```

### Security and Context

#### crossOriginIsolated (Read-only)
Returns a boolean indicating if the website is cross-origin isolated.

**Type:** Boolean  
**Example:**
```javascript
console.log(window.crossOriginIsolated);
```

#### credentialless (Read-only, Experimental)
Indicates if the document was loaded in a credentialless iframe.

**Type:** Boolean

#### isSecureContext (Read-only)
Returns whether the current context is secure (HTTPS).

**Type:** Boolean  
**Example:**
```javascript
if (window.isSecureContext) {
  // Use features requiring secure context
}
```

#### originAgentCluster (Read-only)
Indicates if the window belongs to an origin-keyed agent cluster.

**Type:** Boolean

### Web APIs and Features

#### customElements (Read-only)
Returns the CustomElementRegistry for custom elements.

**Type:** CustomElementRegistry  
**Example:**
```javascript
window.customElements.define('my-element', MyElement);
```

#### performance (Read-only)
Returns the Performance object for performance metrics.

**Type:** Performance  
**Example:**
```javascript
console.log(window.performance.now());
console.log(window.performance.timing.loadEventEnd);
```

#### scheduler (Read-only)
Returns the Scheduler object for task scheduling.

**Type:** Scheduler  
**Example:**
```javascript
window.scheduler.postTask(() => {
  console.log('Task executed');
}, { priority: 'user-blocking' });
```

#### speechSynthesis (Read-only)
Returns the SpeechSynthesis object for text-to-speech.

**Type:** SpeechSynthesis  
**Example:**
```javascript
const utterance = new SpeechSynthesisUtterance('Hello world');
window.speechSynthesis.speak(utterance);
```

#### trustedTypes (Read-only)
Returns the TrustedTypePolicyFactory for the Trusted Types API.

**Type:** TrustedTypePolicyFactory  
**Example:**
```javascript
const policy = window.trustedTypes.createPolicy('myPolicy', {
  createHTML: (input) => input
});
```

### Experimental and Special Features

#### documentPictureInPicture (Read-only, Experimental, Secure Context)
Returns the document Picture-in-Picture window.

**Type:** Window

#### fence (Read-only, Experimental)
Returns the Fence object for fenced frames.

**Type:** Fence

#### launchQueue (Read-only, Experimental)
Provides access to launch queue for PWAs.

**Type:** LaunchQueue

#### sharedStorage (Read-only, Experimental, Secure Context)
Returns the WindowSharedStorage object.

**Type:** WindowSharedStorage

#### viewport (Read-only, Experimental)
Returns information about the device viewport.

**Type:** Viewport

### Deprecated Properties

#### event (Deprecated, Read-only)
Returns the current event being processed.

**Note:** Use the event parameter in handlers instead.

#### external (Deprecated, Read-only)
Returns an object for adding external search providers.

#### orientation (Deprecated, Read-only)
Returns the viewport orientation in degrees.

**Note:** Use Screen Orientation API instead.

#### status (Deprecated)
Gets or sets the status bar text.

**Note:** Most browsers ignore this for security reasons.

## Instance Methods

### Dialog Methods

#### alert(message)
Displays an alert dialog with a message.

**Parameters:**
- message (optional): The message to display

**Returns:** None  
**Example:**
```javascript
window.alert('Warning: Data will be lost!');
```

#### confirm(message)
Displays a confirmation dialog with OK and Cancel buttons.

**Parameters:**
- message (optional): The message to display

**Returns:** Boolean (true if OK clicked, false if Cancel)  
**Example:**
```javascript
if (window.confirm('Are you sure you want to delete?')) {
  // User clicked OK
  deleteItem();
}
```

#### prompt(message, default)
Displays a dialog prompting the user for input.

**Parameters:**
- message (optional): The message to display
- default (optional): Default value for input field

**Returns:** String (user input) or null (if cancelled)  
**Example:**
```javascript
const name = window.prompt('Enter your name:', 'Guest');
if (name !== null) {
  console.log('Hello, ' + name);
}
```

#### print()
Opens the print dialog to print the current document.

**Returns:** None  
**Example:**
```javascript
window.print();
```

### Window Management

#### open(url, target, features)
Opens a new browser window or tab.

**Parameters:**
- url: The URL to load
- target: The name or browsing context
- features: Window features as a string

**Returns:** Window object or null  
**Example:**
```javascript
const popup = window.open(
  'https://example.com',
  'popup',
  'width=600,height=400,resizable=yes'
);
```

#### close()
Closes the current window.

**Returns:** None  
**Example:**
```javascript
window.close(); // Only works for windows opened by script
```

#### focus()
Sets focus on the current window.

**Returns:** None  
**Example:**
```javascript
window.focus();
```

#### blur() (Deprecated)
Removes focus from the window.

**Returns:** None

#### moveBy(deltaX, deltaY)
Moves the window by the specified amount.

**Parameters:**
- deltaX: Horizontal pixels to move
- deltaY: Vertical pixels to move

**Returns:** None  
**Example:**
```javascript
window.moveBy(50, 100); // Move 50px right, 100px down
```

#### moveTo(x, y)
Moves the window to specified coordinates.

**Parameters:**
- x: Horizontal screen coordinate
- y: Vertical screen coordinate

**Returns:** None  
**Example:**
```javascript
window.moveTo(100, 100); // Move to position (100, 100)
```

#### resizeBy(xDelta, yDelta)
Resizes the window by the specified amount.

**Parameters:**
- xDelta: Horizontal pixels to resize
- yDelta: Vertical pixels to resize

**Returns:** None  
**Example:**
```javascript
window.resizeBy(100, 50); // Increase width by 100, height by 50
```

#### resizeTo(width, height)
Resizes the window to specified dimensions.

**Parameters:**
- width: New width in pixels
- height: New height in pixels

**Returns:** None  
**Example:**
```javascript
window.resizeTo(800, 600);
```

### Scrolling Methods

#### scroll(x, y) / scroll(options)
Scrolls to particular coordinates or with options.

**Parameters:**
- x: Horizontal scroll position
- y: Vertical scroll position
- options: Object with left, top, behavior

**Returns:** None  
**Example:**
```javascript
window.scroll(0, 500);
// Or with smooth scrolling
window.scroll({
  top: 500,
  left: 0,
  behavior: 'smooth'
});
```

#### scrollBy(x, y) / scrollBy(options)
Scrolls by the given amount.

**Parameters:**
- x: Horizontal pixels to scroll
- y: Vertical pixels to scroll
- options: Object with left, top, behavior

**Returns:** None  
**Example:**
```javascript
window.scrollBy(0, 100); // Scroll down 100px
window.scrollBy({
  top: 100,
  behavior: 'smooth'
});
```

#### scrollTo(x, y) / scrollTo(options)
Scrolls to specified coordinates.

**Parameters:**
- x: Horizontal scroll position
- y: Vertical scroll position
- options: Object with left, top, behavior

**Returns:** None  
**Example:**
```javascript
window.scrollTo(0, 0); // Scroll to top
window.scrollTo({
  top: document.body.scrollHeight,
  behavior: 'smooth'
});
```

### Timing Methods

#### setTimeout(callback, delay, ...args)
Executes a function after a specified delay.

**Parameters:**
- callback: Function to execute
- delay: Delay in milliseconds
- args: Arguments to pass to callback

**Returns:** Number (timeout ID)  
**Example:**
```javascript
const timeoutId = window.setTimeout(() => {
  console.log('Executed after 2 seconds');
}, 2000);
```

#### clearTimeout(timeoutId)
Cancels a timeout set with setTimeout.

**Parameters:**
- timeoutId: ID returned by setTimeout

**Returns:** None  
**Example:**
```javascript
const id = window.setTimeout(() => console.log('Hi'), 1000);
window.clearTimeout(id); // Cancel the timeout
```

#### setInterval(callback, delay, ...args)
Repeatedly executes a function at specified intervals.

**Parameters:**
- callback: Function to execute
- delay: Interval in milliseconds
- args: Arguments to pass to callback

**Returns:** Number (interval ID)  
**Example:**
```javascript
const intervalId = window.setInterval(() => {
  console.log('Repeats every second');
}, 1000);
```

#### clearInterval(intervalId)
Cancels an interval set with setInterval.

**Parameters:**
- intervalId: ID returned by setInterval

**Returns:** None  
**Example:**
```javascript
const id = window.setInterval(() => console.log('Hi'), 1000);
window.clearInterval(id); // Stop the interval
```

### Animation and Idle Callbacks

#### requestAnimationFrame(callback)
Requests the browser to call a function before the next repaint.

**Parameters:**
- callback: Function to call before repaint

**Returns:** Number (request ID)  
**Example:**
```javascript
function animate() {
  // Animation code
  requestAnimationFrame(animate);
}
window.requestAnimationFrame(animate);
```

#### cancelAnimationFrame(requestId)
Cancels an animation frame request.

**Parameters:**
- requestId: ID returned by requestAnimationFrame

**Returns:** None  
**Example:**
```javascript
const id = window.requestAnimationFrame(animate);
window.cancelAnimationFrame(id);
```

#### requestIdleCallback(callback, options)
Queues a function to be called during idle periods.

**Parameters:**
- callback: Function to call when idle
- options: Object with timeout property

**Returns:** Number (request ID)  
**Example:**
```javascript
window.requestIdleCallback((deadline) => {
  while (deadline.timeRemaining() > 0 && tasks.length > 0) {
    doWork();
  }
}, { timeout: 2000 });
```

#### cancelIdleCallback(requestId)
Cancels an idle callback request.

**Parameters:**
- requestId: ID returned by requestIdleCallback

**Returns:** None  
**Example:**
```javascript
const id = window.requestIdleCallback(doWork);
window.cancelIdleCallback(id);
```

### Communication Methods

#### postMessage(message, targetOrigin, transfer)
Safely sends messages to other windows.

**Parameters:**
- message: Data to send
- targetOrigin: Target origin or "*"
- transfer: Array of transferable objects

**Returns:** None  
**Example:**
```javascript
// In parent window
iframe.contentWindow.postMessage('Hello', 'https://example.com');

// In iframe
window.addEventListener('message', (event) => {
  if (event.origin === 'https://parent.com') {
    console.log(event.data);
  }
});
```

### Encoding Methods

#### atob(encodedData)
Decodes a base-64 encoded string.

**Parameters:**
- encodedData: Base-64 encoded string

**Returns:** String  
**Example:**
```javascript
const decoded = window.atob('SGVsbG8gV29ybGQ=');
console.log(decoded); // "Hello World"
```

#### btoa(stringToEncode)
Creates a base-64 encoded ASCII string.

**Parameters:**
- stringToEncode: String to encode

**Returns:** String  
**Example:**
```javascript
const encoded = window.btoa('Hello World');
console.log(encoded); // "SGVsbG8gV29ybGQ="
```

### Resource and Network Methods

#### fetch(resource, options)
Starts the process of fetching a resource from the network.

**Parameters:**
- resource: URL or Request object
- options: Object with method, headers, body, etc.

**Returns:** Promise<Response>  
**Example:**
```javascript
window.fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

#### stop()
Stops window loading (equivalent to the browser's stop button).

**Returns:** None  
**Example:**
```javascript
window.stop();
```

### Selection and Styling Methods

#### getSelection()
Returns the Selection object representing selected text.

**Returns:** Selection  
**Example:**
```javascript
const selection = window.getSelection();
console.log(selection.toString());
```

#### getComputedStyle(element, pseudoElement)
Gets the computed style for an element.

**Parameters:**
- element: The element to query
- pseudoElement: Optional pseudo-element string

**Returns:** CSSStyleDeclaration  
**Example:**
```javascript
const element = document.getElementById('myElement');
const styles = window.getComputedStyle(element);
console.log(styles.color);
console.log(styles.getPropertyValue('font-size'));
```

#### matchMedia(mediaQueryString)
Returns a MediaQueryList object for a media query.

**Parameters:**
- mediaQueryString: Media query to evaluate

**Returns:** MediaQueryList  
**Example:**
```javascript
const mediaQuery = window.matchMedia('(min-width: 768px)');
console.log(mediaQuery.matches); // true or false

mediaQuery.addEventListener('change', (e) => {
  console.log('Media query changed:', e.matches);
});
```

### File System Methods (Experimental)

#### showOpenFilePicker(options)
Shows a file picker to select files.

**Parameters:**
- options: Object with types, excludeAcceptAllOption, multiple

**Returns:** Promise<FileSystemFileHandle[]>  
**Example:**
```javascript
const [fileHandle] = await window.showOpenFilePicker({
  types: [{
    description: 'Images',
    accept: { 'image/*': ['.png', '.jpg', '.jpeg'] }
  }],
  multiple: false
});
```

#### showSaveFilePicker(options)
Shows a file picker to save a file.

**Parameters:**
- options: Object with types, suggestedName

**Returns:** Promise<FileSystemFileHandle>  
**Example:**
```javascript
const fileHandle = await window.showSaveFilePicker({
  suggestedName: 'document.txt',
  types: [{
    description: 'Text Files',
    accept: { 'text/plain': ['.txt'] }
  }]
});
```

#### showDirectoryPicker(options)
Shows a directory picker.

**Parameters:**
- options: Object with mode

**Returns:** Promise<FileSystemDirectoryHandle>  
**Example:**
```javascript
const dirHandle = await window.showDirectoryPicker();
for await (const entry of dirHandle.values()) {
  console.log(entry.name);
}
```

### Image and Bitmap Methods

#### createImageBitmap(image, options)
Creates an ImageBitmap from various image sources.

**Parameters:**
- image: Image source
- options: Optional cropping and options

**Returns:** Promise<ImageBitmap>  
**Example:**
```javascript
const response = await fetch('image.png');
const blob = await response.blob();
const bitmap = await window.createImageBitmap(blob);
```

### Advanced Methods

#### queueMicrotask(callback)
Queues a microtask to execute.

**Parameters:**
- callback: Function to execute

**Returns:** None  
**Example:**
```javascript
window.queueMicrotask(() => {
  console.log('Microtask executed');
});
```

#### reportError(error)
Reports an error, emulating an unhandled exception.

**Parameters:**
- error: Error to report

**Returns:** None  
**Example:**
```javascript
window.reportError(new Error('Something went wrong'));
```

#### structuredClone(value, options)
Creates a deep clone using the structured clone algorithm.

**Parameters:**
- value: Value to clone
- options: Object with transfer array

**Returns:** Cloned value  
**Example:**
```javascript
const original = { a: 1, b: { c: 2 } };
const clone = window.structuredClone(original);
clone.b.c = 3;
console.log(original.b.c); // 2 (unchanged)
```

### Screen and Display Methods (Experimental)

#### getScreenDetails()
Returns details of all available screens.

**Returns:** Promise<ScreenDetails>  
**Example:**
```javascript
const screenDetails = await window.getScreenDetails();
console.log(screenDetails.screens);
```

#### queryLocalFonts()
Returns locally available fonts.

**Returns:** Promise<FontData[]>  
**Example:**
```javascript
const fonts = await window.queryLocalFonts();
fonts.forEach(font => console.log(font.family));
```

## Events

The Window object fires numerous events. Here are the major categories:

### Load and Unload Events

#### load
Fired when the whole page has loaded.

**Example:**
```javascript
window.addEventListener('load', () => {
  console.log('Page fully loaded');
});
```

#### unload
Fired when the document is being unloaded.

**Example:**
```javascript
window.addEventListener('unload', () => {
  console.log('Page is unloading');
});
```

#### beforeunload
Fired before the window is about to unload.

**Example:**
```javascript
window.addEventListener('beforeunload', (event) => {
  event.preventDefault();
  event.returnValue = ''; // Show confirmation dialog
});
```

### History Events

#### popstate
Fired when the active history entry changes.

**Example:**
```javascript
window.addEventListener('popstate', (event) => {
  console.log('State:', event.state);
});
```

#### hashchange
Fired when the URL fragment identifier changes.

**Example:**
```javascript
window.addEventListener('hashchange', (event) => {
  console.log('Hash changed from', event.oldURL, 'to', event.newURL);
});
```

#### pageshow
Fired when a page is displayed.

**Example:**
```javascript
window.addEventListener('pageshow', (event) => {
  if (event.persisted) {
    console.log('Loaded from cache');
  }
});
```

#### pagehide
Fired when a page is hidden.

**Example:**
```javascript
window.addEventListener('pagehide', (event) => {
  console.log('Page is being hidden');
});
```

### Focus Events

#### focus
Fired when the window gains focus.

**Example:**
```javascript
window.addEventListener('focus', () => {
  console.log('Window focused');
});
```

#### blur
Fired when the window loses focus.

**Example:**
```javascript
window.addEventListener('blur', () => {
  console.log('Window lost focus');
});
```

### Resize and Scroll Events

#### resize
Fired when the window is resized.

**Example:**
```javascript
window.addEventListener('resize', () => {
  console.log('Window size:', window.innerWidth, window.innerHeight);
});
```

### Connection Events

#### online
Fired when the browser gains network access.

**Example:**
```javascript
window.addEventListener('online', () => {
  console.log('Back online');
});
```

#### offline
Fired when the browser loses network access.

**Example:**
```javascript
window.addEventListener('offline', () => {
  console.log('Connection lost');
});
```

### Storage Events

#### storage
Fired when a storage area is modified in another document.

**Example:**
```javascript
window.addEventListener('storage', (event) => {
  console.log('Storage key:', event.key);
  console.log('Old value:', event.oldValue);
  console.log('New value:', event.newValue);
});
```

### Message Events

#### message
Fired when the window receives a message.

**Example:**
```javascript
window.addEventListener('message', (event) => {
  if (event.origin === 'https://trusted.com') {
    console.log('Message:', event.data);
  }
});
```

#### messageerror
Fired when a message cannot be deserialized.

**Example:**
```javascript
window.addEventListener('messageerror', (event) => {
  console.error('Message error:', event);
});
```

### Error Events

#### error
Fired when a resource fails to load or a JavaScript error occurs.

**Example:**
```javascript
window.addEventListener('error', (event) => {
  console.error('Error:', event.message);
  console.error('File:', event.filename);
  console.error('Line:', event.lineno);
});
```

### Promise Rejection Events

#### unhandledrejection
Fired when a Promise is rejected without a handler.

**Example:**
```javascript
window.addEventListener('unhandledrejection', (event) => {
  console.error('Unhandled rejection:', event.reason);
  event.preventDefault(); // Prevent default error handling
});
```

#### rejectionhandled
Fired when a Promise rejection is handled late.

**Example:**
```javascript
window.addEventListener('rejectionhandled', (event) => {
  console.log('Rejection was handled:', event.promise);
});
```

### Print Events

#### beforeprint
Fired before printing or print preview.

**Example:**
```javascript
window.addEventListener('beforeprint', () => {
  console.log('About to print');
});
```

#### afterprint
Fired after printing or closing print preview.

**Example:**
```javascript
window.addEventListener('afterprint', () => {
  console.log('Printing finished');
});
```

### Device Events

#### devicemotion
Fired when device acceleration changes.

**Example:**
```javascript
window.addEventListener('devicemotion', (event) => {
  console.log('Acceleration:', event.acceleration);
});
```

#### deviceorientation
Fired when device orientation changes.

**Example:**
```javascript
window.addEventListener('deviceorientation', (event) => {
  console.log('Alpha:', event.alpha);
  console.log('Beta:', event.beta);
  console.log('Gamma:', event.gamma);
});
```

### Language Events

#### languagechange
Fired when the user's preferred language changes.

**Example:**
```javascript
window.addEventListener('languagechange', () => {
  console.log('Language changed to:', navigator.language);
});
```

### Gamepad Events

#### gamepadconnected
Fired when a gamepad is connected.

**Example:**
```javascript
window.addEventListener('gamepadconnected', (event) => {
  console.log('Gamepad connected:', event.gamepad.id);
});
```

#### gamepaddisconnected
Fired when a gamepad is disconnected.

**Example:**
```javascript
window.addEventListener('gamepaddisconnected', (event) => {
  console.log('Gamepad disconnected:', event.gamepad.id);
});
```

## Named Properties

Elements with `name` or `id` attributes are exposed as window properties.

**Example:**
```html
<img id="logo" src="logo.png" />
<form name="loginForm">...</form>
<iframe name="contentFrame" src="page.html"></iframe>
```

```javascript
console.log(window.logo); // Reference to img element
console.log(window.loginForm); // Reference to form element
console.log(window.contentFrame); // Window object of iframe
```

**Important Notes:**
- For single elements, the element is directly accessible
- For multiple elements with the same name/id, an HTMLCollection is returned
- For iframes and objects, the contentWindow is returned
- This feature exists for backward compatibility but should be avoided in new code

## Best Practices

1. **Avoid Global Pollution**: Minimize global variables to prevent conflicts
   ```javascript
   // Bad
   var data = 'global';
   
   // Good
   (function() {
     const data = 'scoped';
   })();
   ```

2. **Use Modern APIs**: Prefer modern APIs over deprecated ones
   ```javascript
   // Deprecated
   window.event
   
   // Modern
   element.addEventListener('click', (event) => {
     // Use event parameter
   });
   ```

3. **Check for Feature Support**: Test for features before using them
   ```javascript
   if ('IntersectionObserver' in window) {
     // Use IntersectionObserver
   }
   ```

4. **Handle Cross-Origin Messaging Safely**: Always verify origin
   ```javascript
   window.addEventListener('message', (event) => {
     if (event.origin !== 'https://trusted.com') {
       return; // Reject untrusted messages
     }
     // Process message
   });
   ```

5. **Clean Up Resources**: Remove event listeners and clear timers
   ```javascript
   const timerId = setTimeout(callback, 1000);
   // Later
   clearTimeout(timerId);
   
   function handler() { }
   window.addEventListener('resize', handler);
   // Later
   window.removeEventListener('resize', handler);
   ```

6. **Use Passive Event Listeners**: Improve scroll performance
   ```javascript
   window.addEventListener('scroll', handler, { passive: true });
   ```

7. **Debounce Expensive Operations**: For resize and scroll events
   ```javascript
   let timeout;
   window.addEventListener('resize', () => {
     clearTimeout(timeout);
     timeout = setTimeout(() => {
       // Expensive operation
     }, 250);
   });
   ```

## Security Considerations

1. **Same-Origin Policy**: Windows can only access properties of windows from the same origin
2. **Content Security Policy**: May restrict inline scripts and eval
3. **Secure Contexts**: Many features require HTTPS (isSecureContext)
4. **Cross-Origin Isolation**: Some features require special headers
5. **Popup Blocking**: Modern browsers block popups opened without user interaction

## Browser Compatibility

The Window interface has excellent support across all modern browsers. However, some newer features have limited support:

- Basic properties and methods: Supported since the early days of JavaScript
- Crypto API: Supported in all modern browsers
- File System Access API: Limited to Chromium-based browsers
- Document Picture-in-Picture: Chromium only
- Shared Storage API: Experimental, Chromium only

Always check current compatibility tables before using newer features.

## Common Patterns

### Detecting if Code is Running in an Iframe
```javascript
if (window !== window.top) {
  console.log('Running in an iframe');
}
```

### Communicating Between Windows
```javascript
// Parent window
const popup = window.open('popup.html');
popup.postMessage({ type: 'init' }, '*');

// Popup window
window.addEventListener('message', (event) => {
  if (event.data.type === 'init') {
    // Initialize popup
  }
});
```

### Responsive Layout Detection
```javascript
const mobileQuery = window.matchMedia('(max-width: 768px)');

function handleMobileChange(e) {
  if (e.matches) {
    console.log('Mobile layout');
  } else {
    console.log('Desktop layout');
  }
}

mobileQuery.addEventListener('change', handleMobileChange);
handleMobileChange(mobileQuery);
```

### Detecting Online/Offline Status
```javascript
function updateOnlineStatus() {
  console.log(navigator.onLine ? 'Online' : 'Offline');
}

window.addEventListener('online', updateOnlineStatus);
window.addEventListener('offline', updateOnlineStatus);
```

### Smooth Scrolling to Top
```javascript
function scrollToTop() {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  });
}
```

### Viewport Size with Resize Handling
```javascript
function updateViewportSize() {
  const width = window.innerWidth;
  const height = window.innerHeight;
  console.log(`Viewport: ${width}x${height}`);
}

window.addEventListener('resize', updateViewportSize);
updateViewportSize();
```

---
