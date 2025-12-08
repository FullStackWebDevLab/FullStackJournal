# `<code>`

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

The `<code>` element represents a fragment of computer code within content. It semantically identifies text as source code, command-line input, or other computer-readable content, distinguishing it from regular prose. This element provides both semantic meaning for assistive technologies and a foundation for consistent visual styling of code snippets in documentation, tutorials, and technical content.

---

## Syntax & Variants

+ **Standard syntax**: `<code>...</code>`
+ **Not void**: Requires both opening and closing tags
+ **Inline element**: Typically used within text flow
+ **No self-closing variant**: Must contain content between tags
+ **Block usage**: Can be wrapped in `<pre>` for multiline code blocks

---

## Attributes

+ **No specific attributes**: The `<code>` element does not have any attributes specific to its function

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Common usage**: 
  - `class` for syntax highlighting (e.g., `class="language-javascript"`)
  - `data-*` attributes for additional metadata
  - `id` for linking to specific code snippets

---

## Content Model

+ **Permitted content**: Phrasing content
+ **Allowed content**:
  - Text content (code characters)
  - Character references and entities
  - Other inline elements when necessary
+ **Restricted content**: Should not contain block-level elements
+ **Special characters**: HTML entities often needed for `<`, `>`, `&` characters

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within paragraphs (`<p>`) for inline code references
  - Inside list items (`<li>`) for command examples
  - Within table cells (`<td>`, `<th>`) for data display
  - Wrapped in `<pre>` for code blocks
  - In documentation and technical articles
+ **No usage limits**: Can be used multiple times within a document
+ **Nesting**: Can be nested within other inline elements

---

## Behavior and Semantics

+ **Default display**: Inline element
+ **Default styling**:
  - `display: inline`
  - `font-family: monospace` (typically Consolas, Monaco, monospace)
  - `font-size: 1em` (often slightly smaller than surrounding text)
  - `color: inherit` (but often styled with distinct color)
  - `background-color: transparent` (often styled with light background)
+ **Semantic meaning**:
  - Identifies text as computer code
  - Helps screen readers announce content appropriately
  - Provides context for search engines and other automated tools
+ **Accessibility**:
  - Screen readers may change voice or announce as "code"
  - Provides semantic distinction from regular text
  - Helps users understand the content type

---

## Examples

**Basic inline code:**
```html
<p>Use the <code>console.log()</code> function to output messages to the browser console.</p>
```

**Multiple code elements in context:**
```html
<p>In JavaScript, you can declare variables with <code>let</code>, 
<code>const</code>, or <code>var</code>. Use <code>const</code> for 
values that won't be reassigned.</p>
```

**HTML entities for special characters:**
```html
<p>In HTML, use <code>&lt;div&gt;</code> to create a division and 
<code>&amp;nbsp;</code> for a non-breaking space.</p>
```

**Command-line examples:**
```html
<p>To install the dependencies, run <code>npm install</code> in your project directory.</p>

<p>Common Git commands include <code>git status</code>, <code>git add .</code>, 
and <code>git commit -m "message"</code>.</p>
```

**Styled code elements:**
```html
<p>The <code class="inline-code">Array.prototype.map()</code> method 
creates a new array with the results of calling a provided function 
on every element.</p>

<style>
.inline-code {
  background-color: #f4f4f4;
  padding: 2px 6px;
  border-radius: 3px;
  border: 1px solid #ddd;
  font-family: 'Courier New', monospace;
  font-size: 0.9em;
  color: #d63384;
}
</style>
```

**Code blocks with `<pre>` and `<code>`:**
```html
<pre><code class="language-javascript">
function calculateTotal(items) {
  return items.reduce((total, item) => {
    return total + item.price * item.quantity;
  }, 0);
}
</code></pre>

<style>
pre code {
  display: block;
  padding: 16px;
  background-color: #f8f9fa;
  border: 1px solid #e9ecef;
  border-radius: 4px;
  overflow-x: auto;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 14px;
  line-height: 1.4;
}
</style>
```

**API documentation examples:**
```html
<article>
  <h2>API Reference</h2>
  
  <h3><code>fetch()</code> Method</h3>
  <p>The <code>fetch()</code> method starts the process of fetching 
  a resource from the network.</p>
  
  <h4>Syntax</h4>
  <pre><code class="language-javascript">
fetch(url, options)
  .then(response => response.json())
  .then(data => console.log(data));
  </code></pre>
  
  <h4>Parameters</h4>
  <ul>
    <li><code>url</code> - The URL to fetch</li>
    <li><code>options</code> - Optional configuration object</li>
  </ul>
</article>
```

**CSS property examples:**
```html
<p>The <code>display</code> property specifies the display behavior of an element.</p>

<pre><code class="language-css">
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 16px;
}
</code></pre>
```

