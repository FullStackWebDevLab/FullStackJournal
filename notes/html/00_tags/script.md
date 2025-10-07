# `<script>`

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

The `<script>` tag embeds or references executable code within an HTML document, primarily JavaScript, enabling dynamic behavior, interactivity, and programmatic manipulation of document content. This element serves as the primary mechanism for adding client-side scripting capabilities to web pages, supporting both embedded code and external script resources.

---

## Syntax and Variants

+ The `<script>` tag typically requires both an opening `<script>` and closing `</script>` tag when containing inline code.
+ When using the `src` attribute to reference an external script, the element is technically not void but should not contain content (except in specific legacy cases).
+ Self-closing syntax (`<script />`) is invalid in HTML and should not be used.

---

## Attributes

The `<script>` tag supports several attributes that control its loading and execution behavior:

**`src`**  
Specifies the URL of an external script file. When present, the element should be empty (no inline code between tags). The URL can be absolute or relative, and same-origin or cross-origin (subject to CORS policies).

**`type`**  
Specifies the MIME type of the script. Common values include:
- `text/javascript` (default, though modern browsers assume JavaScript regardless)
- `module`: Treats the script as an ES6 module
- `importmap`: Specifies an import map for module resolution
- Other non-JavaScript types for data blocks or custom script types

**`async`**  
Boolean attribute that indicates the script should be executed asynchronously as soon as it is available, without blocking HTML parsing. Only valid for external scripts.

**`defer`**  
Boolean attribute that indicates the script should be executed after the document has been parsed, but before `DOMContentLoaded`. Only valid for external scripts.

**`crossorigin`**  
Configures CORS requests for external scripts. Values include:
- `anonymous`: No credentials sent
- `use-credentials`: Credentials sent
- No value: Same as `anonymous`

**`integrity`**  
Contains a cryptographic hash of the script resource for subresource integrity verification. Format: `algorithm-hash` (e.g., `sha384-abc123...`).

**`nomodule`**  
Boolean attribute that prevents the script from executing in browsers that support ES6 modules. Used for providing fallbacks to legacy browsers.

**`referrerpolicy`**  
Specifies which referrer to send when fetching the script. Values include `no-referrer`, `origin`, `same-origin`, etc.

**`nonce`**  
Cryptographic nonce used for Content Security Policy (CSP) to allow specific inline scripts.

**Global Attributes:**  
The `<script>` tag supports all global attributes including `id`, `class`, `data-*`, and `aria-*` attributes. The `id` attribute is particularly useful for script identification and manipulation.

---

## Content Model

The `<script>` element can contain **script content** (typically JavaScript code) or be **empty** when using the `src` attribute. The content model follows these rules:

- When containing inline code: contains text content that is executed as JavaScript
- When using `src`: should be empty (though some browsers tolerate content for legacy reasons)
- For non-JavaScript types (`type="module"`, etc.): content follows the specified language syntax
- HTML comments within script content were historically used to hide code from old browsers but are now unnecessary

**Restrictions:**
- Cannot contain HTML elements (only text content)
- Script content is processed by the JavaScript engine, not the HTML parser
- For module scripts, content must be valid JavaScript module syntax
- When using `src`, any inline content is ignored (except in some legacy cases)

---

## Context

+ **Placement**: Can be placed in both the `<head>` and `<body>` sections of the HTML document.
+ **Traditional Placement**: Historically in `<head>`, but modern practice often places scripts at the end of `<body>` for performance
+ **Module Scripts**: Typically placed in `<head>` with `type="module"` as they are deferred by default
+ **Usage Limits**:

  - Multiple `<script>` elements are permitted and executed in document order
  - The `async` and `defer` attributes affect execution timing but not order guarantees
  - Module scripts are automatically deferred and follow dependency order

---

## Behavior and Semantics

+ **Rendering**: The `<script>` tag itself has **no visual representation** in the browser window .
+ **Parsing Behavior**: By default, scripts are **parser-blocking**; HTML parsing pauses while the script is fetched and executed
+ **Execution Timing**: Varies based on attributes:

  - No attributes: Fetch and execute immediately, blocking parsing
  - `async`: Fetch asynchronously, execute immediately when available
  - `defer`: Fetch asynchronously, execute after parsing completes
  - `type="module"`: Deferred by default, can use `async` for different behavior

+ **Semantic Impact**:

  - **Interactivity**: Enables dynamic content updates and user interaction handling
  - **Performance**: Script loading and execution significantly impact page load performance
  - **Security**: Subject to same-origin policy and CSP restrictions
  - **Accessibility**: Can enhance or degrade accessibility depending on implementation

---

## Examples

### Basic Example: Inline and External Scripts

This example shows both inline JavaScript and external script references.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Basic Script Examples</title>
    <!-- Inline script -->
    <script>
        console.log('Inline script executed');
        
        function greetUser() {
            alert('Hello from inline script!');
        }
    </script>
    
    <!-- External script -->
    <script src="app.js"></script>
</head>
<body>
    <button onclick="greetUser()">Click Me</button>
    
    <!-- Script at end of body for better performance -->
    <script>
        console.log('DOM is ready to be manipulated');
    </script>
