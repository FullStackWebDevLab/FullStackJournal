# `<mark>`

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

The `<mark>` element represents text that is highlighted or marked for reference purposes due to its relevance in a particular context. It functions as a highlighter pen for text, drawing attention to specific content that is particularly pertinent to the user's current activity or search. Unlike `<strong>` which indicates importance or `<em>` which indicates emphasis, `<mark>` denotes contextual relevance without implying permanent significance.

---

## Syntax and Variants

+ **Standard syntax**: `<mark>...</mark>`
+ **Not void**: Requires both opening and closing tags
+ **Inline element**: Flows with surrounding text content
+ **No self-closing variant**: Must contain content between tags
+ **No alternative forms**: Single, consistent syntax across implementations

---

## Attributes

+ **No specific attributes**: The `<mark>` element does not have any attributes specific to its function

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Common usage**: Typically used with `class` for custom styling or `id` for JavaScript targeting

---

## Content Model

+ **Permitted content**: Phrasing content
+ **Allowed content**:
  - Text and character references
  - Other inline elements: `<span>`, `<strong>`, `<em>`, `<a>`, etc.
  - Images and other phrasing content
+ **Restricted content**: Cannot contain block-level elements
+ **Text emphasis**: Primarily intended for highlighting text content

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within paragraphs (`<p>`)
  - Inside headings (`<h1>`-`<h6>`)
  - Within list items (`<li>`)
  - In table cells (`<td>`, `<th>`)
  - Within other inline contexts
+ **No usage limits**: Can be used multiple times within a document
+ **Nesting**: Can be nested within other inline elements and can contain other inline elements

---

## Behavior and Semantics

+ **Default display**: Inline element
+ **Default styling**:
  - `display: inline`
  - `background-color: yellow` (typically)
  - `color: black` (typically)
  - No inherent font weight or style changes
+ **Semantic meaning**:
  - Indicates text that is relevant in the current context
  - Represents reference highlighting, like search results
  - Denotes content that should attract user attention temporarily
  - Does not convey importance or emphasis like `<strong>` or `<em>`
+ **Accessibility**:
  - Screen readers may announce highlighted content differently
  - Provides semantic meaning for contextual relevance
  - Helps users understand why certain text is visually distinguished

---

## Examples

**Basic text highlighting:**
```html
<p>In this sentence, <mark>only these words</mark> are highlighted for emphasis.</p>
```

**Search result highlighting:**
```html
<p>Search results for "HTML5":</p>
<ul>
  <li>Learn <mark>HTML5</mark> semantic elements and their proper usage</li>
  <li>New features in <mark>HTML5</mark> that improve accessibility</li>
  <li>Migrating from HTML4 to <mark>HTML5</mark>: A complete guide</li>
</ul>
```

**Multiple highlights in context:**
```html
<article>
  <h2>Project Requirements</h2>
  <p>The new website must be <mark>fully responsive</mark> and meet 
  <mark>WCAG 2.1 AA</mark> accessibility standards. All content should 
  be delivered through a <mark>progressive web app</mark> that works 
  offline and provides native-app-like experience.</p>
</article>
```

**Styled mark elements:**
```html
<p>This is <mark class="important">important information</mark> that 
needs attention, while this is <mark class="reference">reference 
material</mark> for further reading.</p>

<style>
mark.important {
  background-color: #ffeb3b;
  color: #333;
  padding: 2px 4px;
  border-radius: 2px;
  font-weight: bold;
}

mark.reference {
  background-color: #e3f2fd;
  color: #1565c0;
  padding: 2px 4px;
  border-style: dotted;
  border-color: #1565c0;
  border-width: 1px;
}
</style>
```

**Highlighting in code documentation:**
```html
<pre><code>
function calculateTotal(items) {
  return items.reduce((total, item) => {
    <mark>return total + item.price * item.quantity;</mark>
  }, 0);
}
</code></pre>
<p>The <mark>highlighted line</mark> shows where the actual calculation occurs.</p>
```

**Quotation with highlighted key points:**
```html
<blockquote>
  <p>"The most important property of a program is whether it accomplishes 
  the intention of its user. <mark>Correctness</mark> and <mark>usability</mark> 
  should never be sacrificed for <mark>performance</mark> in the initial 
  development phases."</p>
  <footer>— Software Engineering Principles</footer>
</blockquote>
```

