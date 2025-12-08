# `<template>`

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

The `<template>` tag serves as a mechanism for holding client-side content that should not be rendered when the page loads but may be instantiated later during runtime using JavaScript. This element provides a native way to declare reusable HTML fragments that can be cloned and inserted into the document programmatically, offering performance benefits over string-based HTML generation and supporting inert content parsing.

---

## Syntax and Variants

+ The `<template>` tag requires both an opening `<template>` and closing `</template>` tag.
+ It is a non-void element that can contain any valid HTML content.
+ No alternative or legacy forms exist, as this is a relatively modern HTML5 addition.

---

## Attributes

The `<template>` tag supports only **global attributes** and has no specific attributes of its own:

**Global Attributes:**
- `id`, `class`: For JavaScript targeting and CSS scoping (when content is activated)
- `data-*`: For custom data attributes that can be accessed after template instantiation
- `aria-*`: For accessibility attributes that become active when content is inserted into DOM
- `style`: Though typically not useful since the template itself isn't rendered

**Important Notes:**
- No required attributes
- No specific attributes control template behavior; activation is entirely JavaScript-driven
- The `id` attribute is particularly useful for programmatic template access
- `data-*` attributes can store template configuration or metadata

---

## Content Model

The `<template>` element can contain virtually any HTML content that would be valid in the document body, with special parsing rules:

**Permitted Content:**
- Text nodes and comments
- Any flow content elements: `<div>`, `<p>`, `<section>`, `<article>`, etc.
- Any phrasing content: `<span>`, `<strong>`, `<em>`, `<a>`, etc.
- Any embedded content: `<img>`, `<video>`, `<canvas>`, `<iframe>`, etc.
- Any interactive elements: `<button>`, `<form>`, `<input>`, `<select>`, etc.
- Other `<template>` elements (nesting is allowed)
- `<script>` and `<style>` elements (with special inert behavior)

**Special Content Handling:**
- `<script>` elements within templates are not executed until the template content is activated
- `<style>` elements within templates are not applied until the template content is activated
- Images, iframes, and other external resources are not fetched until activation
- The content is parsed but not rendered, creating a "document fragment"

**Restrictions:**
- Some attributes like `src` on `<img>` or `href` on `<a>` are parsed but not acted upon until activation
- Template content cannot contain certain metadata elements that are only valid in `<head>`

---

## Context

+ **Placement**: Can be placed in both the `<head>` and `<body>` sections of the HTML document, though `<body>` is more common for content templates.
+ **Preferred Location**: Typically placed in `<body>`, often at the end for organizational purposes
+ **Head Context**: Valid but less common, useful for templates that might be used throughout the document
+ **Usage Limits**: 
  - Multiple `<template>` elements are permitted throughout the document
  - Nesting of `<template>` elements is allowed
  - No practical limit on the number of templates, though performance considerations apply for very large templates

---

## Behavior and Semantics

+ **Rendering**: The `<template>` tag and its content are **not rendered** in the browser; both the element itself and its children are invisible.
+ **Content Inertness**: The template content is considered "inert"; scripts don't run, styles don't apply, images don't load, and elements are not focusable
+ **DOM Structure**: Template content exists in a separate "document fragment" (a lightweight document-like structure) that is not part of the main document tree
+ **Default CSS**: The element itself is typically styled as `display: none` by browsers, though this is not required by specification
+ **Semantic Impact**:

  - **Performance**: Improves performance by allowing browsers to parse HTML upfront without rendering or fetching resources
  - **Maintainability**: Provides a clean separation between static content and dynamic content templates
  - **Reusability**: Enables declarative template definitions that can be instantiated multiple times
  - **Standards Compliance**: Offers a native alternative to non-standard template approaches like hidden `<div>` elements or script-based templates

---

## Examples

### Basic Example: Simple Template Usage

This example shows a basic template that creates reusable user card markup.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Basic Template Example</title>
    <style>
        .user-card {
            border: 1px solid #ccc;
            border-radius: 8px;
            padding: 16px;
            margin: 10px;
            background: #f9f9f9;
        }
        .user-name {
            font-weight: bold;
            color: #2c3e50;
        }
    </style>
