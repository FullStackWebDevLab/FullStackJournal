# `<section>`

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

The `<section>` tag represents a thematic grouping of content, typically with a heading, that forms an independent part of a document or application. Unlike generic containers, sections should represent content that would naturally appear in a document's outline and logically belong together as a coherent unit. This element provides semantic meaning to content groups while facilitating document structure and accessibility.

---

## Syntax and Variants

+ The `<section>` tag requires both an opening `<section>` and closing `</section>` tag.
+ It is a non-void element that serves as a sectioning content container.
+ No alternative or legacy forms exist, as this is an HTML5 semantic element.

---

## Attributes

The `<section>` tag supports only **global attributes** with no specific attributes of its own:

**Global Attributes:**
- `id`: Particularly useful for creating document fragments and anchor links to specific sections
- `class`, `style`: For CSS styling and visual presentation
- `data-*`: For custom data attributes to store section-specific information
- `aria-*`: For enhanced accessibility semantics, such as `aria-labelledby` or `aria-label` when the section has no heading
- `lang`, `dir`: For language and text direction specific to the section content
- `title`: For advisory information about the section

**Important Notes:**
- No required attributes
- The `id` attribute is commonly used for navigation and JavaScript targeting
- `aria-labelledby` can associate a section with its heading for better accessibility
- `aria-label` can provide an accessible name when a visual heading isn't present

---

## Content Model

The `<section>` element can contain **flow content**, which includes virtually all elements that can appear in the document body:

**Permitted Content:**
- Text content and phrasing elements
- Heading elements (`<h1>`-`<h6>`) - strongly recommended for proper section identification
- Paragraphs (`<p>`), lists (`<ul>`, `<ol>`, `<dl>`), and other block-level elements
- Embedded content: `<img>`, `<video>`, `<audio>`, `<canvas>`, `<iframe>`
- Interactive elements: `<button>`, `<form>`, `<input>`, `<details>`
- Other sectioning elements: `<article>`, `<aside>`, `<nav>`, and even nested `<section>`
- Generic containers: `<div>`, `<span>`

**Restrictions:**
- Should not be used as a generic wrapper for styling purposes (use `<div>` instead)
- Should not contain `<main>` element (only one `<main>` per document)
- Content should be thematically related and meaningful when considered as a unit

---

## Context

+ **Placement**: Can be placed within any element that accepts flow content, including `<body>`, `<main>`, `<article>`, `<aside>`, `<div>`, and other `<section>` elements .
+ **Parent Elements**: `<body>`, `<main>`, `<article>`, `<aside>`, `<div>`, `<li>`, `<blockquote>`, `<td>`, and other sectioning/content elements
+ **Sectioning Root**: The `<section>` element itself is a sectioning element that creates a new section in the document outline
+ **Usage Limits**: 
  - Multiple `<section>` elements are encouraged for proper content organization
  - Can be nested to create hierarchical content structures
  - Should represent actual document sections, not just visual groupings

---

## Behavior and Semantics

+ **Rendering**: The `<section>` tag is a **block-level element** that creates line breaks before and after its content.
+ **Default CSS**: Browsers apply minimal default styling:
  ```css
  section {
    display: block;
  }
  ```
+ **Document Outline**: Creates an entry in the document outline, which can be navigated by assistive technologies
+ **Semantic Impact**:
  - **Accessibility**: Screen readers can identify and navigate between sections, improving user experience for visually impaired users
  - **SEO**: Search engines use section structure to better understand content organization and relevance
  - **Maintainability**: Provides semantic meaning that makes HTML more readable and maintainable
  - **User Experience**: Helps all users mentally organize and navigate complex content

---

## Examples

### Basic Example: Document Sections with Headings

This example demonstrates proper use of `<section>` with heading elements.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Basic Section Example</title>
    <style>
        section {
            margin: 2rem 0;
            padding: 1.5rem;
            border-left: 4px solid #3498db;
            background: #f8f9fa;
        }
        
        h2 {
            color: #2c3e50;
            margin-top: 0;
        }
    </style>
