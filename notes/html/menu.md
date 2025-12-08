# `<menu>`

## Key Topics

+ [Definition and Purpose](#definition-and-purpose)
+ [Syntax and Variants](#syntax-and-variants)
+ [Attributes](#attributes)
+ [Content Model](#content-model)
+ [Context](#context)
+ [Behavior and Semantics](#behavior-and-semantics)
+ [Examples](#examples)
+ [Notes](#notes)

---

## Definition and Purpose

The `<menu>` element represents a group of commands that a user can perform or activate. It serves as a semantic container for interactive elements, typically used for toolbar-style interfaces, context menus, or lists of form controls. The element has evolved through HTML specifications, with its current purpose in HTML5 focusing on creating accessible, semantic groupings of interactive controls rather than traditional navigation lists.

---

## Syntax and Variants

+ **Standard syntax**: `<menu>...</menu>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain list items and interactive elements
+ **Two contextual types**:
  - Toolbar menus: Horizontal groups of interactive controls
  - Context menus: Popup-style menus (requires JavaScript)
+ **No self-closing variant**: Must contain child elements

---

## Attributes

+ **Core attributes**:
  - `type` (optional): Specifies the menu type - `toolbar`, `context`, or `list` (default)
  - `label` (optional): Provides an accessible name for the menu

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Event attributes**: Supports all standard event handlers

+ **Deprecated attributes**: 
  - `compact` (obsolete in HTML5)

---

## Content Model

+ **Permitted content**: Zero or more `<li>`, `<script>`, or `<template>` elements
+ **Allowed content patterns**:
  - `<li>` elements containing interactive controls
  - Mix of `<li>` and flow content in certain contexts
  - Script-supporting elements
+ **Interactive content**: Typically contains buttons, links, or form controls
+ **Restricted content**: Cannot directly contain text nodes without container elements

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Application toolbars and control panels
  - Context menus (with JavaScript implementation)
  - Form control groupings
  - Interactive application interfaces
+ **Sibling relationships**: Can be used alongside other semantic grouping elements
+ **Nesting**: Can contain nested menus in complex interface designs

---

## Behavior and Semantics

+ **Default display**: Block-level element (`display: block`)
+ **Default styling**:
  - Similar to `<ul>` with list styling: `list-style-type: disc`
  - Padding and margin similar to other list elements
  - No inherent visual distinction from regular lists
+ **Semantic meaning**:
  - Represents a group of commands or interactive options
  - Provides semantic structure for toolbar interfaces
  - Enhances accessibility for complex control groupings
+ **Accessibility role**:
  - Default role: `menu` when `type` is specified
  - Screen readers announce as menu containers
  - Supports keyboard navigation patterns

---

## Examples

**Basic toolbar menu:**
```html
<menu type="toolbar">
  <li><button onclick="saveDocument()">Save</button></li>
  <li><button onclick="printDocument()">Print</button></li>
  <li><button onclick="shareDocument()">Share</button></li>
</menu>
```

**Context menu structure:**
```html
<menu type="context" id="text-context-menu">
  <li><button onclick="copyText()">Copy</button></li>
  <li><button onclick="cutText()">Cut</button></li>
  <li><button onclick="pasteText()">Paste</button></li>
  <li role="separator"></li>
  <li><button onclick="selectAll()">Select All</button></li>
</menu>

<script>
// Context menu would be triggered via JavaScript
document.addEventListener('contextmenu', function(e) {
  e.preventDefault();
  const menu = document.getElementById('text-context-menu');
  menu.style.display = 'block';
  menu.style.left = e.pageX + 'px';
  menu.style.top = e.pageY + 'px';
});
</script>
```

**Styled toolbar with icons:**
```html
<menu type="toolbar" class="editor-toolbar" aria-label="Text formatting tools">
  <li>
    <button type="button" aria-label="Bold" onclick="formatText('bold')">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
        <path d="M15.6 10.79c.97-.67 1.65-1.77 1.65-2.79 0-2.26-1.75-4-4-4H7v14h7.04c2.09 0 3.71-1.7 3.71-3.79 0-1.52-.86-2.82-2.15-3.42zM10 6.5h3c.83 0 1.5.67 1.5 1.5s-.67 1.5-1.5 1.5h-3v-3zm3.5 9H10v-3h3.5c.83 0 1.5.67 1.5 1.5s-.67 1.5-1.5 1.5z"/>
      </svg>
    </button>
  </li>
  <li>
    <button type="button" aria-label="Italic" onclick="formatText('italic')">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
        <path d="M10 4v3h2.21l-3.42 8H6v3h8v-3h-2.21l3.42-8H18V4z"/>
      </svg>
    </button>
  </li>
  <li>
    <button type="button" aria-label="Underline" onclick="formatText('underline')">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
        <path d="M12 17c3.31 0 6-2.69 6-6V3h-2.5v8c0 1.93-1.57 3.5-3.5 3.5S8.5 12.93 8.5 11V3H6v8c0 3.31 2.69 6 6 6zm-7 2v2h14v-2H5z"/>
      </svg>
    </button>
  </li>
</menu>

<style>
.editor-toolbar {
  display: flex;
  gap: 4px;
  padding: 8px;
  background: #f5f5f5;
  border: 1px solid #ddd;
  border-radius: 4px;
  list-style: none;
  margin: 0;
}

.editor-toolbar button {
  padding: 8px;
  border: 1px solid #ccc;
  background: white;
  border-radius: 3px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.editor-toolbar button:hover {
  background: #e9e9e9;
}

.editor-toolbar button:active {
  background: #ddd;
}
</style>
```

**Form control grouping menu:**
```html
<menu class="form-actions" aria-label="Document actions">
  <li>
    <button type="submit" class="btn-primary">Save Changes</button>
  </li>
  <li>
    <button type="reset" class="btn-secondary">Reset</button>
  </li>
  <li>
    <button type="button" class="btn-secondary" onclick="previewDocument()">Preview</button>
  </li>
  <li>
    <button type="button" class="btn-danger" onclick="deleteDocument()">Delete</button>
  </li>
</menu>

<style>
.form-actions {
  display: flex;
  gap: 12px;
  list-style: none;
  padding: 0;
  margin: 20px 0;
  flex-wrap: wrap;
}

.btn-primary {
  background: #007bff;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.btn-secondary {
  background: #6c757d;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.btn-danger {
  background: #dc3545;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
```

**Accessible context menu implementation:**
```html
<menu type="context" id="accessible-context-menu" class="context-menu" 
      aria-label="Page options" hidden>
  <li>
    <button type="button" onclick="reloadPage()" aria-keyshortcuts="R">
      <span>Reload</span>
      <kbd aria-hidden="true">R</kbd>
    </button>
  </li>
  <li>
    <button type="button" onclick="viewSource()" aria-keyshortcuts="U">
      <span>View Source</span>
      <kbd aria-hidden="true">U</kbd>
    </button>
  </li>
  <li role="separator"></li>
  <li>
    <button type="button" onclick="inspectElement()" aria-keyshortcuts="I">
      <span>Inspect</span>
      <kbd aria-hidden="true">I</kbd>
    </button>
  </li>
</menu>

<script>
let currentTarget = null;

document.addEventListener('contextmenu', (e) => {
  e.preventDefault();
  currentTarget = e.target;
  
  const menu = document.getElementById('accessible-context-menu');
  menu.hidden = false;
  menu.style.left = `${e.pageX}px`;
  menu.style.top = `${e.pageY}px`;
  
  // Focus first item for keyboard navigation
  const firstButton = menu.querySelector('button');
  firstButton.focus();
});

// Close menu when clicking outside
document.addEventListener('click', (e) => {
  if (!e.target.closest('.context-menu')) {
    document.getElementById('accessible-context-menu').hidden = true;
  }
});

// Keyboard navigation
document.addEventListener('keydown', (e) => {
  const menu = document.getElementById('accessible-context-menu');
  if (menu.hidden) return;
  
  if (e.key === 'Escape') {
    menu.hidden = true;
    currentTarget?.focus();
  }
});
</script>

<style>
.context-menu {
  position: fixed;
  background: white;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  padding: 4px 0;
  min-width: 180px;
  z-index: 1000;
}

.context-menu li {
  list-style: none;
  margin: 0;
}

.context-menu button {
  width: 100%;
  padding: 8px 16px;
  border: none;
  background: none;
  text-align: left;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.context-menu button:hover {
  background: #f0f0f0;
}

.context-menu [role="separator"] {
  height: 1px;
  background: #eee;
  margin: 4px 0;
}

.context-menu kbd {
  background: #f5f5f5;
  border: 1px solid #ddd;
  border-radius: 3px;
  padding: 2px 6px;
  font-size: 0.8em;
}
</style>
```

**Nested menu structure:**
```html
<menu type="toolbar" class="nested-menu" aria-label="Advanced editing tools">
  <li>
    <button onclick="insertText()">Insert</button>
    <menu class="submenu">
      <li><button onclick="insertImage()">Image</button></li>
      <li><button onclick="insertTable()">Table</button></li>
      <li><button onclick="insertLink()">Link</button></li>
    </menu>
  </li>
  <li>
    <button onclick="formatText()">Format</button>
    <menu class="submenu">
      <li><button onclick="changeFont()">Font</button></li>
      <li><button onclick="changeSize()">Size</button></li>
      <li><button onclick="changeColor()">Color</button></li>
    </menu>
  </li>
</menu>

<style>
.nested-menu {
  display: flex;
  gap: 8px;
  list-style: none;
  padding: 0;
  margin: 0;
  position: relative;
}

.nested-menu > li {
  position: relative;
}

.nested-menu button {
  padding: 8px 16px;
  border: 1px solid #ccc;
  background: white;
  cursor: pointer;
}

.submenu {
  position: absolute;
  top: 100%;
  left: 0;
  background: white;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  padding: 4px 0;
  min-width: 120px;
  display: none;
  list-style: none;
  z-index: 100;
}

.nested-menu > li:hover .submenu {
  display: block;
}

.submenu button {
  width: 100%;
  border: none;
  border-radius: 0;
  text-align: left;
}

.submenu button:hover {
  background: #f0f0f0;
}
</style>
```

**Application command palette:**
```html
<menu type="toolbar" class="command-palette" aria-label="Application commands">
  <li>
    <button onclick="showFileMenu()" aria-haspopup="true">
      File
      <span aria-hidden="true">▼</span>
    </button>
  </li>
  <li>
    <button onclick="showEditMenu()" aria-haspopup="true">
      Edit
      <span aria-hidden="true">▼</span>
    </button>
  </li>
  <li>
    <button onclick="showViewMenu()" aria-haspopup="true">
      View
      <span aria-hidden="true">▼</span>
    </button>
  </li>
  <li>
    <button onclick="showHelpMenu()" aria-haspopup="true">
      Help
      <span aria-hidden="true">▼</span>
    </button>
  </li>
</menu>

<style>
.command-palette {
  display: flex;
  background: #2c3e50;
  padding: 0;
  margin: 0;
  list-style: none;
}

.command-palette button {
  background: none;
  border: none;
  color: white;
  padding: 12px 20px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 4px;
}

.command-palette button:hover {
  background: #34495e;
}

.command-palette button:focus {
  outline: 2px solid #3498db;
  outline-offset: -2px;
}
</style>
```

**Responsive mobile menu:**
```html
<menu type="toolbar" class="mobile-actions" aria-label="Mobile actions">
  <li>
    <button type="button" class="action-btn" onclick="callNumber()" aria-label="Call">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
        <path d="M20 15.5c-1.25 0-2.45-.2-3.57-.57-.35-.11-.74-.03-1.02.24l-2.2 2.2c-2.83-1.44-5.15-3.75-6.59-6.59l2.2-2.21c.28-.26.36-.65.25-1C8.7 6.45 8.5 5.25 8.5 4c0-.55-.45-1-1-1H4c-.55 0-1 .45-1 1 0 9.39 7.61 17 17 17 .55 0 1-.45 1-1v-3.5c0-.55-.45-1-1-1zM12 3v10l3-3h6V3h-9z"/>
      </svg>
    </button>
  </li>
  <li>
    <button type="button" class="action-btn" onclick="sendMessage()" aria-label="Message">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
        <path d="M20 2H4c-1.1 0-1.99.9-1.99 2L2 22l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm-2 12H6v-2h12v2zm0-3H6V9h12v2zm0-3H6V6h12v2z"/>
      </svg>
    </button>
  </li>
  <li>
    <button type="button" class="action-btn" onclick="shareContact()" aria-label="Share">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
        <path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92 1.61 0 2.92-1.31 2.92-2.92s-1.31-2.92-2.92-2.92z"/>
      </svg>
    </button>
  </li>
</menu>

<style>
.mobile-actions {
  display: flex;
  justify-content: space-around;
  list-style: none;
  padding: 16px;
  margin: 0;
  background: #f8f9fa;
  border-top: 1px solid #dee2e6;
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
}

.action-btn {
  background: none;
  border: none;
  padding: 12px;
  border-radius: 50%;
  background: #007bff;
  color: white;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.action-btn:active {
  background: #0056b3;
  transform: scale(0.95);
}

@media (min-width: 768px) {
  .mobile-actions {
    display: none;
  }
}
</style>
```

**Menu with state management:**
```html
<menu type="toolbar" class="stateful-menu" aria-label="Document state controls">
  <li>
    <button type="button" 
            onclick="toggleBold()" 
            aria-pressed="false"
            data-state="bold"
            class="state-btn">
      Bold
    </button>
  </li>
  <li>
    <button type="button" 
            onclick="toggleItalic()" 
            aria-pressed="false"
            data-state="italic"
            class="state-btn">
      Italic
    </button>
  </li>
  <li>
    <button type="button" 
            onclick="toggleUnderline()" 
            aria-pressed="false"
            data-state="underline"
            class="state-btn">
      Underline
    </button>
  </li>
  <li>
    <select onchange="changeFontSize(this.value)" aria-label="Font size">
      <option value="12">12px</option>
      <option value="14">14px</option>
      <option value="16">16px</option>
      <option value="18">18px</option>
      <option value="24">24px</option>
    </select>
  </li>
</menu>

<script>
function toggleBold() {
  const button = document.querySelector('[data-state="bold"]');
  const isPressed = button.getAttribute('aria-pressed') === 'true';
  button.setAttribute('aria-pressed', !isPressed);
  // Implement bold formatting logic
}

function toggleItalic() {
  const button = document.querySelector('[data-state="italic"]');
  const isPressed = button.getAttribute('aria-pressed') === 'true';
  button.setAttribute('aria-pressed', !isPressed);
  // Implement italic formatting logic
}

function toggleUnderline() {
  const button = document.querySelector('[data-state="underline"]');
  const isPressed = button.getAttribute('aria-pressed') === 'true';
  button.setAttribute('aria-pressed', !isPressed);
  // Implement underline formatting logic
}

function changeFontSize(size) {
  // Implement font size change logic
  console.log('Font size changed to:', size);
}
</script>

<style>
.stateful-menu {
  display: flex;
  gap: 8px;
  list-style: none;
  padding: 12px;
  margin: 0;
  background: #f8f9fa;
  border: 1px solid #dee2e6;
  border-radius: 6px;
  align-items: center;
}

.state-btn {
  padding: 8px 16px;
  border: 1px solid #6c757d;
  background: white;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.2s;
}

.state-btn[aria-pressed="true"] {
  background: #007bff;
  color: white;
  border-color: #007bff;
}

.stateful-menu select {
  padding: 8px;
  border: 1px solid #6c757d;
  border-radius: 4px;
  background: white;
}
</style>
```

---

## Notes

* **Specification evolution**:
  - HTML4: Intended for list menus (largely unused)
  - HTML5: Repurposed for command menus and toolbars
  - Current: Focus on interactive command groupings

* **Browser support**: 
  - Well supported in modern browsers
  - Limited semantic value without proper ARIA attributes
  - Visual styling similar to `<ul>` by default

* **Accessibility considerations**:
  - Use `aria-label` or `aria-labelledby` to provide context
  - Implement proper keyboard navigation for interactive menus
  - Use `aria-pressed` for toggle buttons
  - Provide focus management for context menus
  - Consider screen reader announcements for dynamic menus

* **Common mistakes**:
  - Using for navigation menus (use `<nav>` instead)
  - Not providing accessible labels
  - Forgetting to implement keyboard support
  - Using without proper interactive content
  - Confusing with deprecated HTML4 usage

* **Best practices**:
  - Use for genuine command and control interfaces
  - Implement proper keyboard navigation patterns
  - Provide visual feedback for interactive states
  - Use ARIA roles and attributes appropriately
  - Test with screen readers and keyboard-only users

* **Alternative approaches**:
  - Use `<nav>` for site navigation menus
  - Use `<ul>` for simple lists without interactive controls
  - Use `<div>` with ARIA roles for custom menu implementations
  - Use native `<select>` for simple option selection

* **Progressive enhancement**:
  - Ensure menus work without JavaScript where possible
  - Provide fallbacks for complex interactive features
  - Consider mobile touch interactions
  - Test across different input methods

* **Performance considerations**:
  - Complex nested menus can impact rendering performance
  - Dynamic menu creation should be optimized
  - Consider lazy loading for large menu structures
  - Monitor memory usage with many interactive elements

---
