# `<textarea>`

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

The `<textarea>` element represents a multi-line plain-text editing control, useful for collecting longer text input from users such as comments, descriptions, or messages. Unlike the `<input>` element which is single-line, `<textarea>` provides a resizable text box capable of handling substantial amounts of text with built-in scrolling capabilities.

---

## Syntax and Variants

+ **Standard syntax**: `<textarea>...</textarea>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain initial text content between tags
+ **No self-closing variant**: Must be properly closed
+ **Text container**: Initial value provided as text content rather than attribute

---

## Attributes

+ **Core attributes**:
  - `name` (optional): Name for form submission and scripting
  - `rows` (optional): Visible number of text lines (positive integer)
  - `cols` (optional): Visible width in character columns (positive integer)
  - `placeholder` (optional): Hint text displayed when textarea is empty
  - `required` (optional): Marks field as mandatory (boolean)
  - `disabled` (optional): Disables the textarea (boolean)
  - `readonly` (optional): Makes textarea read-only (boolean)
  - `autocomplete` (optional): Enable/disable autocomplete (`on`, `off`)
  - `autofocus` (optional): Automatically focus on page load (boolean)
  - `maxlength` (optional): Maximum number of characters allowed
  - `minlength` (optional): Minimum number of characters required
  - `wrap` (optional): Text wrapping behavior (`soft`, `hard`)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No type attribute**: Unlike `<input>`, textarea doesn't have a type attribute

---

## Content Model

+ **Permitted content**: Text only
+ **Allowed content**: 
  - Plain text and character references
  - No HTML elements or formatting
+ **Initial value**: Provided as text content between opening and closing tags
+ **Whitespace**: Preserves whitespace and line breaks in content

---

## Context

+ **Required parent**: Should be within a `<form>` element for submission
+ **Common locations**:
  - Directly within `<form>` elements
  - Within `<div>`, `<fieldset>`, or other form containers
  - With associated `<label>` elements for accessibility
+ **Form association**: Can be associated with forms using `form` attribute

---

## Behavior and Semantics

+ **Default display**: Inline-block element
+ **Default styling**:
  - `display: inline-block`
  - Typically has borders and padding
  - Resizable handle in bottom-right corner (CSS `resize` property)
  - Monospace or system font family
+ **Interactive behavior**:
  - Multi-line text editing with word wrap
  - Vertical and horizontal scrolling when content overflows
  - Supports text selection, copy, paste operations
  - Can be resized by user (unless disabled via CSS)
+ **Semantic meaning**:
  - Represents a multi-line text input control
  - Screen readers announce as "text area" or "edit text"
  - Provides context for longer text entry
+ **Accessibility**: Requires proper labeling and may need additional instructions for complex use cases

---

## Examples

**Basic textarea:**
```html
<label for="comments">Comments:</label>
<textarea id="comments" name="comments" 
          rows="4" cols="50"
          placeholder="Enter your comments here..."></textarea>
```

**Textarea with initial content:**
```html
<label for="message">Message Template:</label>
<textarea id="message" name="message" rows="6" cols="40">
Dear Team,

I wanted to follow up on our recent discussion.

Best regards,
[Your Name]
</textarea>
```

**Required textarea with validation:**
```html
<label for="description">Product Description:</label>
<textarea id="description" name="description"
          rows="5" cols="60"
          placeholder="Describe the product features and benefits..."
          minlength="50"
          maxlength="1000"
          required
          aria-describedby="desc-help">
</textarea>
<small id="desc-help">Must be between 50 and 1000 characters.</small>
```

**Styled textarea with CSS:**
```html
<label for="bio">Biography:</label>
<textarea id="bio" name="bio" 
          class="styled-textarea"
          placeholder="Tell us about yourself..."
          rows="8"></textarea>

<style>
.styled-textarea {
  width: 100%;
  max-width: 600px;
  padding: 12px;
  border: 2px solid #ddd;
  border-radius: 8px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 16px;
  line-height: 1.5;
  resize: vertical;
  transition: border-color 0.3s ease;
}