**Command sequences:**
```html
<div class="terminal-demo">
  <h3>Setup Commands</h3>
  <pre><code class="language-bash">
# Clone the repository
git clone https://github.com/user/repo.git

# Navigate to project directory
cd repo

# Install dependencies
npm install

# Start development server
npm run dev
  </code></pre>
</div>

<style>
.terminal-demo pre code {
  background-color: #2d3748;
  color: #e2e8f0;
  border-radius: 6px;
  padding: 20px;
}
</style>
```

**Inline code with different languages:**
```html
<p>In Python, use <code class="python">print()</code> for output, 
while in PHP you use <code class="php">echo</code> or 
<code class="php">print()</code>.</p>

<p>SQL queries use <code class="sql">SELECT</code> statements, 
and CSS uses <code class="css">color</code> for text coloring.</p>

<style>
code.python { color: #3572A5; }
code.php { color: #4F5D95; }
code.sql { color: #e38c00; }
code.css { color: #563d7c; }
</style>
```

**Error messages and debugging:**
```html
<div class="error-example">
  <p>When you see the error:</p>
  <pre><code class="language-javascript">
TypeError: Cannot read properties of undefined (reading 'map')
    at UserList (userList.js:15:25)
    at render (app.js:8:12)
  </code></pre>
  <p>Check that your data is properly initialized before calling 
  <code>.map()</code> on it.</p>
</div>
```

**Code in data attributes:**
```html
<button onclick="executeCode(this.dataset.code)">
  Run Example
</button>

<script>
function executeCode(code) {
  eval(code);
}
</script>
```

**Accessible code examples:**
```html
<div class="code-example">
  <h4 id="code-example-1">JavaScript Function Example</h4>
  <pre aria-labelledby="code-example-1" role="region" aria-label="JavaScript code example">
<code class="language-javascript">
// Calculate factorial recursively
function factorial(n) {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
}

// Usage
console.log(factorial(5)); // Output: 120
</code>
  </pre>
  <p class="sr-only">This code example shows a recursive factorial function in JavaScript.</p>
</div>

<style>
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
</style>
```

**Interactive code examples:**
```html
<div class="interactive-code">
  <h3>Try This Code</h3>
  <pre><code id="editable-code" contenteditable="true" class="language-javascript">
// Edit this code
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(n => n * 2);
console.log(doubled);
  </code></pre>
  <button onclick="runCode()">Run Code</button>
  <div id="output"></div>
</div>

<script>
function runCode() {
  const code = document.getElementById('editable-code').textContent;
  const output = document.getElementById('output');
  
  try {
    // In a real application, use a safer execution method
    const result = eval(code);
    output.innerHTML = `<pre>Result: ${JSON.stringify(result, null, 2)}</pre>`;
  } catch (error) {
    output.innerHTML = `<pre class="error">Error: ${error.message}</pre>`;
  }
}
</script>

<style>
#editable-code {
  border: 2px solid transparent;
  outline: none;
}

#editable-code:focus {
  border-color: #007bff;
}

.error {
  color: #dc3545;
}
</style>
```

**Code with line numbers:**
```html
<div class="code-with-lines">
  <pre><code class="language-python">
def fibonacci(n):
    if n <= 0:
        return []
    elif n == 1:
        return [0]
    elif n == 2:
        return [0, 1]
    
    sequence = [0, 1]
    for i in range(2, n):
        sequence.append(sequence[i-1] + sequence[i-2])
    
    return sequence
  </code></pre>
</div>

<style>
.code-with-lines {
  position: relative;
  counter-reset: line;
}

.code-with-lines code::before {
  counter-increment: line;
  content: counter(line);
  display: inline-block;
  width: 2em;
  margin-right: 1em;
  color: #6c757d;
  text-align: right;
  user-select: none;
}
</style>
```

**Responsive code blocks:**
```html
<div class="responsive-code">
  <pre><code class="language-css">
@media (max-width: 768px) {
  .container {
    flex-direction: column;
    padding: 16px;
  }
  
  .sidebar {
    order: -1;
    margin-bottom: 20px;
  }
  
  .main-content {
    min-width: 100%;
  }
}
  </code></pre>
</div>

<style>
.responsive-code pre {
  max-width: 100%;
  overflow-x: auto;
}

.responsive-code code {
  white-space: pre;
  word-wrap: normal;
}

/* Add scrollbar styling for better UX */
.responsive-code pre::-webkit-scrollbar {
  height: 8px;
}

.responsive-code pre::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 4px;
}

.responsive-code pre::-webkit-scrollbar-thumb {
  background: #c1c1c1;
  border-radius: 4px;
}

.responsive-code pre::-webkit-scrollbar-thumb:hover {
  background: #a8a8a8;
}
</style>
```

