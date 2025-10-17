# `<pre>`

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

The `<pre>` element represents preformatted text that should be presented exactly as written in the HTML file. It preserves both spaces and line breaks, maintaining the original formatting of the text content. This element is essential for displaying code blocks, ASCII art, formatted text, or any content where whitespace and line breaks are semantically significant.

---

## Syntax & Variants

+ **Standard syntax**: `<pre>...</pre>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain text and limited inline elements
+ **No self-closing variant**: Must contain content
+ **No alternative forms**: Standard syntax only

---

## Attributes

+ **Core attributes**:
  - `cols` (optional, deprecated): Suggested visible width in characters
  - `width` (optional, deprecated): Suggested visible width
  - `wrap` (non-standard): Hint for line wrapping behavior

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, `lang`, `dir`, etc.

+ **Event handlers**: All global event attributes supported

---

## Content Model

+ **Permitted content**: Phrasing content, but with significant restrictions
+ **Allowed content**:
  - Text and character references (including whitespace)
  - Limited inline elements: `<code>`, `<span>`, `<strong>`, `<em>`, etc.
  - Character entities and special characters
+ **Restricted content**:
  - Most interactive elements are not permitted
  - Block-level elements are not allowed
  - Images and other replaced content should be avoided
+ **Whitespace handling**: All whitespace is preserved exactly as written

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<body>` for standalone preformatted content
  - Within `<article>`, `<section>`, or `<div>` for contextual code examples
  - Within `<figure>` for captioned code blocks
  - In documentation, tutorials, and technical content
+ **Nesting relationships**:
  - Can contain text and limited phrasing content
  - Often nested with `<code>` for code examples
  - Can be contained within most block-level elements

---

## Behavior and Semantics

+ **Default display**: Block-level element
+ **Default styling**:
  - `display: block`
  - `white-space: pre` (preserves spaces and line breaks)
  - `font-family: monospace` (most browsers)
  - `margin: 1em 0` (typical browser default)
  - Often has additional browser-specific padding and borders
+ **Semantic meaning**:
  - Indicates preformatted text where formatting is meaningful
  - Represents content that should be rendered as originally structured
  - Signals that whitespace and line breaks are intentional
+ **Accessibility role**:
  - Implicit ARIA role: `generic`
  - Screen readers may announce as "preformatted text"
  - Important to provide context for non-visual users
+ **SEO significance**: Helps search engines identify code examples and formatted content

---

## Examples

**Basic preformatted text:**
```html
<pre>
This    text   preserves
all   spaces    and
line     breaks
exactly as written.
</pre>
```

**Code block with syntax:**
```html
<pre><code>
function calculateTotal(items) {
  return items.reduce((sum, item) => {
    return sum + item.price * item.quantity;
  }, 0);
}

const cart = [
  { name: "Book", price: 15.99, quantity: 2 },
  { name: "Pen", price: 1.49, quantity: 5 }
];

console.log(calculateTotal(cart));
</code></pre>
```

**ASCII art preservation:**
```html
<pre>
   _____
  /     \
 | () () |
  \  ^  /
   |||||
   |||||
</pre>
```

**Formatted data display:**
```html
<pre>
NAME               AGE    DEPARTMENT    SALARY
John Smith         32     Engineering   85,000
Sarah Johnson      28     Marketing     72,000
Michael Chen       45     Executive     120,000
Emily Davis        29     Engineering   78,000
</pre>
```

**Styled code block with line numbers:**
```html
<div class="code-block">
  <header class="code-header">
    <span class="code-title">example.js</span>
    <button class="copy-button">Copy</button>
  </header>
  <pre class="line-numbers"><code>
function fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}

function memoizedFibonacci() {
  const cache = {};
  return function fib(n) {
    if (n in cache) return cache[n];
    if (n <= 1) return n;
    cache[n] = fib(n - 1) + fib(n - 2);
    return cache[n];
  };
}
  </code></pre>
</div>

<style>
.code-block {
  background: #2d2d2d;
  border-radius: 8px;
  overflow: hidden;
  margin: 1.5rem 0;
}

.code-header {
  background: #1a1a1a;
  padding: 12px 16px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid #444;
}

.code-title {
  color: #e6e6e6;
  font-weight: 600;
  font-family: system-ui, sans-serif;
}

.copy-button {
  background: #4a5568;
  color: white;
  border: none;
  padding: 6px 12px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 0.875rem;
}

.copy-button:hover {
  background: #2d3748;
}

.line-numbers {
  color: #e6e6e6;
  background: #2d2d2d;
  padding: 16px;
  margin: 0;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 14px;
  line-height: 1.5;
  overflow-x: auto;
}

.line-numbers code {
  display: block;
  counter-reset: line;
}

.line-numbers code::before {
  content: counter(line);
  counter-increment: line;
  display: inline-block;
  width: 2em;
  margin-right: 1em;
  color: #666;
  text-align: right;
}
</style>
```