.styled-textarea:focus {
  border-color: #4CAF50;
  outline: none;
  box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.1);
}
</style>
```

**Textarea with character counter:**
```html
<div class="textarea-with-counter">
  <label for="review">Product Review:</label>
  <textarea id="review" name="review"
            rows="6" 
            maxlength="500"
            placeholder="Write your review here..."
            aria-describedby="char-count"></textarea>
  <div id="char-count" class="char-counter" aria-live="polite">
    <span id="char-remaining">500</span> characters remaining
  </div>
</div>

<script>
const textarea = document.getElementById('review');
const charCounter = document.getElementById('char-remaining');

textarea.addEventListener('input', function() {
  const remaining = this.maxLength - this.value.length;
  charCounter.textContent = remaining;
  
  // Update visual feedback
  if (remaining < 50) {
    charCounter.style.color = '#e74c3c';
  } else if (remaining < 100) {
    charCounter.style.color = '#f39c12';
  } else {
    charCounter.style.color = '#27ae60';
  }
});
</script>

<style>
.textarea-with-counter {
  position: relative;
  max-width: 600px;
}

.char-counter {
  text-align: right;
  font-size: 0.875rem;
  margin-top: 0.5rem;
  color: #666;
}
</style>
```

**Read-only textarea for displaying content:**
```html
<label for="terms">Terms and Conditions:</label>
<textarea id="terms" name="terms" rows="10" readonly>
1. Introduction
Welcome to our service. By using our platform, you agree to these terms.

2. User Responsibilities
You are responsible for maintaining the confidentiality of your account.

3. Privacy
We respect your privacy and are committed to protecting your personal data.

[Additional terms...]
</textarea>
```

**Textarea with auto-resize functionality:**
```html
<label for="dynamic-textarea">Dynamic Textarea:</label>
<textarea id="dynamic-textarea" name="dynamic_content"
          class="auto-resize"
          placeholder="This textarea grows with your content..."
          rows="1"></textarea>

<style>
.auto-resize {
  width: 100%;
  max-width: 500px;
  resize: none;
  overflow: hidden;
  min-height: 40px;
  transition: height 0.2s ease;
}
</style>

<script>
const dynamicTextarea = document.getElementById('dynamic-textarea');

dynamicTextarea.addEventListener('input', function() {
  this.style.height = 'auto';
  this.style.height = (this.scrollHeight) + 'px';
});

// Initialize height
dynamicTextarea.dispatchEvent(new Event('input'));
</script>
```

**Accessible textarea with ARIA:**
```html
<div class="form-group">
  <label for="accessible-textarea" id="textarea-label">
    Project Description
    <span class="required" aria-hidden="true">*</span>
  </label>
  
  <textarea id="accessible-textarea"
            name="project_description"
            rows="6"
            required
            aria-labelledby="textarea-label"
            aria-required="true"
            aria-describedby="textarea-help textarea-error"
            aria-invalid="false"
            placeholder="Describe your project requirements and goals...">
  </textarea>
  
  <div id="textarea-help" class="help-text">
    Please provide a detailed description of your project, including objectives, timeline, and any specific requirements.
  </div>
  
  <div id="textarea-error" class="error-text" aria-live="polite"></div>
</div>

<script>
const textarea = document.getElementById('accessible-textarea');
const errorElement = document.getElementById('textarea-error');

textarea.addEventListener('blur', function() {
  if (this.validity.valueMissing) {
    this.setAttribute('aria-invalid', 'true');
    errorElement.textContent = 'Project description is required.';
  } else if (this.value.length < 20) {
    this.setAttribute('aria-invalid', 'true');
    errorElement.textContent = 'Description must be at least 20 characters.';
  } else {
    this.setAttribute('aria-invalid', 'false');
    errorElement.textContent = '';
  }
});
</script>
```

**Textarea with markdown preview:**
```html
<div class="markdown-editor">
  <label for="markdown-content">Markdown Content:</label>
  <div class="editor-container">
    <textarea id="markdown-content" name="markdown_content"
              rows="12" 
              placeholder="Write your content in Markdown..."
              aria-describedby="markdown-help"></textarea>
    <div class="preview-container">
      <h4>Preview:</h4>
      <div id="markdown-preview" class="preview-content"></div>
    </div>
  </div>
  <small id="markdown-help">Supports Markdown formatting: **bold**, *italic*, `code`, etc.</small>
</div>

<style>
.markdown-editor {
  max-width: 800px;
}

.editor-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-bottom: 10px;
}