**Interactive highlighting with JavaScript:**
```html
<p id="highlightable">Click the button below to highlight all instances of the word "highlight" in this paragraph that demonstrates how highlighting works.</p>

<button onclick="highlightText()">Highlight "highlight"</button>
<button onclick="clearHighlights()">Clear Highlights</button>

<script>
function highlightText() {
  const paragraph = document.getElementById('highlightable');
  const text = paragraph.textContent;
  const highlighted = text.replace(/(highlight)/gi, '<mark>$1</mark>');
  paragraph.innerHTML = highlighted;
}

function clearHighlights() {
  const paragraph = document.getElementById('highlightable');
  const text = paragraph.textContent;
  paragraph.innerHTML = text;
}
</script>
```

**Educational content with multiple highlight types:**
```html
<div class="lesson-content">
  <h3>Chemical Reactions</h3>
  <p>In a <mark class="term">chemical reaction</mark>, substances 
  (<mark class="term">reactants</mark>) transform into different 
  substances (<mark class="term">products</mark>). The 
  <mark class="formula">law of conservation of mass</mark> states 
  that mass is neither created nor destroyed in chemical reactions.</p>
</div>

<style>
mark.term {
  background-color: #fff9c4;
  font-style: italic;
  padding: 1px 3px;
}

mark.formula {
  background-color: #f3e5f5;
  font-family: monospace;
  border-left: 3px solid #7b1fa2;
  padding: 1px 3px 1px 6px;
}
</style>
```

**Comparison highlighting:**
```html
<div class="comparison">
  <h4>Before Optimization:</h4>
  <p>The algorithm processed <mark>each element individually</mark>, 
  resulting in O(n²) time complexity.</p>
  
  <h4>After Optimization:</h4>
  <p>The optimized version processes elements in <mark>batches of 64</mark>, 
  achieving O(n log n) performance.</p>
</div>

<style>
.comparison mark {
  background-color: #c8e6c9;
  padding: 1px 4px;
  border-radius: 3px;
}
</style>
```

**Legal document with highlighted clauses:**
```html
<div class="legal-document">
  <h2>Service Agreement</h2>
  <p>By using this service, you agree to the following terms:</p>
  <ul>
    <li>Users must be <mark>at least 18 years old</mark> to create an account</li>
    <li>All content must comply with <mark>copyright laws</mark></li>
    <li>The service provider reserves the right to <mark>terminate accounts</mark> 
    that violate these terms</li>
    <li><mark>Monthly subscription fees</mark> will be automatically charged</li>
  </ul>
</div>

<style>
.legal-document mark {
  background-color: #ffecb3;
  font-weight: 600;
  padding: 1px 3px;
}
</style>
```

**Accessible highlighted content:**
```html
<p>The upcoming conference will focus on 
<mark aria-label="highlighted: web accessibility">web accessibility</mark> 
best practices and <mark aria-label="highlighted: inclusive design">inclusive design</mark> 
principles that benefit all users.</p>
```

**Highlighting in data tables:**
```html
<table>
  <caption>Quarterly Sales Report</caption>
  <thead>
    <tr>
      <th>Quarter</th>
      <th>Sales</th>
      <th>Growth</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Q1</td>
      <td>$125,000</td>
      <td>+5%</td>
    </tr>
    <tr>
      <td>Q2</td>
      <td><mark>$145,000</mark></td>
      <td><mark>+18%</mark></td>
    </tr>
    <tr>
      <td>Q3</td>
      <td>$138,000</td>
      <td>+12%</td>
    </tr>
  </tbody>
</table>

<style>
table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}

mark {
  background-color: #fff9c4;
  padding: 2px 4px;
}
</style>
```

