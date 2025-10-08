# `<h1>` to `<h6>`

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

The `<h1>` through `<h6>` tags represent six levels of section headings, with `<h1>` being the highest (most important) level and `<h6>` the lowest (least important) level. These elements create a hierarchical structure for document content, providing both visual organization and semantic meaning that is crucial for accessibility, SEO, and content comprehension.

---

## Syntax and Variants

+ All heading tags require both opening and closing tags: `<h1>...</h1>` through `<h6>...</h6>`.
+ They are non-void elements that contain text content and/or phrasing content.
+ No alternative or legacy forms exist, though their default styling has evolved across HTML versions.

---

## Attributes

The heading tags (`<h1>` through `<h6>`) support only **global attributes** with no specific attributes of their own:

**Global Attributes:**
- `id`: Particularly useful for creating document fragments and anchor links
- `class`, `style`: For CSS styling and visual customization
- `data-*`: For custom data attributes
- `aria-*`: For enhanced accessibility semantics (e.g., `aria-level` for overriding implicit heading levels)
- `lang`, `dir`: For language and text direction specific to the heading
- `title`: For advisory information that appears on hover

**Important Notes:**
- No required attributes for any heading level
- The `id` attribute is commonly used with headings to create navigable anchor points
- `aria-level` can override the implicit heading level for complex document structures
- Heading elements do not have any specific attributes that control their hierarchical behavior

---

## Content Model

All heading elements (`<h1>` through `<h6>`) share the same content model, supporting **phrasing content**:

**Permitted Content:**
- Text content
- Phrasing elements: `<span>`, `<strong>`, `<em>`, `<mark>`, `<code>`, etc.
- Inline links: `<a>`
- Images: `<img>` (when used inline with text)
- Line breaks: `<br>`
- Mathematical and annotation elements: `<sub>`, `<sup>`, `<small>`
- Time and semantic elements: `<time>`, `<data>`

**Restrictions:**
- Cannot contain **flow content** (block-level elements like `<div>`, `<p>`, other headings)
- Cannot contain interactive content that would break the heading semantics
- Should not contain only non-text content without appropriate text alternatives
- Nesting headings within headings is invalid

---

## Context