#markdown-content {
  width: 100%;
  resize: vertical;
  font-family: 'Courier New', monospace;
}

.preview-content {
  border: 1px solid #ddd;
  padding: 12px;
  min-height: 200px;
  background: #f9f9f9;
  border-radius: 4px;
}

@media (max-width: 768px) {
  .editor-container {
    grid-template-columns: 1fr;
  }
}
</style>

<script>
const markdownTextarea = document.getElementById('markdown-content');
const preview = document.getElementById('markdown-preview');

function updatePreview() {
  const content = markdownTextarea.value;
  // Simple markdown parsing (in real implementation, use a library like marked.js)
  const html = content
    .replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>')
    .replace(/\*(.*?)\*/g, '<em>$1</em>')
    .replace(/`(.*?)`/g, '<code>$1</code>')
    .replace(/\n/g, '<br>');
  
  preview.innerHTML = html || '<em>Preview will appear here...</em>';
}

markdownTextarea.addEventListener('input', updatePreview);
updatePreview(); // Initial preview
</script>
```

**Textarea with tab support:**
```html
<label for="code-editor">Code Snippet:</label>
<textarea id="code-editor" name="code"
          class="code-textarea"
          rows="10"
          placeholder="Paste your code here...">
function helloWorld() {
  console.log("Hello, World!");
}
</textarea>

<style>
.code-textarea {
  font-family: 'Courier New', monospace;
  font-size: 14px;
  line-height: 1.4;
  tab-size: 2;
}
</style>

<script>
const codeTextarea = document.getElementById('code-editor');

codeTextarea.addEventListener('keydown', function(e) {
  if (e.key === 'Tab') {
    e.preventDefault();
    
    const start = this.selectionStart;
    const end = this.selectionEnd;
    
    // Insert two spaces at cursor position
    this.value = this.value.substring(0, start) + '  ' + this.value.substring(end);
    
    // Move cursor position after the inserted spaces
    this.selectionStart = this.selectionEnd = start + 2;
  }
});
</script>
```

**Textarea in a contact form:**
```html
<form action="/contact" method="post" class="contact-form">
  <h2>Contact Us</h2>
  
  <div class="form-group">
    <label for="contact-name">Your Name:</label>
    <input type="text" id="contact-name" name="name" required>
  </div>
  
  <div class="form-group">
    <label for="contact-email">Email:</label>
    <input type="email" id="contact-email" name="email" required>
  </div>
  
  <div class="form-group">
    <label for="contact-subject">Subject:</label>
    <input type="text" id="contact-subject" name="subject" required>
  </div>
  
  <div class="form-group">
    <label for="contact-message">Message:</label>
    <textarea id="contact-message" name="message"
              rows="8" 
              placeholder="How can we help you?"
              minlength="10"
              maxlength="2000"
              required
              aria-describedby="message-help"></textarea>
    <small id="message-help">Please provide detailed information about your inquiry.</small>
  </div>
  
  <button type="submit">Send Message</button>
</form>

<style>
.contact-form {
  max-width: 600px;
  margin: 0 auto;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: bold;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}
</style>
```

---

## Notes

* **Content vs value**: Initial content provided as text between tags, not as `value` attribute
* **Accessibility requirements**:
  - Always associate with `<label>` elements
  - Provide clear instructions for expected input format
  - Use `aria-describedby` for additional help text
  - Ensure proper contrast and readable font sizes
* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using self-closing syntax (invalid for textarea)
  - Forgetting to specify `name` attribute for form submission
  - Not providing adequate sizing (rows/cols or CSS dimensions)
  - Overlooking scroll behavior for long content
  - Using for formatted text (textarea only handles plain text)
* **CSS styling**:
  - Use `resize` property to control resizing behavior (`both`, `horizontal`, `vertical`, `none`)
  - `overflow` property controls scrollbar behavior
  - Font and line-height affect text readability
* **Mobile considerations**:
  - Ensure adequate touch target size
  - Consider virtual keyboard behavior
  - Test with various screen sizes and orientations
* **Performance**: 
  - Very large text content can impact performance
  - Consider virtualization for extremely large text areas
  - Debounce real-time validation for better performance
* **Security**: 
  - Sanitize user input when displaying textarea content elsewhere
  - Be cautious of XSS when pre-populating with user data
  - Validate both client-side and server-side

---