</head>
<body>
    <h1>Research Paper: Climate Change Impacts</h1>
    
    <section id="introduction">
        <h2>Introduction</h2>
        <p>Climate change represents one of the most significant challenges facing humanity today...</p>
        <p>This paper examines the various impacts across different ecosystems and human systems.</p>
    </section>
    
    <section id="methodology">
        <h2>Methodology</h2>
        <p>Our research employed a mixed-methods approach combining quantitative data analysis...</p>
        
        <h3>Data Collection</h3>
        <p>We gathered temperature records from 150 weather stations spanning 50 years...</p>
    </section>
    
    <section id="results">
        <h2>Results</h2>
        <p>The analysis revealed several key trends in climate patterns...</p>
        
        <section id="temperature-results">
            <h3>Temperature Changes</h3>
            <p>Average temperatures have increased by 1.2°C over the study period...</p>
        </section>
        
        <section id="precipitation-results">
            <h3>Precipitation Patterns</h3>
            <p>Changes in precipitation show significant regional variation...</p>
        </section>
    </section>
    
    <section id="conclusion">
        <h2>Conclusion</h2>
        <p>The findings underscore the urgent need for comprehensive climate action...</p>
    </section>
</body>
</html>
```

### Intermediate Example: Complex Page Structure

This example shows sections used in a more complex layout with multiple content types.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Company Website</title>
    <style>
        .page-section {
            padding: 3rem 1rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .hero-section {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-align: center;
        }
        
        .features-section {
            background: #f8f9fa;
        }
        
        .feature-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }
        
        .testimonials-section {
            background: #2c3e50;
            color: white;
        }
    </style>
</head>
<body>
    <header>
        <nav><!-- Navigation content --></nav>
    </header>
    
    <main>
        <section class="page-section hero-section" aria-labelledby="hero-heading">
            <h1 id="hero-heading">Innovative Solutions for Modern Business</h1>
            <p>We help companies transform their digital presence with cutting-edge technology.</p>
            <button>Learn More</button>
        </section>
        
        <section class="page-section features-section" aria-labelledby="features-heading">
            <h2 id="features-heading">Our Core Features</h2>
            <div class="feature-grid">
                <section class="feature" aria-labelledby="feature1-heading">
                    <h3 id="feature1-heading">Cloud Integration</h3>
                    <p>Seamlessly integrate with all major cloud platforms for scalable solutions.</p>
                </section>
                
                <section class="feature" aria-labelledby="feature2-heading">
                    <h3 id="feature2-heading">Data Analytics</h3>
                    <p>Transform raw data into actionable insights with our advanced analytics platform.</p>
                </section>
                
                <section class="feature" aria-labelledby="feature3-heading">
                    <h3 id="feature3-heading">Security First</h3>
                    <p>Enterprise-grade security measures to protect your valuable data and assets.</p>
                </section>
            </div>
        </section>
        
        <section class="page-section testimonials-section" aria-labelledby="testimonials-heading">
            <h2 id="testimonials-heading">Client Success Stories</h2>
            
            <section class="testimonial" aria-labelledby="testimonial1-heading">
                <h3 id="testimonial1-heading">Global Tech Corp</h3>
                <blockquote>
                    <p>"This solution increased our operational efficiency by 40% within the first quarter."</p>
                    <cite>— Sarah Chen, CTO</cite>
                </blockquote>
            </section>
            
            <section class="testimonial" aria-labelledby="testimonial2-heading">
                <h3 id="testimonial2-heading">Innovation Labs</h3>
                <blockquote>
                    <p>"The implementation was seamless and the support team was exceptional throughout."</p>
                    <cite>— Marcus Johnson, CEO</cite>
                </blockquote>
            </section>
        </section>
    </main>
    
    <footer>
        <section aria-labelledby="contact-heading">
            <h2 id="contact-heading">Contact Us</h2>
            <address>
                <p>Email: info@company.com</p>
                <p>Phone: (555) 123-4567</p>
            </address>
        </section>
    </footer>
</body>
</html>
```

### Advanced Example: Nested Sections with ARIA

This example demonstrates complex nested sections with enhanced accessibility.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Advanced Section Structure</title>
    <style>
        .chapter {
            margin: 2rem 0;
            padding: 2rem;
            border: 1px solid #ddd;
            border-radius: 8px;
        }
        
        .section {
            margin: 1.5rem 0;
            padding: 1rem;
            background: #f8f9fa;
            border-left: 3px solid #3498db;
        }
        
        .subsection {
            margin: 1rem 0;
            padding: 0.5rem 1rem;
            background: #e9ecef;
        }
        
        .code-sample {
            background: #2d3748;
            color: #e2e8f0;
            padding: 1rem;
            border-radius: 4px;
            font-family: 'Courier New', monospace;
        }
    </style>