**Command line output:**
```html
<pre class="terminal">
<span class="prompt">$</span> git status
<span class="output">On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add &lt;file&gt;..." to update what will be committed)
  (use "git restore &lt;file&gt;..." to discard changes in working directory)
    <span class="modified">modified:   src/index.js</span>
    <span class="modified">modified:   package.json</span>

Untracked files:
  (use "git add &lt;file&gt;..." to include in what will be committed)
    <span class="untracked">new-file.txt</span>

no changes added to commit (use "git add" and/or "git commit -a")</span>
</pre>

<style>
.terminal {
  background: #1a1a1a;
  color: #e6e6e6;
  padding: 16px;
  border-radius: 6px;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 14px;
  line-height: 1.4;
  overflow-x: auto;
}

.prompt {
  color: #00ff00;
  font-weight: bold;
}

.output {
  color: #e6e6e6;
}

.modified {
  color: #ffa500;
}

.untracked {
  color: #87ceeb;
}
</style>
```

**Configuration file example:**
```html
<pre class="config-file">
<span class="comment"># Database configuration</span>
<span class="section">[database]</span>
host = <span class="value">localhost</span>
port = <span class="value">5432</span>
name = <span class="value">myapp_db</span>
user = <span class="value">app_user</span>
password = <span class="value">secret_password</span>

<span class="comment"># Application settings</span>
<span class="section">[app]</span>
debug = <span class="value">false</span>
port = <span class="value">3000</span>
log_level = <span class="value">info</span>

<span class="comment"># Cache configuration</span>
<span class="section">[cache]</span>
enabled = <span class="value">true</span>
ttl = <span class="value">3600</span>
</pre>

<style>
.config-file {
  background: #f8f9fa;
  border: 1px solid #e9ecef;
  border-left: 4px solid #6f42c1;
  padding: 16px;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 14px;
  line-height: 1.4;
  overflow-x: auto;
}

.comment {
  color: #6a737d;
  font-style: italic;
}

.section {
  color: #d73a49;
  font-weight: bold;
}

.value {
  color: #032f62;
}

.config-file .section,
.config-file .comment {
  display: block;
  margin-top: 8px;
}
</style>
```

**Responsive code block with syntax highlighting:**
```html
<figure class="code-figure">
  <figcaption>CSS Grid Layout Example</figcaption>
  <pre class="syntax-highlight"><code>
<span class="comment">/* Grid container */</span>
<span class="selector">.grid-container</span> {
  <span class="property">display</span>: <span class="value">grid</span>;
  <span class="property">grid-template-columns</span>: <span class="value">repeat(auto-fit, minmax(250px, 1fr))</span>;
  <span class="property">gap</span>: <span class="value">20px</span>;
  <span class="property">padding</span>: <span class="value">20px</span>;
}

<span class="comment">/* Grid items */</span>
<span class="selector">.grid-item</span> {
  <span class="property">background</span>: <span class="value">#fff</span>;
  <span class="property">border</span>: <span class="value">1px solid #ddd</span>;
  <span class="property">border-radius</span>: <span class="value">8px</span>;
  <span class="property">padding</span>: <span class="value">20px</span>;
  <span class="property">box-shadow</span>: <span class="value">0 2px 4px rgba(0,0,0,0.1)</span>;
}

<span class="comment">/* Responsive adjustments */</span>
<span class="keyword">@media</span> (<span class="property">max-width</span>: <span class="value">768px</span>) {
  <span class="selector">.grid-container</span> {
    <span class="property">grid-template-columns</span>: <span class="value">1fr</span>;
    <span class="property">gap</span>: <span class="value">10px</span>;
  }
}
  </code></pre>
</figure>

<style>
.code-figure {
  margin: 2rem 0;
  background: #f6f8fa;
  border: 1px solid #e1e4e8;
  border-radius: 6px;
  overflow: hidden;
}

.code-figure figcaption {
  background: #f1f3f4;
  padding: 12px 16px;
  font-weight: 600;
  color: #1a1a1a;
  border-bottom: 1px solid #e1e4e8;
  font-family: system-ui, sans-serif;
}

.syntax-highlight {
  background: white;
  padding: 16px;
  margin: 0;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 14px;
  line-height: 1.5;
  overflow-x: auto;
}

.selector {
  color: #d73a49;
}

.property {
  color: #6f42c1;
}

.value {
  color: #032f62;
}

.comment {
  color: #6a737d;
  font-style: italic;
}

.keyword {
  color: #d73a49;
  font-weight: bold;
}

@media (max-width: 768px) {
  .syntax-highlight {
    font-size: 12px;
    padding: 12px;
  }
}
</style>
```