**Syntax highlighting with classes:**
```html
<pre><code class="language-html">
&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;
    &lt;title&gt;<span class="code-title">Document Title</span>&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;h1&gt;<span class="code-content">Hello World</span>&lt;/h1&gt;
&lt;/body&gt;
&lt;/html&gt;
</code></pre>

<style>
.language-html {
  color: #e06c75; /* Default color for tags */
}

.code-title {
  color: #98c379; /* Green for content */
}

.code-content {
  color: #d19a66; /* Orange for other content */
}

/* Tag-specific colors */
.language-html .code-tag {
  color: #e06c75;
}

.language-html .code-attr {
  color: #d19a66;
}

.language-html .code-value {
  color: #98c379;
}
</style>
```

**Code in documentation with copy functionality:**
```html
<div class="code-snippet">
  <div class="code-header">
    <span>JavaScript</span>
    <button class="copy-btn" onclick="copyCode(this)">Copy</button>
  </div>
  <pre><code id="snippet-1" class="language-javascript">
// Debounce function implementation
function debounce(func, wait) {
  let timeout;
  return function executedFunction(...args) {
    const later = () => {
      clearTimeout(timeout);
      func(...args);
    };
    clearTimeout(timeout);
    timeout = setTimeout(later, wait);
  };
}
  </code></pre>
</div>

<script>
function copyCode(button) {
  const codeElement = button.parentElement.nextElementSibling.querySelector('code');
  const textArea = document.createElement('textarea');
  textArea.value = codeElement.textContent;
  document.body.appendChild(textArea);
  textArea.select();
  document.execCommand('copy');
  document.body.removeChild(textArea);
  
  // Visual feedback
  button.textContent = 'Copied!';
  setTimeout(() => {
    button.textContent = 'Copy';
  }, 2000);
}
</script>

<style>
.code-snippet {
  border: 1px solid #e1e4e8;
  border-radius: 6px;
  margin: 16px 0;
  overflow: hidden;
}

.code-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 16px;
  background-color: #f6f8fa;
  border-bottom: 1px solid #e1e4e8;
  font-size: 14px;
  font-weight: 600;
}

.copy-btn {
  background: none;
  border: 1px solid #d1d5da;
  border-radius: 4px;
  padding: 4px 8px;
  font-size: 12px;
  cursor: pointer;
}

.copy-btn:hover {
  background-color: #f3f4f6;
}

.code-snippet pre {
  margin: 0;
  padding: 16px;
  background-color: white;
  overflow-x: auto;
}
</style>
```

**Mathematical and scientific code:**
```html
<p>The quadratic formula is expressed in code as:</p>
<pre><code class="language-python">
import math

def solve_quadratic(a, b, c):
    discriminant = b**2 - 4*a*c
    if discriminant < 0:
        return None  # No real solutions
    
    sqrt_discriminant = math.sqrt(discriminant)
    x1 = (-b + sqrt_discriminant) / (2*a)
    x2 = (-b - sqrt_discriminant) / (2*a)
    
    return x1, x2
</code></pre>
```

---

## Notes

* **Semantic importance**: 
  - Provides meaningful structure for assistive technologies
  - Helps search engines understand content type
  - Distinguishes code from regular text programmatically
* **Character encoding**: 
  - Always escape `<`, `>`, and `&` characters with HTML entities
  - Use `&lt;` for `<`, `&gt;` for `>`, `&amp;` for `&`
* **Browser compatibility**: Universally supported across all browsers
* **Syntax highlighting**: 
  - Often used with classes like `language-*` for highlighters
  - Popular libraries: Prism.js, Highlight.js
  - CSS can provide basic coloring without JavaScript
* **Accessibility considerations**:
  - Screen readers may announce "code" before reading content
  - Ensure sufficient color contrast for styled code
  - Provide descriptions for complex code blocks
  - Use `aria-label` or `aria-describedby` when helpful
* **Common mistakes**:
  - Forgetting to escape special HTML characters
  - Using for non-code content (use `<samp>` or `<kbd>` instead)
  - Applying excessive styling that reduces readability
  - Using block-level elements inside inline `<code>`
* **Best practices**:
  - Use with `<pre>` for multi-line code blocks
  - Escape all special characters properly
  - Choose readable monospace fonts
  - Ensure adequate contrast for accessibility
  - Provide context for code examples
  - Use appropriate language classes for syntax highlighting
* **Performance**: 
  - Syntax highlighting can impact page load time
  - Consider server-side highlighting for large code blocks
  - Lazy-load highlighting for non-critical content
* **Mobile considerations**:
  - Ensure code blocks are horizontally scrollable on small screens
  - Use adequate font sizes for readability on mobile devices
  - Test touch interactions with interactive code examples

---