+ **Placement**: Can be placed within any sectioning content or flow content context.
+ **Parent Elements**: Typically found within `<body>`, `<article>`, `<section>`, `<aside>`, `<nav>`, `<header>`, `<main>`, and other sectioning elements
+ **Sectioning Roots**: Can also appear in elements that establish new sectioning roots like `<blockquote>`, `<details>`, `<fieldset>`, `<figure>`, `<td>`
+ **Usage Limits**: 
  - Should follow proper hierarchical nesting (don't skip heading levels)
  - Multiple headings of the same level can exist within appropriate sections
  - Each sectioning element can have its own heading hierarchy
  - The document should generally have only one `<h1>` representing the main topic

---

## Behavior and Semantics

+ **Rendering**: Heading tags are **block-level elements** that create line breaks before and after their content.
+ **Default CSS**: Browsers apply decreasing font sizes and varying weights:

  ```css
  h1 { display: block; font-size: 2em; margin: 0.67em 0; font-weight: bold; }
  h2 { display: block; font-size: 1.5em; margin: 0.83em 0; font-weight: bold; }
  h3 { display: block; font-size: 1.17em; margin: 1em 0; font-weight: bold; }
  h4 { display: block; font-size: 1em; margin: 1.33em 0; font-weight: bold; }
  h5 { display: block; font-size: 0.83em; margin: 1.67em 0; font-weight: bold; }
  h6 { display: block; font-size: 0.67em; margin: 2.33em 0; font-weight: bold; }
  ```

+ **Semantic Impact**:

  - **Accessibility**: Screen readers use heading structure to provide document navigation
  - **SEO**: Search engines use heading hierarchy to understand content importance and relationships
  - **Document Outline**: Creates an implicit document structure that aids comprehension
  - **User Experience**: Provides visual hierarchy that guides readers through content

---

## Examples

### Basic Example: Proper Heading Hierarchy

This example demonstrates correct hierarchical nesting of heading elements.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Proper Heading Hierarchy</title>
</head>
<body>
    <h1>Main Document Title</h1>
    
    <h2>Introduction</h2>
    <p>This is the introductory section...</p>
    
    <h2>Main Content</h2>
    
    <h3>First Topic</h3>
    <p>Content about the first topic...</p>
    
    <h4>Subtopic Details</h4>
    <p>More detailed information...</p>
    
    <h3>Second Topic</h3>
    <p>Content about the second topic...</p>
    
    <h2>Conclusion</h2>
    <p>Concluding remarks...</p>
</body>
</html>
```

### Intermediate Example: Headings in Sectioning Elements

This example shows how headings work within semantic sectioning elements.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Headings in Sections</title>
    <style>
        article { margin-bottom: 2rem; padding: 1rem; border: 1px solid #ddd; }
        section { margin-left: 1rem; }
    </style>
</head>
<body>
    <header>
        <h1>Website Blog</h1>
        <nav>
            <h2 class="sr-only">Main Navigation</h2>
            <!-- Navigation content -->
        </nav>
    </header>
    
    <main>
        <article>
            <h1>Understanding HTML Headings</h1>
            <p>Published on <time datetime="2024-01-15">January 15, 2024</time></p>
            
            <section>
                <h2>Introduction to Heading Elements</h2>
                <p>Heading elements provide structure...</p>
                
                <section>
                    <h3>Heading Levels</h3>
                    <p>There are six heading levels...</p>
                </section>
            </section>
            
            <section>
                <h2>Best Practices</h2>
                <p>Follow these guidelines for proper heading usage...</p>
            </section>
        </article>
        
        <aside>
            <h2>Related Articles</h2>
            <section>
                <h3>Semantic HTML</h3>
                <p>Learn about semantic elements...</p>
            </section>
        </aside>
    </main>
    
    <footer>
        <h2>About This Site</h2>
        <p>Copyright information and links...</p>
    </footer>
</body>
</html>
```

### Advanced Example: Complex Document Structure with ARIA

This example demonstrates advanced heading usage with ARIA attributes and complex layouts.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Advanced Heading Structure</title>
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
        
        .card {
            border: 1px solid #ccc;
            border-radius: 8px;
            padding: 1rem;
            margin: 1rem 0;
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
    </style>
</head>
<body>
    <h1>Product Documentation</h1>
    
    <nav aria-label="Table of Contents">
        <h2 id="toc-heading">Table of Contents</h2>
        <ul>
            <li><a href="#installation">Installation</a></li>
            <li><a href="#configuration">Configuration</a></li>
            <li><a href="#api">API Reference</a></li>
        </ul>
    </nav>
    
    <div class="card">
        <h2 id="installation">Installation Guide</h2>
        
        <h3>System Requirements</h3>
        <p>Minimum system requirements...</p>
        
        <h3>Installation Steps</h3>
        
        <h4>Step 1: Download</h4>
        <p>Download the installation package...</p>
        
        <h4>Step 2: Install Dependencies</h4>
        <p>Install required dependencies...</p>
        
        <h4>Step 3: Configuration</h4>
        <p>Configure your environment...</p>
    </div>
    
    <div class="card">
        <h2 id="configuration">Configuration Options</h2>
        
        <h3>Basic Configuration</h3>
        <p>Essential configuration settings...</p>
        
        <h3>Advanced Settings</h3>
        
        <h4>Performance Tuning</h4>
        <p>Optimize for performance...</p>
        
        <h4>Security Settings</h4>
        <p>Security-related configurations...</p>
    </div>
    
    <!-- Tab interface with proper heading structure -->
    <div role="tablist" aria-label="API Endpoints">
        <h2 id="api">API Reference</h2>
        
        <button role="tab" aria-selected="true" aria-controls="users-tab">
            <h3>Users API</h3>
        </button>
        <button role="tab" aria-selected="false" aria-controls="products-tab">
            <h3>Products API</h3>
        </button>
        
        <div role="tabpanel" id="users-tab" class="tab-content active" aria-labelledby="api">
            <h4>GET /users</h4>
            <p>Retrieve list of users...</p>
            
            <h4>POST /users</h4>
            <p>Create a new user...</p>
            
            <h5>Request Body</h5>
            <p>User object parameters...</p>
            
            <h5>Response</h5>
            <p>Success response format...</p>
        </div>
        
        <div role="tabpanel" id="products-tab" class="tab-content" aria-labelledby="api">
            <h4>GET /products</h4>
            <p>Retrieve product catalog...</p>
        </div>
    </div>
    
    <!-- Using aria-level for non-standard heading structures -->
    <div class="card">
        <div role="heading" aria-level="2">Custom Heading with ARIA</div>
        <p>This uses aria-level to create a heading outside the normal h1-h6 elements.</p>
        
        <div role="heading" aria-level="3">Subheading with ARIA</div>
        <p>This maintains proper hierarchy programmatically.</p>
    </div>
</body>
</html>
```

### Specialized Example: Responsive Headings with CSS

This example shows how to style headings responsively while maintaining semantics.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Headings</title>
    <style>
        :root {
            --heading-scale: 1.2;
            --base-size: 1rem;
        }
        
        .article-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }
        
        .article-card {
            background: #f8f9fa;
            padding: 1.5rem;
            border-radius: 8px;
        }
        
        /* Responsive heading sizes */
        h1 { font-size: calc(var(--base-size) * pow(var(--heading-scale), 5)); }
        h2 { font-size: calc(var(--base-size) * pow(var(--heading-scale), 4)); }
        h3 { font-size: calc(var(--base-size) * pow(var(--heading-scale), 3)); }
        h4 { font-size: calc(var(--base-size) * pow(var(--heading-scale), 2)); }
        h5 { font-size: calc(var(--base-size) * var(--heading-scale)); }
        h6 { font-size: var(--base-size); }
        
        /* Mobile adjustments */
        @media (max-width: 768px) {
            :root {
                --heading-scale: 1.15;
                --base-size: 0.9rem;
            }
            
            h1 { font-size: calc(var(--base-size) * pow(var(--heading-scale), 4)); }
        }
        
        /* Decorative heading styles */
        .fancy-heading {
            position: relative;
            padding-bottom: 0.5rem;
        }
        
        .fancy-heading::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 50px;
            height: 3px;
            background: linear-gradient(90deg, #ff6b6b, #4ecdc4);
        }
        
        /* Section with different heading context */
        .feature-section h2 {
            color: #2c3e50;
            border-left: 4px solid #3498db;
            padding-left: 1rem;
        }
    </style>
</head>
<body>
    <header>
        <h1 class="fancy-heading">Modern Web Design</h1>
        <p>Exploring responsive typography and semantic structure</p>
    </header>
    
    <main>
        <section class="feature-section">
            <h2>Featured Articles</h2>
            
            <div class="article-grid">
                <article class="article-card">
                    <h3>Responsive Typography</h3>
                    <p>Learn how to create fluid type scales...</p>
                    
                    <h4>Viewport Units</h4>
                    <p>Using vw, vh, vmin, and vmax...</p>
                </article>
                
                <article class="article-card">
                    <h3>CSS Grid Layout</h3>
                    <p>Modern layout techniques with CSS Grid...</p>
                    
                    <h4>Grid Template Areas</h4>
                    <p>Visual layout planning with named areas...</p>
                </article>
            </div>
        </section>
        
        <section>
            <h2>Technical Documentation</h2>
            
            <h3>Installation Guide</h3>
            <p>Step-by-step installation instructions...</p>
            
            <h4>Prerequisites</h4>
            <p>System requirements and dependencies...</p>
            
            <h4>Step 1: Environment Setup</h4>
            <p>Configure your development environment...</p>
            
            <h5>Node.js Installation</h5>
            <p>Installing Node.js and npm...</p>
            
            <h6>Troubleshooting</h6>
            <p>Common installation issues and solutions...</p>
        </section>
    </main>
</body>
</html>
```

---

## Notes

* **Historical Context**: 

  - Early HTML versions had less strict rules about heading hierarchy
  - HTML5 introduced the concept of sectioning elements and their impact on heading outlines
  - The default styling of headings has become more consistent across modern browsers

* **Accessibility Requirements**:

  - **Never skip heading levels** (e.g., don't go from `<h1>` to `<h3>` without an `<h2>`)
  - **Maintain logical structure** even when visually styling headings differently
  - **Use one `<h1>` per page** typically representing the main content
  - **Consider screen readers** that provide heading navigation as a primary feature

* **SEO Implications**:

  - Search engines use heading structure to understand content hierarchy and relevance
  - Proper heading use can improve content visibility in search results
  - Keyword stuffing in headings can negatively impact SEO
  - Heading structure should reflect the natural hierarchy of your content

* **Common Pitfalls**:

  - Using headings purely for visual styling rather than semantic structure
  - Skipping heading levels (e.g., `<h1>` directly to `<h3>`)
  - Having multiple `<h1>` elements on the same page (though this is debated in modern SEO)
  - Using headings for non-heading content (use `<p>` with CSS instead)
  - Nesting headings improperly within sectioning elements

* **Browser Quirks**:

  - Default margin sizes vary slightly between browsers
  - Some older browsers may not properly handle the document outline algorithm
  - Font rendering of bold text in headings can vary across operating systems
  - Mobile browsers may apply different default scaling to headings

* **Best Practices**:

  - Start with an `<h1>` that describes the main purpose of the page
  - Maintain a consistent, logical hierarchy throughout the document
  - Use sectioning elements (`<article>`, `<section>`) to create contextual heading hierarchies
  - Consider using CSS to style headings rather than choosing heading levels based on appearance
  - Test your heading structure with accessibility tools and screen readers
  - Use the HTML5 document outline algorithm to validate your heading structure

---