**Dynamic search highlighting:**
```html
<input type="text" id="searchInput" placeholder="Search for terms...">
<div id="content">
  <p>Semantic HTML provides meaning to web content rather than just presentation. 
  Semantic elements like article, section, nav, and aside clearly describe their 
  meaning in a human- and machine-readable way.</p>
  
  <p>Using semantic HTML improves accessibility, SEO, and maintainability. 
  Screen readers can better interpret the page structure, and search engines 
  can understand the content hierarchy.</p>
</div>

<script>
document.getElementById('searchInput').addEventListener('input', function(e) {
  const searchTerm = e.target.value.trim();
  const content = document.getElementById('content');
  const originalHTML = content.dataset.original || content.innerHTML;
  
  // Store original HTML if not already stored
  if (!content.dataset.original) {
    content.dataset.original = originalHTML;
  }
  
  if (searchTerm.length < 2) {
    content.innerHTML = content.dataset.original;
    return;
  }
  
  const regex = new RegExp(`(${searchTerm})`, 'gi');
  const highlighted = originalHTML.replace(regex, '<mark>$1</mark>');
  content.innerHTML = highlighted;
});
</script>

<style>
#searchInput {
  padding: 8px 12px;
  margin-bottom: 16px;
  width: 300px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

mark {
  background-color: #ffeb3b;
  padding: 1px 2px;
  border-radius: 2px;
}
</style>
```

**Highlighting with different color schemes:**
```html
<p class="color-scheme-dark">
  This text contains <mark class="dark-highlight">highlighted content</mark> 
  that works well in dark mode.
</p>

<p class="color-scheme-light">
  This text contains <mark class="light-highlight">highlighted content</mark> 
  that works well in light mode.
</p>

<style>
.color-scheme-dark {
  background-color: #333;
  color: white;
  padding: 16px;
}

.color-scheme-light {
  background-color: white;
  color: #333;
  padding: 16px;
}

mark.dark-highlight {
  background-color: #ffd54f;
  color: #333;
  padding: 1px 4px;
}

mark.light-highlight {
  background-color: #1565c0;
  color: white;
  padding: 1px 4px;
}
</style>
```

**Nested highlighting for complex emphasis:**
```html
<p>In the sentence "The <mark>quick brown fox <strong>jumps</strong> 
over the lazy dog</mark>," the entire phrase is highlighted, but 
<strong>jumps</strong> receives additional emphasis.</p>
```

**Highlighting in form validation:**
```html
<form>
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" 
         pattern="[a-zA-Z0-9_]{3,20}" required>
  <div class="requirements">
    Must contain only <mark>letters</mark>, <mark>numbers</mark>, 
    and <mark>underscores</mark>, and be <mark>3-20 characters</mark> long.
  </div>
</form>

<style>
.requirements {
  font-size: 0.875em;
  color: #666;
  margin-top: 4px;
}

.requirements mark {
  background-color: #e8f5e8;
  color: #2e7d32;
  padding: 1px 3px;
  border-radius: 2px;
}
</style>
```

---

## Notes

* **Semantic difference from `<strong>` and `<em>`**:
  - `<strong>` indicates importance or seriousness
  - `<em>` indicates emphasis or stress
  - `<mark>` indicates relevance in current context
* **Browser compatibility**: Universally supported in modern browsers
* **Styling considerations**:
  - Default yellow background may not suit all color schemes
  - Custom styling often needed for better visual integration
  - Consider accessibility when choosing highlight colors
* **Common use cases**:
  - Search result highlighting
  - Educational materials and study guides
  - Legal document key points
  - Code documentation and tutorials
  - User attention direction
* **Accessibility best practices**:
  - Ensure sufficient color contrast for highlighted text
  - Consider providing alternative indicators for colorblind users
  - Use ARIA attributes when additional context is needed
  - Test with screen readers to ensure proper announcement
* **Performance**: Excessive use of `<mark>` elements may impact rendering performance
* **SEO considerations**: Search engines may interpret marked content as particularly relevant
* **Common mistakes**:
  - Using `<mark>` for permanent importance (use `<strong>` instead)
  - Using `<mark>` for stylistic purposes only (use CSS instead)
  - Overusing highlights, which can reduce their effectiveness
  - Poor color choices that reduce readability
* **Best practices**:
  - Use sparingly to maintain effectiveness
  - Choose highlight colors with sufficient contrast
  - Consider the semantic meaning before using
  - Test across different devices and user preferences
  - Provide clear context for why content is highlighted

---
