# JavaScript Document Object Reference

## 1. Overview

The `document` object represents the HTML document loaded in the browser window. It serves as the entry point to the Document Object Model (DOM) tree, providing methods and properties to access, manipulate, and traverse HTML elements. The `document` object is a property of the `window` object and implements the `Document` interface.

## 2. Element Selection Methods

### 2.1 getElementById()

Returns the element with the specified ID attribute. Returns `null` if no element is found.

**Syntax:**
```javascript
document.getElementById(id)
```

**Return Value:** `HTMLElement | null`

**Usage:**
```javascript
const header = document.getElementById('main-header');
const btn = document.getElementById('submit-btn');

if (header) {
    header.style.color = 'blue';
}
```

### 2.2 getElementsByClassName()

Returns a live HTMLCollection of elements with the specified class name(s).

**Syntax:**
```javascript
document.getElementsByClassName(classNames)
```

**Return Value:** `HTMLCollection` (live collection)

**Usage:**
```javascript
const items = document.getElementsByClassName('item');
const activeItems = document.getElementsByClassName('item active');

for (let i = 0; i < items.length; i++) {
    items[i].style.fontWeight = 'bold';
}

const itemsArray = Array.from(items);
itemsArray.forEach(item => console.log(item));
```

### 2.3 getElementsByTagName()

Returns a live HTMLCollection of elements with the specified tag name.

**Syntax:**
```javascript
document.getElementsByTagName(tagName)
```

**Return Value:** `HTMLCollection` (live collection)

**Usage:**
```javascript
const paragraphs = document.getElementsByTagName('p');
const divs = document.getElementsByTagName('div');
const allElements = document.getElementsByTagName('*');
```

### 2.4 getElementsByName()

Returns a live NodeList of elements with the specified `name` attribute.

**Syntax:**
```javascript
document.getElementsByName(name)
```

**Return Value:** `NodeList` (live collection)

**Usage:**
```javascript
const radioButtons = document.getElementsByName('gender');

radioButtons.forEach(button => {
    button.addEventListener('change', function() {
        console.log('Selected:', this.value);
    });
});
```

### 2.5 querySelector()

Returns the first element matching the specified CSS selector(s). Returns `null` if no match is found.

**Syntax:**
```javascript
document.querySelector(selectors)
```

**Return Value:** `Element | null`

**Usage:**
```javascript
const header = document.querySelector('#header');
const firstItem = document.querySelector('.item');
const paragraph = document.querySelector('p');
const link = document.querySelector('nav > ul > li > a');
const input = document.querySelector('input[type="email"]');
const lastChild = document.querySelector('ul li:last-child');
const dataAttr = document.querySelector('[data-id="123"]');
const firstP = document.querySelector('p:first-child');
const element = document.querySelector('h1, h2, h3');
```

### 2.6 querySelectorAll()

Returns a static NodeList of all elements matching the specified CSS selector(s).

**Syntax:**
```javascript
document.querySelectorAll(selectors)
```

**Return Value:** `NodeList` (static collection)

**Usage:**
```javascript
const paragraphs = document.querySelectorAll('p');
const items = document.querySelectorAll('.item.active');
const requiredInputs = document.querySelectorAll('input[required]');
const navLinks = document.querySelectorAll('nav a');

items.forEach(item => {
    item.style.backgroundColor = 'yellow';
});

const itemsArray = [...items];
const filtered = itemsArray.filter(item => item.textContent.includes('test'));
const headings = document.querySelectorAll('h1, h2, h3, h4, h5, h6');
```

### Comparison of Selection Methods

| Method | Returns | Live/Static | Flexibility | Performance |
|--------|---------|-------------|-------------|-------------|
| `getElementById()` | Single element | N/A | Low | Fastest |
| `getElementsByClassName()` | HTMLCollection | Live | Medium | Fast |
| `getElementsByTagName()` | HTMLCollection | Live | Low | Fast |
| `getElementsByName()` | NodeList | Live | Low | Fast |
| `querySelector()` | Single element | Static | High | Medium |
| `querySelectorAll()` | NodeList | Static | High | Medium |

## 3. Element Creation Methods

### 3.1 createElement()

Creates a new HTML element with the specified tag name.

**Syntax:**
```javascript
document.createElement(tagName [, options])
```