</head>
<body>
    <h1>User List</h1>
    <div id="user-container"></div>

    <!-- Template definition -->
    <template id="user-card-template">
        <div class="user-card">
            <div class="user-name"></div>
            <div class="user-email"></div>
            <button class="view-profile">View Profile</button>
        </div>
    </template>

    <script>
        // Template usage
        const template = document.getElementById('user-card-template');
        const container = document.getElementById('user-container');
        
        // Sample data
        const users = [
            { name: 'John Doe', email: 'john@example.com' },
            { name: 'Jane Smith', email: 'jane@example.com' },
            { name: 'Bob Johnson', email: 'bob@example.com' }
        ];
        
        // Instantiate template for each user
        users.forEach(user => {
            // Clone template content
            const instance = template.content.cloneNode(true);
            
            // Populate with data
            instance.querySelector('.user-name').textContent = user.name;
            instance.querySelector('.user-email').textContent = user.email;
            
            // Add event listener
            instance.querySelector('.view-profile').addEventListener('click', () => {
                alert(`Viewing profile of: ${user.name}`);
            });
            
            // Append to container
            container.appendChild(instance);
        });
    </script>
</body>
</html>
```

### Intermediate Example: Complex Template with Scripts and Styles

This example demonstrates templates containing scripts, styles, and nested structures.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Advanced Template Example</title>
</head>
<body>
    <h1>Product Dashboard</h1>
    <div id="dashboard"></div>

    <!-- Complex template with internal styles and scripts -->
    <template id="product-widget-template">
        <style>
            .product-widget {
                border: 2px solid #e0e0e0;
                border-radius: 12px;
                padding: 20px;
                margin: 15px;
                background: white;
                box-shadow: 0 2px 8px rgba(0,0,0,0.1);
                transition: transform 0.2s ease;
            }
            .product-widget:hover {
                transform: translateY(-2px);
            }
            .price {
                font-size: 1.5em;
                color: #27ae60;
                font-weight: bold;
            }
        </style>
        
        <div class="product-widget">
            <h2 class="product-title"></h2>
            <p class="product-description"></p>
            <div class="price"></div>
            <button class="add-to-cart">Add to Cart</button>
            <div class="inventory-status"></div>
        </div>
        
        <script>
            // This script runs when the template is instantiated
            document.addEventListener('DOMContentLoaded', function() {
                const buttons = document.querySelectorAll('.add-to-cart');
                buttons.forEach(button => {
                    button.addEventListener('click', function() {
                        const productName = this.closest('.product-widget')
                                            .querySelector('.product-title').textContent;
                        console.log(`Added to cart: ${productName}`);
                    });
                });
            });
        </script>
    </template>

    <script>
        function createProductWidget(product) {
            const template = document.getElementById('product-widget-template');
            const instance = template.content.cloneNode(true);
            
            // Populate template
            instance.querySelector('.product-title').textContent = product.name;
            instance.querySelector('.product-description').textContent = product.description;
            instance.querySelector('.price').textContent = `$${product.price}`;
            
            // Conditional styling
            const statusElement = instance.querySelector('.inventory-status');
            if (product.inStock) {
                statusElement.textContent = 'In Stock';
                statusElement.style.color = 'green';
            } else {
                statusElement.textContent = 'Out of Stock';
                statusElement.style.color = 'red';
                instance.querySelector('.add-to-cart').disabled = true;
            }
            
            document.getElementById('dashboard').appendChild(instance);
        }
        
        // Create some product widgets
        createProductWidget({
            name: 'Laptop',
            description: 'High-performance laptop for professionals',
            price: 1299.99,
            inStock: true
        });
        
        createProductWidget({
            name: 'Wireless Mouse',
            description: 'Ergonomic wireless mouse',
            price: 49.99,
            inStock: false
        });
    </script>
</body>
</html>
```

### Advanced Example: Nested Templates and Dynamic Content