</head>
<body>
    <article>
        <h1>Advanced Web Development Guide</h1>
        
        <section class="chapter" id="html5-semantics" aria-labelledby="html5-heading">
            <h2 id="html5-heading">HTML5 Semantic Elements</h2>
            <p>Modern HTML5 provides numerous semantic elements for better document structure.</p>
            
            <section class="section" id="sectioning-elements" aria-labelledby="sectioning-heading">
                <h3 id="sectioning-heading">Sectioning Elements</h3>
                <p>Sectioning elements create outlines and help organize content logically.</p>
                
                <section class="subsection" id="section-element" aria-labelledby="section-heading">
                    <h4 id="section-heading">The &lt;section&gt; Element</h4>
                    <p>The <code>&lt;section&gt;</code> element represents a thematic grouping of content.</p>
                    
                    <div class="code-sample">
&lt;section id="introduction"&gt;
    &lt;h2&gt;Introduction&lt;/h2&gt;
    &lt;p&gt;This section contains introductory content...&lt;/p&gt;
&lt;/section&gt;
                    </div>
                </section>
                
                <section class="subsection" id="article-element" aria-labelledby="article-heading">
                    <h4 id="article-heading">The &lt;article&gt; Element</h4>
                    <p>Use <code>&lt;article&gt;</code> for self-contained, reusable content.</p>
                </section>
            </section>
            
            <section class="section" id="accessibility" aria-labelledby="a11y-heading">
                <h3 id="a11y-heading">Accessibility Considerations</h3>
                <p>Proper semantic structure greatly enhances accessibility.</p>
                
                <section class="subsection" id="aria-landmarks" aria-labelledby="aria-heading">
                    <h4 id="aria-heading">ARIA Landmarks</h4>
                    <p>Use ARIA landmarks to enhance navigation for screen reader users.</p>
                </section>
            </section>
        </section>
        
        <section class="chapter" id="css-layout" aria-labelledby="css-heading">
            <h2 id="css-heading">Modern CSS Layout</h2>
            <p>CSS Grid and Flexbox have revolutionized web layout techniques.</p>
            
            <section class="section" id="css-grid" aria-labelledby="grid-heading">
                <h3 id="grid-heading">CSS Grid Layout</h3>
                <p>Two-dimensional layout system for complex web applications.</p>
            </section>
        </section>
    </article>