**Return Value:** `HTMLElement`

**Usage:**
```javascript
const div = document.createElement('div');
const paragraph = document.createElement('p');
const button = document.createElement('button');

div.id = 'container';
div.className = 'wrapper';
paragraph.textContent = 'Hello, World!';
button.innerHTML = 'Click Me';
```

### 3.2 createTextNode()

Creates a new text node containing the specified text.

**Syntax:**
```javascript
document.createTextNode(data)
```

**Return Value:** `Text`

**Usage:**
```javascript
const textNode = document.createTextNode('This is text content');
const paragraph = document.createElement('p');
paragraph.appendChild(textNode);
document.body.appendChild(paragraph);
```

### 3.3 createDocumentFragment()

Creates a lightweight document fragment. Useful for building multiple elements before inserting into DOM.

**Syntax:**
```javascript
document.createDocumentFragment()
```

**Return Value:** `DocumentFragment`

**Usage:**
```javascript
const fragment = document.createDocumentFragment();

for (let i = 0; i < 100; i++) {
    const li = document.createElement('li');
    li.textContent = `Item ${i}`;
    fragment.appendChild(li);
}

document.querySelector('ul').appendChild(fragment);
```

### 3.4 createComment()

Creates a comment node.

**Syntax:**
```javascript
document.createComment(data)
```

**Usage:**
```javascript
const comment = document.createComment('This is a comment');
document.body.appendChild(comment);
```

## 4. DOM Manipulation Methods

### 4.1 appendChild()

Appends a node as the last child of a parent node.

**Syntax:**
```javascript
parentNode.appendChild(childNode)
```

**Usage:**
```javascript
const parent = document.getElementById('container');
const child = document.createElement('div');
child.textContent = 'New child';

parent.appendChild(child);

const existingElement = document.getElementById('move-me');
parent.appendChild(existingElement);
```

### 4.2 insertBefore()

Inserts a node before a reference node as a child of a parent node.

**Syntax:**
```javascript
parentNode.insertBefore(newNode, referenceNode)
```

**Usage:**
```javascript
const parent = document.getElementById('list');
const newItem = document.createElement('li');
const referenceItem = document.querySelector('li:nth-child(2)');

parent.insertBefore(newItem, referenceItem);
parent.insertBefore(newItem, parent.firstChild);
```

### 4.3 removeChild()

Removes a child node from the DOM.

**Syntax:**
```javascript
parentNode.removeChild(childNode)
```

**Usage:**
```javascript
const parent = document.getElementById('container');
const child = document.getElementById('remove-me');

parent.removeChild(child);

const element = document.getElementById('remove-me');
element.parentNode.removeChild(element);
element.remove();
```

### 4.4 replaceChild()

Replaces a child node with a new node.

**Syntax:**
```javascript
parentNode.replaceChild(newChild, oldChild)
```

**Usage:**
```javascript
const parent = document.getElementById('container');
const newElement = document.createElement('p');
newElement.textContent = 'New content';
const oldElement = document.getElementById('old');

parent.replaceChild(newElement, oldElement);
```

### 4.5 cloneNode()

Creates a copy of a node.

**Syntax:**
```javascript
node.cloneNode([deep])
```

**Usage:**
```javascript
const original = document.getElementById('template');

const shallowClone = original.cloneNode(false);
const deepClone = original.cloneNode(true);

document.body.appendChild(deepClone);
```

## 5. Document Properties

### 5.1 document.body

Reference to the `<body>` element.

**Type:** `HTMLBodyElement | null`

**Usage:**
```javascript
document.body.style.backgroundColor = 'lightblue';
document.body.innerHTML = '<h1>New Content</h1>';

const div = document.createElement('div');
document.body.appendChild(div);
```

### 5.2 document.head

Reference to the `<head>` element.

**Type:** `HTMLHeadElement | null`

**Usage:**
```javascript
const link = document.createElement('link');
link.rel = 'stylesheet';
link.href = 'styles.css';
document.head.appendChild(link);

const meta = document.createElement('meta');
meta.name = 'description';
meta.content = 'Page description';
document.head.appendChild(meta);
```

### 5.3 document.documentElement

Returns the root element of the document (`<html>` element).

**Type:** `HTMLElement`

**Usage:**
```javascript
const lang = document.documentElement.lang;
document.documentElement.setAttribute('data-theme', 'dark');
document.documentElement.scrollTop = 0;
```