This example shows nested templates and more complex instantiation patterns.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Nested Templates Example</title>
    <style>
        .data-table { width: 100%; border-collapse: collapse; }
        .data-table th, .data-table td { border: 1px solid #ddd; padding: 8px; }
        .data-table th { background: #f5f5f5; }
        .loading { opacity: 0.6; }
    </style>
</head>
<body>
    <h1>Data Table with Templates</h1>
    <div id="app"></div>

    <!-- Main table template -->
    <template id="table-template">
        <div class="table-container">
            <table class="data-table">
                <thead>
                    <tr class="header-row"></tr>
                </thead>
                <tbody class="table-body"></tbody>
            </table>
            <div class="table-footer">
                <button class="load-more">Load More</button>
                <span class="row-count">0 rows</span>
            </div>
        </div>
    </template>

    <!-- Row template (nested usage) -->
    <template id="row-template">
        <tr class="data-row">
            <td class="cell-id"></td>
            <td class="cell-name"></td>
            <td class="cell-value"></td>
            <td class="cell-actions">
                <button class="edit-btn">Edit</button>
                <button class="delete-btn">Delete</button>
            </td>
        </tr>
    </template>

    <!-- Header cell template -->
    <template id="header-template">
        <th class="header-cell"></th>
    </template>

    <script>
        class DataTable {
            constructor(container, data) {
                this.container = container;
                this.data = data;
                this.currentPage = 0;
                this.pageSize = 5;
                this.init();
            }
            
            init() {
                // Create table structure
                const tableTemplate = document.getElementById('table-template');
                this.tableInstance = tableTemplate.content.cloneNode(true);
                
                // Create headers
                this.createHeaders();
                
                // Create initial rows
                this.renderPage();
                
                // Add event listeners
                this.tableInstance.querySelector('.load-more')
                    .addEventListener('click', () => this.loadMore());
                
                this.container.appendChild(this.tableInstance);
            }
            
            createHeaders() {
                const headerRow = this.tableInstance.querySelector('.header-row');
                const headerTemplate = document.getElementById('header-template');
                
                ['ID', 'Name', 'Value', 'Actions'].forEach(headerText => {
                    const headerInstance = headerTemplate.content.cloneNode(true);
                    headerInstance.querySelector('.header-cell').textContent = headerText;
                    headerRow.appendChild(headerInstance);
                });
            }
            
            renderPage() {
                const tableBody = this.tableInstance.querySelector('.table-body');
                const rowTemplate = document.getElementById('row-template');
                const start = this.currentPage * this.pageSize;
                const end = start + this.pageSize;
                const pageData = this.data.slice(start, end);
                
                pageData.forEach(item => {
                    const rowInstance = rowTemplate.content.cloneNode(true);
                    
                    // Populate row data
                    rowInstance.querySelector('.cell-id').textContent = item.id;
                    rowInstance.querySelector('.cell-name').textContent = item.name;
                    rowInstance.querySelector('.cell-value').textContent = item.value;
                    
                    // Add event listeners
                    rowInstance.querySelector('.edit-btn').addEventListener('click', 
                        () => this.editItem(item.id));
                    rowInstance.querySelector('.delete-btn').addEventListener('click', 
                        () => this.deleteItem(item.id));
                    
                    tableBody.appendChild(rowInstance);
                });
                
                // Update row count
                this.tableInstance.querySelector('.row-count').textContent = 
                    `${tableBody.children.length} rows`;
            }
            
            loadMore() {
                this.currentPage++;
                this.renderPage();
            }
            
            editItem(id) {
                console.log(`Editing item ${id}`);
            }
            
            deleteItem(id) {
                console.log(`Deleting item ${id}`);
            }
        }
        
        // Sample data
        const sampleData = Array.from({ length: 20 }, (_, i) => ({
            id: i + 1,
            name: `Item ${i + 1}`,
            value: Math.random() * 100
        }));
        
        // Initialize the table
        new DataTable(document.getElementById('app'), sampleData);
    </script>
</body>
</html>
```

### Specialized Example: Template with Shadow DOM

This example demonstrates using templates with Web Components and Shadow DOM.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Template with Shadow DOM</title>
</head>
<body>
    <h1>Custom Elements with Templates</h1>
    
    <user-profile name="John Doe" role="Developer" avatar="john.jpg"></user-profile>
    <user-profile name="Jane Smith" role="Designer" avatar="jane.jpg"></user-profile>

    <!-- Template for custom element -->
    <template id="user-profile-template">
        <style>
            :host {
                display: block;
                margin: 10px;
                padding: 20px;
                border: 1px solid #ddd;
                border-radius: 8px;
                font-family: Arial, sans-serif;
            }
            .avatar {
                width: 60px;
                height: 60px;
                border-radius: 50%;
                background: #f0f0f0;
                display: inline-block;
                vertical-align: middle;
                margin-right: 15px;
            }
            .info {
                display: inline-block;
                vertical-align: middle;
            }
            .name {
                font-weight: bold;
                font-size: 1.2em;
                margin: 0;
            }
            .role {
                color: #666;
                margin: 0;
            }
        </style>
        
        <div class="profile">
            <div class="avatar"></div>
            <div class="info">
                <p class="name"></p>
                <p class="role"></p>
            </div>
        </div>
    </template>

    <script>
        // Define custom element
        class UserProfile extends HTMLElement {
            static observedAttributes = ['name', 'role', 'avatar'];
            
            constructor() {
                super();
                this.attachShadow({ mode: 'open' });
            }
            
            connectedCallback() {
                const template = document.getElementById('user-profile-template');
                this.shadowRoot.appendChild(template.content.cloneNode(true));
                this.updateContent();
            }
            
            attributeChangedCallback() {
                if (this.shadowRoot) {
                    this.updateContent();
                }
            }
            
            updateContent() {
                const name = this.getAttribute('name') || 'Unknown';
                const role = this.getAttribute('role') || 'Unknown Role';
                const avatar = this.getAttribute('avatar');
                
                this.shadowRoot.querySelector('.name').textContent = name;
                this.shadowRoot.querySelector('.role').textContent = role;
                
                const avatarEl = this.shadowRoot.querySelector('.avatar');
                if (avatar) {
                    avatarEl.style.backgroundImage = `url(${avatar})`;
                    avatarEl.style.backgroundSize = 'cover';
                }
            }
        }
        
        // Register custom element
        customElements.define('user-profile', UserProfile);
    </script>
</body>
</html>
```

---

## Notes

* **Browser Support**: 

  - Modern browsers have excellent support for `<template>` elements
  - Internet Explorer 11 has partial support (may require polyfills for some advanced features)
  - Mobile browsers generally have good support in recent versions

* **Performance Benefits**:

  - Templates are parsed once during page load, avoiding repeated HTML parsing during instantiation
  - Inert content prevents unnecessary resource loading and script execution
  - Better memory management compared to hidden DOM elements
  - Improved performance over string concatenation and `innerHTML` approaches

* **Common Pitfalls**:

  - Forgetting to use `content.cloneNode(true)` to access the template content
  - Assuming template content is immediately available in the main DOM tree
  - Not understanding that scripts within templates only execute upon activation
  - Using templates for very small fragments where string templates might be simpler
  - Overlooking the need to manage event listeners when cloning templates multiple times

* **Alternative Approaches**:

  - **String templates**: Using template literals in JavaScript
  - **Hidden elements**: Using `display: none` or `hidden` attribute (less performant)
  - **Document fragments**: Creating fragments programmatically without `<template>`
  - **Framework templates**: Using React, Vue, Angular, or other framework templating systems

* **Best Practices**:

  - Use templates for complex, reusable HTML structures
  - Prefer templates over string concatenation for better maintainability and security
  - Use `id` attributes for easy template access
  - Consider using templates with Web Components for encapsulated functionality
  - Test template instantiation performance for very large or complex templates
  - Use event delegation when possible to manage events in template instances

* **Security Considerations**:

  - Template content is inherently safer than `innerHTML` with user-provided strings
  - Still requires proper data sanitization when inserting user content
  - Scripts in templates execute with the same privileges as regular scripts
  - Consider Content Security Policy (CSP) for scripts within templates

---