</body>
</html>
```

### Specialized Example: Tabbed Interface with Sections

This example shows sections used in an interactive tabbed interface.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Tabbed Documentation</title>
    <style>
        .tabs {
            display: flex;
            border-bottom: 2px solid #ddd;
            margin-bottom: 0;
        }
        
        .tab-button {
            padding: 1rem 2rem;
            background: none;
            border: none;
            border-bottom: 3px solid transparent;
            cursor: pointer;
            font-size: 1rem;
        }
        
        .tab-button.active {
            border-bottom-color: #3498db;
            color: #3498db;
            font-weight: bold;
        }
        
        .tab-content {
            display: none;
            padding: 2rem;
            border: 1px solid #ddd;
            border-top: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .api-endpoint {
            background: #f8f9fa;
            padding: 1rem;
            margin: 1rem 0;
            border-left: 4px solid #28a745;
        }
    </style>
</head>
<body>
    <h1>API Documentation</h1>
    
    <div role="tablist" aria-label="API Documentation Sections">
        <button role="tab" aria-selected="true" aria-controls="authentication-tab" class="tab-button active">
            Authentication
        </button>
        <button role="tab" aria-selected="false" aria-controls="users-tab" class="tab-button">
            Users API
        </button>
        <button role="tab" aria-selected="false" aria-controls="products-tab" class="tab-button">
            Products API
        </button>
    </div>
    
    <section id="authentication-tab" role="tabpanel" class="tab-content active" aria-labelledby="authentication-heading">
        <h2 id="authentication-heading">Authentication</h2>
        <p>All API requests require authentication using JWT tokens.</p>
        
        <section class="api-endpoint" aria-labelledby="login-endpoint-heading">
            <h3 id="login-endpoint-heading">POST /api/auth/login</h3>
            <p>Authenticate user and receive access token.</p>
            
            <section aria-labelledby="login-request-heading">
                <h4 id="login-request-heading">Request Body</h4>
                <pre><code>{
  "username": "string",
  "password": "string"
}</code></pre>
            </section>
            
            <section aria-labelledby="login-response-heading">
                <h4 id="login-response-heading">Response</h4>
                <pre><code>{
  "token": "jwt-token-string",
  "expiresIn": 3600
}</code></pre>
            </section>
        </section>
    </section>
    
    <section id="users-tab" role="tabpanel" class="tab-content" aria-labelledby="users-heading">
        <h2 id="users-heading">Users API</h2>
        <p>Manage user accounts and profiles.</p>
        
        <section class="api-endpoint" aria-labelledby="get-users-heading">
            <h3 id="get-users-heading">GET /api/users</h3>
            <p>Retrieve list of users with optional filtering.</p>
        </section>
    </section>
    
    <section id="products-tab" role="tabpanel" class="tab-content" aria-labelledby="products-heading">
        <h2 id="products-heading">Products API</h2>
        <p>Manage product catalog and inventory.</p>
        
        <section class="api-endpoint" aria-labelledby="create-product-heading">
            <h3 id="create-product-heading">POST /api/products</h3>
            <p>Create a new product in the catalog.</p>
        </section>
    </section>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const tabButtons = document.querySelectorAll('.tab-button');
            const tabContents = document.querySelectorAll('.tab-content');
            
            tabButtons.forEach(button => {
                button.addEventListener('click', function() {
                    // Remove active class from all buttons and contents
                    tabButtons.forEach(btn => {
                        btn.classList.remove('active');
                        btn.setAttribute('aria-selected', 'false');
                    });
                    tabContents.forEach(content => content.classList.remove('active'));
                    
                    // Add active class to clicked button and corresponding content
                    this.classList.add('active');
                    this.setAttribute('aria-selected', 'true');
                    const targetTab = document.getElementById(this.getAttribute('aria-controls'));
                    targetTab.classList.add('active');
                });
            });
        });
    </script>
</body>
</html>
```

---

## Notes

* **When to Use `<section>` vs `<div>`**:

  - Use `<section>` for **thematic content groupings** that belong in the document outline
  - Use `<div>` for **styling wrappers** or **generic containers** without semantic meaning
  - If you're grouping content just for CSS styling, use `<div>`
  - If the content forms a logical section of your document, use `<section>`

* **When to Use `<section>` vs `<article>`**:

  - Use `<article>` for **self-contained, reusable content** (blog posts, news articles, product cards)
  - Use `<section>` for **thematic groupings within content** (chapters, tab panels, documentation sections)
  - An `<article>` can contain multiple `<section>` elements
  - A `<section>` can contain multiple `<article>` elements

* **Accessibility Best Practices**:

  - **Always include a heading** within each section for proper identification
  - Use `aria-labelledby` to associate the section with its heading
  - Use `aria-label` if a visual heading isn't present but you need an accessible name
  - Avoid nesting sections too deeply (3-4 levels maximum for usability)

* **Common Pitfalls**:

  - Using `<section>` as a generic replacement for `<div>`
  - Creating sections without headings (poor accessibility)
  - Over-nesting sections without clear thematic purpose
  - Using sections for small, unrelated content groupings

* **SEO Considerations**:

  - Proper section structure helps search engines understand content hierarchy
  - Sections with relevant headings can improve content relevance for specific queries
  - Avoid keyword stuffing in section headings
  - Ensure section content is thematically consistent with its heading

* **Browser Support**:

  - Excellent support in all modern browsers
  - Internet Explorer 9+ supports `<section>` with basic styling
  - The document outline algorithm may not be fully implemented in all browsers

*   **Best Practices**:

  - Start each section with a heading element (`<h1>`-`<h6>`)
  - Use the `id` attribute for navigable sections
  - Keep sections thematically focused and coherent
  - Consider the document outline when nesting sections
  - Test with screen readers to ensure proper navigation
  - Use ARIA attributes when the native semantics need enhancement

---