### 5.4 document.title

Gets or sets the document title.

**Type:** `String`

**Usage:**
```javascript
console.log(document.title);
document.title = 'New Page Title';
document.title = `${pageCount} items - My App`;
```

### 5.5 document.URL

Returns the complete URL of the document.

**Type:** `String` (read-only)

**Usage:**
```javascript
console.log(document.URL);

const url = new URL(document.URL);
console.log(url.hostname);
console.log(url.pathname);
```

### 5.6 document.referrer

Returns the URL of the page that linked to the current page.

**Type:** `String` (read-only)

**Usage:**
```javascript
const previousPage = document.referrer;
console.log('Came from:', previousPage);

if (document.referrer) {
    console.log('User came from another page');
} else {
    console.log('Direct visit or referrer blocked');
}
```

### 5.7 document.readyState

Returns the loading state of the document.

**Type:** `String` (read-only)

**Possible Values:**
- `"loading"`: Document still loading
- `"interactive"`: Document parsed, subresources loading
- `"complete"`: Document and all subresources loaded

**Usage:**
```javascript
console.log(document.readyState);

if (document.readyState === 'complete') {
    init();
} else {
    document.addEventListener('DOMContentLoaded', init);
}

document.onreadystatechange = function() {
    if (document.readyState === 'interactive') {
        console.log('DOM ready');
    } else if (document.readyState === 'complete') {
        console.log('Page fully loaded');
    }
};
```

### 5.8 document.cookie

Gets or sets cookies associated with the document.

**Type:** `String`

**Reading Cookies:**
```javascript
console.log(document.cookie);

function getCookie(name) {
    const cookies = document.cookie.split(';');
    for (let cookie of cookies) {
        const [key, value] = cookie.trim().split('=');
        if (key === name) {
            return decodeURIComponent(value);
        }
    }
    return null;
}

const username = getCookie('username');
```

**Setting Cookies:**
```javascript
document.cookie = "username=John";

const expirationDate = new Date();
expirationDate.setDate(expirationDate.getDate() + 7);
document.cookie = `token=abc123; expires=${expirationDate.toUTCString()}`;

document.cookie = "session=xyz; max-age=3600";
document.cookie = "user=John; path=/";
document.cookie = "theme=dark; domain=example.com";
document.cookie = "auth=token; secure; samesite=strict";

function setCookie(name, value, days) {
    const date = new Date();
    date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
    const expires = `expires=${date.toUTCString()}`;
    document.cookie = `${name}=${value}; ${expires}; path=/`;
}

setCookie('preferences', 'darkMode', 30);
```

**Deleting Cookies:**
```javascript
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/";

function deleteCookie(name) {
    document.cookie = `${name}=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/`;
}

deleteCookie('session');
```

### 5.9 document.location

Returns the Location object for the document.

**Type:** `Location`

**Usage:**
```javascript
console.log(document.location.href);

document.location.href = 'https://example.com';
document.location.reload();

console.log(document.location.protocol);
console.log(document.location.hostname);
console.log(document.location.pathname);
console.log(document.location.search);
console.log(document.location.hash);
```

### 5.10 document.forms

Returns HTMLCollection of all `<form>` elements.

**Type:** `HTMLCollection`

**Usage:**
```javascript
const forms = document.forms;

const firstForm = document.forms[0];
const loginForm = document.forms['login'];
const loginForm2 = document.forms.login;

for (let form of document.forms) {
    form.addEventListener('submit', handleSubmit);
}
```

### 5.11 document.images

Returns HTMLCollection of all `<img>` elements.

**Type:** `HTMLCollection`

**Usage:**
```javascript
const images = document.images;

for (let img of document.images) {
    console.log('Loading:', img.src);
}
```

### 5.12 document.links

Returns HTMLCollection of all links with href attribute.

**Type:** `HTMLCollection`

**Usage:**
```javascript
const links = document.links;

for (let link of document.links) {
    if (link.hostname !== location.hostname) {
        link.target = '_blank';
        link.rel = 'noopener noreferrer';
    }
}
```

### 5.13 document.scripts

Returns HTMLCollection of all `<script>` elements.

**Type:** `HTMLCollection`