**JSON data display:**
```html
<pre class="json-display">
{
  <span class="json-key">"user"</span>: {
    <span class="json-key">"id"</span>: <span class="json-number">12345</span>,
    <span class="json-key">"name"</span>: <span class="json-string">"John Doe"</span>,
    <span class="json-key">"email"</span>: <span class="json-string">"john.doe@example.com"</span>,
    <span class="json-key">"preferences"</span>: {
      <span class="json-key">"theme"</span>: <span class="json-string">"dark"</span>,
      <span class="json-key">"notifications"</span>: <span class="json-boolean">true</span>,
      <span class="json-key">"language"</span>: <span class="json-string">"en-US"</span>
    }
  },
  <span class="json-key">"orders"</span>: [
    {
      <span class="json-key">"orderId"</span>: <span class="json-string">"ORD-001"</span>,
      <span class="json-key">"total"</span>: <span class="json-number">99.99</span>,
      <span class="json-key">"status"</span>: <span class="json-string">"completed"</span>
    },
    {
      <span class="json-key">"orderId"</span>: <span class="json-string">"ORD-002"</span>,
      <span class="json-key">"total"</span>: <span class="json-number">149.50</span>,
      <span class="json-key">"status"</span>: <span class="json-string">"pending"</span>
    }
  ]
}
</pre>

<style>
.json-display {
  background: #1e1e1e;
  color: #d4d4d4;
  padding: 20px;
  border-radius: 8px;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 14px;
  line-height: 1.4;
  overflow-x: auto;
}

.json-key {
  color: #9cdcfe;
}

.json-string {
  color: #ce9178;
}

.json-number {
  color: #b5cea8;
}

.json-boolean {
  color: #569cd6;
}
</style>
```

**SQL query example:**
```html
<pre class="sql-query">
<span class="sql-keyword">SELECT</span> 
    customers.customer_name,
    orders.order_date,
    orders.total_amount,
    products.product_name,
    order_items.quantity
<span class="sql-keyword">FROM</span> customers
<span class="sql-keyword">INNER JOIN</span> orders 
    <span class="sql-keyword">ON</span> customers.customer_id = orders.customer_id
<span class="sql-keyword">INNER JOIN</span> order_items 
    <span class="sql-keyword">ON</span> orders.order_id = order_items.order_id
<span class="sql-keyword">INNER JOIN</span> products 
    <span class="sql-keyword">ON</span> order_items.product_id = products.product_id
<span class="sql-keyword">WHERE</span> orders.order_date >= <span class="sql-string">'2024-01-01'</span>
    <span class="sql-keyword">AND</span> orders.total_amount > <span class="sql-number">1000</span>
<span class="sql-keyword">ORDER BY</span> 
    orders.order_date <span class="sql-keyword">DESC</span>,
    orders.total_amount <span class="sql-keyword">DESC</span>;
</pre>

<style>
.sql-query {
  background: #f8f9fa;
  border: 1px solid #e9ecef;
  border-left: 4px solid #007bff;
  padding: 20px;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 14px;
  line-height: 1.5;
  overflow-x: auto;
}

.sql-keyword {
  color: #d73a49;
  font-weight: bold;
}

.sql-string {
  color: #032f62;
}

.sql-number {
  color: #005cc5;
}
</style>
```