</body>
</html>
```

### Intermediate Example: Async, Defer, and Module Scripts

This example demonstrates different loading strategies and modern module usage.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Advanced Loading Strategies</title>
    
    <!-- Regular script (blocks parsing) -->
    <script src="analytics.js"></script>
    
    <!-- Async script (executes when available, order not guaranteed) -->
    <script src="widget.js" async></script>
    
    <!-- Deferred script (executes after parsing, in order) -->
    <script src="main.js" defer></script>
    
    <!-- ES6 Module (deferred by default) -->
    <script type="module">
        import { utils } from './utils.js';
        utils.initialize();
    </script>
    
    <!-- Module with fallback for older browsers -->
    <script type="module" src="modern-app.js"></script>
    <script nomodule src="legacy-app.js"></script>
</head>
<body>
    <div id="app">Content loaded with various script strategies</div>
</body>
</html>
```

### Advanced Example: Security and Performance Features

This example shows security considerations and advanced attributes.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Security and Performance</title>
    
    <!-- External script with integrity check -->
    <script 
        src="https://cdn.example.com/library.js"
        integrity="sha384-abc123def456..."
        crossorigin="anonymous">
    </script>
    
    <!-- Inline script with CSP nonce -->
    <script nonce="xyz789">
        const apiKey = 'secret-value';
        // This script is allowed by CSP
    </script>
    
    <!-- Module with import map -->
    <script type="importmap">
    {
        "imports": {
            "lodash": "/node_modules/lodash-es/lodash.js"
        }
    }
    </script>
    
    <!-- Dynamic import for code splitting -->
    <script type="module">
        const loadFeature = async () => {
            const feature = await import('./heavy-feature.js');
            feature.initialize();
        };
        
        // Load only when needed
        document.getElementById('load-feature').addEventListener('click', loadFeature);
    </script>
</head>
<body>
    <button id="load-feature">Load Heavy Feature</button>
</body>
</html>
```

### Specialized Example: Error Handling and Dynamic Scripts

This example demonstrates error handling and programmatic script injection.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Error Handling and Dynamic Scripts</title>
</head>
<body>
    <div id="status">Loading...</div>
    
    <!-- Script with error handling -->
    <script>
        try {
            // Code that might throw errors
            undefinedFunction();
        } catch (error) {
            console.error('Script error:', error);
            document.getElementById('status').textContent = 'Error loading script';
        }
    </script>
    
    <!-- Dynamically injected script -->
    <script>
        function loadScript(src, callback) {
            const script = document.createElement('script');
            script.src = src;
            script.onload = () => callback(null, script);
            script.onerror = () => callback(new Error(`Script load error: ${src}`), script);
            document.head.appendChild(script);
        }
        
        // Load script dynamically
        loadScript('dynamic-component.js', (error, script) => {
            if (error) {
                console.error('Failed to load dynamic script:', error);
            } else {
                console.log('Dynamic script loaded successfully');
            }
        });
    </script>
    
    <!-- JSON-LD structured data (non-executable script) -->
    <script type="application/ld+json">
    {
        "@context": "https://schema.org",
        "@type": "WebPage",
        "name": "Example Page",
        "description": "A page with various script examples"
    }
    </script>
</body>
</html>
```

---

## Notes

* **Historical Context**: 

  - The `language` attribute (e.g., `language="javascript"`) is obsolete and should not be used
  - HTML comments within scripts (`<!-- //-->`) were needed for very old browsers but are now unnecessary
  - The `type` attribute defaulted to `text/javascript` in HTML4 but is optional in HTML5

* **Performance Implications**:

  - Scripts without `async` or `defer` block HTML parsing, potentially significantly delaying page rendering
  - Multiple synchronous scripts create a "waterfall" loading effect
  - Large inline scripts can delay first paint and increase main thread workload
  - Dynamic script injection can be used for performance optimization but complicates dependency management

* **Security Considerations**:

  - The `integrity` attribute protects against CDN compromise and malicious script injection
  - CSP with `nonce` or `hash` prevents unauthorized inline script execution
  - Cross-origin scripts require proper CORS configuration for error logging
  - Dynamic script injection can bypass some CSP restrictions if not properly configured

* **Common Pitfalls**:

  - Assuming `async` scripts execute in load order (they execute in completion order)
  - Placing script references before the elements they try to manipulate
  - Forgetting that module scripts have different scoping and CORS requirements
  - Using deprecated attributes like `language` or XML-style self-closing syntax

* **Browser Quirks**:

  - Legacy browsers have different parsing behavior for script content
  - Module support varies across browsers (though widely supported in modern browsers)
  - Error handling in dynamic scripts may report differently across browsers
  - Some browsers may execute script content even when `type` is unrecognized

* **Best Practices**:

  - Use `defer` for scripts that don't need immediate execution
  - Use `async` for independent scripts like analytics
  - Place non-critical scripts at the end of the body
  - Use modules for modern JavaScript applications
  - Implement proper error handling for dynamic script loading
  - Use Subresource Integrity for third-party scripts
  - Configure appropriate CORS policies for cross-origin resources

---