**Usage:**
```javascript
const scripts = document.scripts;

console.log(`Total scripts: ${scripts.length}`);

for (let script of document.scripts) {
    if (script.src.includes('analytics')) {
        console.log('Analytics loaded');
    }
}
```

### 5.14 document.styleSheets

Returns StyleSheetList of all stylesheets.

**Type:** `StyleSheetList`

**Usage:**
```javascript
const sheets = document.styleSheets;

for (let sheet of document.styleSheets) {
    console.log(sheet.href);
}
```

### 5.15 document.activeElement

Returns the currently focused element.

**Type:** `Element | null`

**Usage:**
```javascript
const focused = document.activeElement;
console.log(focused.tagName);

if (document.activeElement === myInput) {
    console.log('Input is focused');
}

document.addEventListener('focusin', () => {
    console.log('Focus on:', document.activeElement);
});
```

### 5.16 document.characterSet

Returns the character encoding of the document.

**Type:** `String` (read-only)

**Usage:**
```javascript
console.log(document.characterSet);
```

### 5.17 document.doctype

Returns the Document Type Declaration of the document.

**Type:** `DocumentType | null`

**Usage:**
```javascript
const doctype = document.doctype;

if (doctype) {
    console.log(doctype.name);
    console.log(doctype.publicId);
    console.log(doctype.systemId);
}
```

## 6. Document Write Methods

### 6.1 document.write()

Writes HTML expressions or JavaScript code to the document stream.

**Syntax:**
```javascript
document.write(markup)
```

**Usage:**
```javascript
document.write('<h1>Hello World</h1>');
document.write('<p>Current date: ' + new Date() + '</p>');
```

**Warning:** Overwrites entire document if called after page load. Rarely used in modern development.

### 6.2 document.writeln()

Similar to `document.write()`, but adds a newline character.

**Syntax:**
```javascript
document.writeln(markup)
```

### 6.3 document.open()

Opens the document for writing. Clears existing content.

**Syntax:**
```javascript
document.open()
```

### 6.4 document.close()

Closes the document stream opened by `document.open()`.

**Syntax:**
```javascript
document.close()
```

## 7. Event Methods

### 7.1 addEventListener()

Attaches an event handler to the document.

**Syntax:**
```javascript
document.addEventListener(type, listener [, options])
```

**Usage:**
```javascript
document.addEventListener('DOMContentLoaded', function() {
    console.log('DOM ready');
});

document.addEventListener('click', (e) => {
    console.log('Clicked at:', e.clientX, e.clientY);
});

document.addEventListener('scroll', handleScroll, {
    passive: true,
    capture: false,
    once: true
});

document.addEventListener('keydown', (e) => {
    if (e.key === 'Escape') {
        closeModal();
    }
});

document.addEventListener('mousemove', (e) => {
    cursor.style.left = e.clientX + 'px';
    cursor.style.top = e.clientY + 'px';
});
```

**Common Document Events:**
- `DOMContentLoaded`: DOM tree built
- `readystatechange`: Document.readyState changes
- `click`: Mouse click
- `keydown`, `keyup`, `keypress`: Keyboard events
- `scroll`: Document scrolled
- `visibilitychange`: Page visibility changes

### 7.2 removeEventListener()

Removes an event handler from the document.

**Syntax:**
```javascript
document.removeEventListener(type, listener [, options])
```

**Usage:**
```javascript
function handleClick(e) {
    console.log('Clicked');
}

document.addEventListener('click', handleClick);
document.removeEventListener('click', handleClick);
```

### 7.3 dispatchEvent()

Dispatches a synthetic event on the document.

**Syntax:**
```javascript
document.dispatchEvent(event)
```

**Usage:**
```javascript
const customEvent = new CustomEvent('myEvent', {
    detail: { message: 'Hello' },
    bubbles: true,
    cancelable: true
});

document.addEventListener('myEvent', (e) => {
    console.log(e.detail.message);
});

document.dispatchEvent(customEvent);

const clickEvent = new MouseEvent('click', {
    bubbles: true,
    cancelable: true
});
document.dispatchEvent(clickEvent);
```

## 8. Additional Methods

### 8.1 document.hasFocus()

Returns boolean indicating if document or any element has focus.

**Syntax:**
```javascript
document.hasFocus()
```

**Return Value:** `Boolean`