**Accessible pre block with ARIA attributes:**
```html
<div class="accessible-code">
  <div class="code-actions">
    <button 
      aria-label="Copy code to clipboard"
      onclick="copyCode(this)"
      class="copy-btn">
      Copy
    </button>
    <span class="language-label">JavaScript</span>
  </div>
  
  <pre 
    role="code"
    aria-label="JavaScript function example"
    tabindex="0"
    class="focusable-code">
function debounce(func, wait, immediate) {
  let timeout;
  return function executedFunction(...args) {
    const later = () => {
      timeout = null;
      if (!immediate) func(...args);
    };
    const callNow = immediate && !timeout;
    clearTimeout(timeout);
    timeout = setTimeout(later, wait);
    if (callNow) func(...args);
  };
}
  </pre>
</div>

<style>
.accessible-code {
  background: #2d2d2d;
  border-radius: 8px;
  overflow: hidden;
  margin: 1.5rem 0;
}

.code-actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 16px;
  background: #1a1a1a;
  border-bottom: 1px solid #444;
}

.copy-btn {
  background: #4a5568;
  color: white;
  border: none;
  padding: 6px 12px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 0.875rem;
}

.copy-btn:hover {
  background: #2d3748;
}

.language-label {
  color: #a0aec0;
  font-size: 0.875rem;
  font-family: system-ui, sans-serif;
}

.focusable-code {
  color: #e6e6e6;
  background: #2d2d2d;
  padding: 20px;
  margin: 0;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 14px;
  line-height: 1.5;
  overflow-x: auto;
  outline: none;
}

.focusable-code:focus {
  box-shadow: 0 0 0 2px #4299e1;
}

@media (prefers-reduced-motion: no-preference) {
  .copy-btn {
    transition: background-color 0.2s ease;
  }
}
</style>

<script>
function copyCode(button) {
  const pre = button.closest('.accessible-code').querySelector('pre');
  const text = pre.textContent;
  
  navigator.clipboard.writeText(text).then(() => {
    const originalText = button.textContent;
    button.textContent = 'Copied!';
    button.style.background = '#38a169';
    
    setTimeout(() => {
      button.textContent = originalText;
      button.style.background = '';
    }, 2000);
  });
}
</script>
```

**Inline code within paragraphs:**
```html
<article>
  <h1>Using the &lt;pre&gt; Element</h1>
  
  <p>
    The <code>&lt;pre&gt;</code> element is essential for displaying code snippets
    and preformatted text. For example, to create a basic HTML structure:
  </p>
  
  <pre><code>&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;title&gt;Document&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;h1&gt;Hello World&lt;/h1&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>
  
  <p>
    Notice how the indentation and line breaks are preserved exactly as written.
    This makes the <code>&lt;pre&gt;</code> element perfect for code examples,
    configuration files, and any content where formatting matters.
  </p>
</article>

<style>
article {
  max-width: 800px;
  margin: 0 auto;
  line-height: 1.6;
}

code {
  background: #f1f3f4;
  padding: 2px 6px;
  border-radius: 3px;
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 0.9em;
}

pre code {
  background: none;
  padding: 0;
  border-radius: 0;
}
</style>
```

---

## Notes

* **Whitespace preservation**: All spaces, tabs, and line breaks are preserved exactly as written
* **Character entities**: Special characters may need to be escaped (`<` as `&lt;`, `>` as `&gt;`, `&` as `&amp;`)
* **Accessibility considerations**:
  - Provide context for screen reader users with `aria-label` or surrounding text
  - Consider using `<code>` inside `<pre>` for code examples
  - Ensure sufficient color contrast for syntax highlighting
  - Make code blocks focusable and navigable for keyboard users
* **Browser support**: Universally supported across all browsers
* **Common misuse**:
  - Using for general text layout (use CSS instead)
  - Including interactive elements inside `<pre>`
  - Forgetting to escape special HTML characters
* **Responsive design**:
  - Use `overflow-x: auto` for horizontal scrolling on small screens
  - Consider responsive font sizes for code blocks
  - Test readability on mobile devices
* **Performance**: Large `<pre>` blocks can impact performance; consider virtualization for very large content
* **Best practices**:
  - Combine with `<code>` for code examples
  - Use semantic class names for styling
  - Provide copy-to-clipboard functionality for code blocks
  - Maintain accessibility with proper ARIA attributes
  - Consider line numbers for large code examples
* **Deprecated attributes**: `cols`, `width` - use CSS instead
* **CSS alternatives**: `white-space: pre` can mimic `<pre>` behavior for other elements

---