**Usage:**
```javascript
setInterval(() => {
    if (document.hasFocus()) {
        console.log('Window is focused');
    } else {
        console.log('Window is not focused');
    }
}, 1000);
```

### 8.2 document.importNode()

Imports a node from another document.

**Syntax:**
```javascript
document.importNode(externalNode, deep)
```

**Usage:**
```javascript
const iframe = document.querySelector('iframe');
const externalNode = iframe.contentDocument.querySelector('.item');
const importedNode = document.importNode(externalNode, true);
document.body.appendChild(importedNode);
```

### 8.3 document.adoptNode()

Adopts a node from another document.

**Syntax:**
```javascript
document.adoptNode(externalNode)
```

**Usage:**
```javascript
const iframe = document.querySelector('iframe');
const externalNode = iframe.contentDocument.querySelector('.item');
document.adoptNode(externalNode);
document.body.appendChild(externalNode);
```

## 9. Visibility and Focus

### 9.1 document.hidden

Returns boolean indicating if page is hidden.

**Type:** `Boolean` (read-only)

**Usage:**
```javascript
if (document.hidden) {
    pauseVideo();
} else {
    playVideo();
}

document.addEventListener('visibilitychange', () => {
    if (document.hidden) {
        console.log('Tab is hidden');
    } else {
        console.log('Tab is visible');
    }
});
```

### 9.2 document.visibilityState

Returns visibility state of document.

**Type:** `String` (read-only)

**Possible Values:**
- `"visible"`: Page content may be partially visible
- `"hidden"`: Page content is not visible

**Usage:**
```javascript
console.log(document.visibilityState);

switch (document.visibilityState) {
    case 'visible':
        resumeAnimations();
        break;
    case 'hidden':
        pauseAnimations();
        break;
}
```

## 10. Best Practices

### 10.1 Performance Optimization

**Minimize DOM Access:**
```javascript
const container = document.getElementById('container');
const fragment = document.createDocumentFragment();
for (let i = 0; i < 100; i++) {
    fragment.appendChild(createItem());
}
container.appendChild(fragment);
```

**Cache Selectors:**
```javascript
const button = document.getElementById('btn');
button.addEventListener('click', handleClick);
button.style.color = 'red';
```

### 10.2 Modern Selection

Prefer `querySelector` and `querySelectorAll` for flexibility:

```javascript
const element = document.querySelector('.class[data-id="123"]');
const elements = document.querySelectorAll('div > p:first-child');
```

### 10.3 Event Delegation

Use event delegation for dynamic content:

```javascript
document.addEventListener('click', (e) => {
    if (e.target.matches('.delete-btn')) {
        deleteItem(e.target.closest('.item'));
    }
});
```

### 10.4 Security

Avoid `innerHTML` with user input:

```javascript
const userInput = '<script>alert("XSS")</script>';
element.textContent = userInput;
```

### 10.5 DOM Ready

Wait for DOM before manipulation:

```javascript
document.addEventListener('DOMContentLoaded', () => {
    initializeApp();
});

if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', init);
} else {
    init();
}
```

## 11. Browser Compatibility

Most document methods and properties are universally supported across modern browsers. Notable considerations:

- `querySelector/querySelectorAll`: IE9+
- `classList`: IE10+
- `DocumentFragment`: All browsers
- `DOMContentLoaded`: All modern browsers
- `document.hidden`: IE10+

## 12. Common Patterns

### 12.1 Dynamic Content Loading

```javascript
fetch('/api/data')
    .then(response => response.json())
    .then(data => {
        const fragment = document.createDocumentFragment();
        data.forEach(item => {
            const el = document.createElement('div');
            el.textContent = item.name;
            fragment.appendChild(el);
        });
        document.getElementById('container').appendChild(fragment);
    });
```

### 12.2 Form Handling

```javascript
const form = document.forms['contact'];
form.addEventListener('submit', (e) => {
    e.preventDefault();
    const data = new FormData(form);
    submitForm(data);
});
```

### 12.3 Scroll Detection

```javascript
document.addEventListener('scroll', () => {
    const scrolled = document.documentElement.scrollTop;
    const height = document.documentElement.scrollHeight;
    const viewport = document.documentElement.clientHeight;
    
    if (scrolled + viewport >= height - 100) {
        loadMoreContent();
    }
});
```

---
