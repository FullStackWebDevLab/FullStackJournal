# `<main>`

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

The `<main>` tag represents the dominant content of the `<body>` of a document, application, or website. It should contain content that is directly related to or expands upon the central topic of the document, excluding content that is repeated across a set of documents such as navigation links, copyright information, site logos, and search forms. This element helps identify the primary content area for users, assistive technologies, and search engines.

---

## Syntax and Variants

+ The `<main>` tag requires both an opening `<main>` and closing `</main>` tag .
+ It is a non-void element that serves as the primary content container .
+ No alternative or legacy forms exist, as this is an HTML5 semantic element .

---

## Attributes

The `<main>` tag supports only **global attributes** with no specific attributes of its own:

**Global Attributes:**
- `id`: Useful for creating unique identifiers for main content areas, enabling direct linking and JavaScript targeting
- `class`, `style`: For CSS styling and visual presentation
- `data-*`: For custom data attributes to store main-content-specific information
- `aria-*`: For enhanced accessibility semantics, though the element implicitly has `role="main"`
- `lang`, `dir`: For language and text direction specific to the main content
- `title`: For advisory information about the main content area

**Important Notes:**
- No required attributes
- The element implicitly has `role="main"` for accessibility
- The `id` attribute is commonly used for skip navigation links
- Multiple `class` names can be used for styling different types of main content areas

---

## Content Model

The `<main>` element can contain **flow content**, which includes virtually all elements that can appear in the document body:

**Permitted Content:**
- Text content and phrasing elements
- Heading elements (`<h1>`-`<h6>`) - typically starting with the main document heading
- Paragraphs (`<p>`), lists (`<ul>`, `<ol>`, `<dl>`), and other block-level elements
- Sectioning elements: `<article>`, `<section>`, `<nav>` (when used for in-content navigation), `<aside>` (when related to main content)
- Embedded content: `<img>`, `<video>`, `<audio>`, `<canvas>`, `<iframe>`
- Interactive elements: `<button>`, `<form>`, `<input>`, `<details>`
- Generic containers: `<div>`, `<span>`
- Tables: `<table>`, `<tr>`, `<td>`, etc.

**Restrictions:**
- Cannot contain another `<main>` element
- Should not contain content that is repeated across pages (headers, footers, navigation, etc.)
- Should represent the unique, central content of the document

---

## Context

+ **Placement**: Should be placed within the `<body>` element, typically after the `<header>` and before the `<footer>`.
+ **Parent Elements**: `<body>` is the primary parent, though it can also be placed within other container elements that accept flow content
+ **Sibling Elements**: Typically follows `<header>` and precedes `<footer>` elements
+ **Usage Limits**: 
  - Only one `<main>` element should be used per document
  - The element should not be nested within `<article>`, `<aside>`, `<footer>`, `<header>`, or `<nav>` elements
  - Should contain the unique, primary content of the page

---

## Behavior and Semantics

+ **Rendering**: The `<main>` tag is a **block-level element** that creates line breaks before and after its content .
+ **Default CSS**: Browsers apply minimal default styling:
  ```css
  main {
    display: block;
  }
  ```
+ **Semantic Impact**:
  - **Accessibility**: Screen readers recognize main as a landmark region (`role="main"`), allowing users to jump directly to primary content
  - **SEO**: Search engines prioritize content within main as the primary subject matter of the page
  - **User Experience**: Provides clear semantic structure that helps users identify the core content
  - **Navigation**: Enables "skip to main content" functionality for keyboard and screen reader users

---

## Examples

### Basic Example: Simple Document Structure

This example demonstrates a basic document structure with main content area.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Basic Main Example</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            line-height: 1.6;
        }
        
        .skip-link {
            position: absolute;
            top: -40px;
            left: 6px;
            background: #000;
            color: white;
            padding: 8px;
            text-decoration: none;
            z-index: 1000;
        }
        
        .skip-link:focus {
            top: 6px;
        }
        
        header {
            background: #2c3e50;
            color: white;
            padding: 1rem 2rem;
        }
        
        main {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        footer {
            background: #34495e;
            color: white;
            text-align: center;
            padding: 1rem;
            margin-top: 2rem;
        }
        
        .article-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }
        
        .article-card {
            background: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
    </style>
</head>
<body>
    <!-- Skip to main content link for accessibility -->
    <a href="#main-content" class="skip-link">Skip to main content</a>
    
    <header role="banner">
        <nav aria-label="Main navigation">
            <a href="/">Home</a>
            <a href="/about">About</a>
            <a href="/contact">Contact</a>
        </nav>
    </header>
    
    <main id="main-content" role="main">
        <h1>Welcome to Our Website</h1>
        <p>This is the main content area of our webpage. It contains the unique, primary content that users are looking for.</p>
        
        <section aria-labelledby="featured-heading">
            <h2 id="featured-heading">Featured Articles</h2>
            <div class="article-grid">
                <article class="article-card">
                    <h3>Understanding Semantic HTML</h3>
                    <p>Learn how semantic elements improve accessibility and SEO.</p>
                    <a href="/article/semantic-html">Read more</a>
                </article>
                
                <article class="article-card">
                    <h3>CSS Grid Layout Guide</h3>
                    <p>Master modern CSS layout techniques with this comprehensive guide.</p>
                    <a href="/article/css-grid">Read more</a>
                </article>
                
                <article class="article-card">
                    <h3>JavaScript Best Practices</h3>
                    <p>Discover essential patterns and practices for modern JavaScript development.</p>
                    <a href="/article/javascript-practices">Read more</a>
                </article>
            </div>
        </section>
        
        <section aria-labelledby="about-heading">
            <h2 id="about-heading">About Our Mission</h2>
            <p>We are dedicated to creating accessible, performant, and user-friendly web experiences. Our content focuses on modern web development practices and emerging technologies.</p>
        </section>
    </main>
    
    <footer role="contentinfo">
        <p>&copy; 2024 Company Name. All rights reserved.</p>
        <nav aria-label="Footer navigation">
            <a href="/privacy">Privacy Policy</a>
            <a href="/terms">Terms of Service</a>
        </nav>
    </footer>
</body>
</html>
```

### Intermediate Example: Complex Application Layout

This example shows main used in a more complex web application layout.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Web Application Layout</title>
    <style>
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --text-light: #ecf0f1;
            --spacing: 1rem;
        }
        
        body {
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: grid;
            grid-template-rows: auto 1fr auto;
            min-height: 100vh;
        }
        
        .app-header {
            background: var(--primary-color);
            color: var(--text-light);
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .app-main {
            display: grid;
            grid-template-columns: 250px 1fr;
            gap: 0;
            min-height: calc(100vh - 120px);
        }
        
        .sidebar {
            background: #34495e;
            color: var(--text-light);
            padding: 2rem 1rem;
        }
        
        .sidebar nav ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }
        
        .sidebar nav a {
            color: var(--text-light);
            text-decoration: none;
            display: block;
            padding: 0.75rem 1rem;
            border-radius: 4px;
            transition: background-color 0.3s ease;
        }
        
        .sidebar nav a:hover {
            background: rgba(255,255,255,0.1);
        }
        
        .content-area {
            padding: 2rem;
            background: #f8f9fa;
            overflow-y: auto;
        }
        
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
            margin: 2rem 0;
        }
        
        .metric-card {
            background: white;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            text-align: center;
        }
        
        .metric-value {
            font-size: 2.5rem;
            font-weight: bold;
            color: var(--primary-color);
            margin: 0.5rem 0;
        }
        
        .metric-label {
            color: #7f8c8d;
            font-size: 0.9rem;
        }
        
        .content-section {
            background: white;
            border-radius: 8px;
            padding: 1.5rem;
            margin: 1.5rem 0;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .app-footer {
            background: var(--primary-color);
            color: var(--text-light);
            text-align: center;
            padding: 1rem;
        }
        
        @media (max-width: 768px) {
            .app-main {
                grid-template-columns: 1fr;
            }
            
            .sidebar {
                display: none;
            }
        }
    </style>
</head>
<body>
    <header class="app-header" role="banner">
        <div class="logo">
            <h1>Dashboard App</h1>
        </div>
        <nav aria-label="User navigation">
            <button>Profile</button>
            <button>Settings</button>
            <button>Logout</button>
        </nav>
    </header>
    
    <main class="app-main" role="main">
        <aside class="sidebar" role="complementary" aria-label="Main navigation">
            <nav>
                <ul>
                    <li><a href="#overview" aria-current="page">Overview</a></li>
                    <li><a href="#analytics">Analytics</a></li>
                    <li><a href="#reports">Reports</a></li>
                    <li><a href="#settings">Settings</a></li>
                    <li><a href="#help">Help & Support</a></li>
                </ul>
            </nav>
        </aside>
        
        <div class="content-area">
            <section class="content-section" aria-labelledby="welcome-heading">
                <h2 id="welcome-heading">Welcome to Your Dashboard</h2>
                <p>Here's an overview of your recent activity and key metrics.</p>
            </section>
            
            <section class="content-section" aria-labelledby="metrics-heading">
                <h3 id="metrics-heading">Key Metrics</h3>
                <div class="dashboard-grid">
                    <div class="metric-card">
                        <div class="metric-value">1,234</div>
                        <div class="metric-label">Total Users</div>
                    </div>
                    <div class="metric-card">
                        <div class="metric-value">$12,456</div>
                        <div class="metric-label">Revenue</div>
                    </div>
                    <div class="metric-card">
                        <div class="metric-value">89%</div>
                        <div class="metric-label">Satisfaction</div>
                    </div>
                    <div class="metric-card">
                        <div class="metric-value">42</div>
                        <div class="metric-label">New Signups</div>
                    </div>
                </div>
            </section>
            
            <section class="content-section" aria-labelledby="activity-heading">
                <h3 id="activity-heading">Recent Activity</h3>
                <div class="activity-list">
                    <article>
                        <h4>New User Registration</h4>
                        <p>John Doe signed up for the premium plan.</p>
                        <time datetime="2024-01-15T14:30:00Z">2 hours ago</time>
                    </article>
                    <article>
                        <h4>Payment Processed</h4>
                        <p>Monthly subscription payment received from Acme Corp.</p>
                        <time datetime="2024-01-15T12:15:00Z">4 hours ago</time>
                    </article>
                    <article>
                        <h4>Support Ticket Closed</h4>
                        <p>Issue #1234 has been resolved and closed.</p>
                        <time datetime="2024-01-15T09:45:00Z">7 hours ago</time>
                    </article>
                </div>
            </section>
        </div>
    </main>
    
    <footer class="app-footer" role="contentinfo">
        <p>&copy; 2024 Dashboard App. All rights reserved. | <a href="/privacy" style="color: var(--text-light);">Privacy Policy</a></p>
    </footer>
</body>
</html>
```

### Advanced Example: Multi-section Content with ARIA

This example demonstrates advanced usage with multiple content sections and enhanced accessibility.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Main Content Example</title>
    <style>
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --accent-color: #e74c3c;
            --text-dark: #2c3e50;
            --text-light: #ecf0f1;
            --spacing: 1rem;
        }
        
        .page-container {
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }
        
        .site-header {
            background: var(--primary-color);
            color: var(--text-light);
            padding: 1rem 2rem;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .main-content {
            flex: 1;
            display: grid;
            grid-template-columns: 1fr 300px;
            gap: 2rem;
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
            width: 100%;
            box-sizing: border-box;
        }
        
        .primary-content {
            min-width: 0; /* Prevents flexbox overflow issues */
        }
        
        .content-section {
            background: white;
            border-radius: 8px;
            padding: 2rem;
            margin-bottom: 2rem;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            border-left: 4px solid var(--secondary-color);
        }
        
        .content-section.featured {
            border-left-color: var(--accent-color);
            background: linear-gradient(135deg, #fff 0%, #f8f9fa 100%);
        }
        
        .sidebar {
            background: #f8f9fa;
            border-radius: 8px;
            padding: 1.5rem;
            height: fit-content;
            position: sticky;
            top: 2rem;
        }
        
        .tab-container {
            margin: 2rem 0;
        }
        
        .tab-buttons {
            display: flex;
            border-bottom: 2px solid #e9ecef;
            margin-bottom: 1rem;
        }
        
        .tab-button {
            padding: 1rem 1.5rem;
            background: none;
            border: none;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.3s ease;
        }
        
        .tab-button[aria-selected="true"] {
            border-bottom-color: var(--secondary-color);
            color: var(--secondary-color);
            font-weight: bold;
        }
        
        .tab-panel {
            display: none;
            padding: 1.5rem;
            background: #f8f9fa;
            border-radius: 0 0 8px 8px;
        }
        
        .tab-panel[aria-hidden="false"] {
            display: block;
        }
        
        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin: 1.5rem 0;
        }
        
        .card {
            background: white;
            border: 1px solid #e9ecef;
            border-radius: 6px;
            padding: 1.5rem;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .card:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
        }
        
        .site-footer {
            background: var(--primary-color);
            color: var(--text-light);
            text-align: center;
            padding: 2rem;
            margin-top: auto;
        }
        
        .breadcrumb {
            background: #f8f9fa;
            padding: 1rem 2rem;
            border-bottom: 1px solid #e9ecef;
        }
        
        .breadcrumb ol {
            list-style: none;
            padding: 0;
            margin: 0;
            display: flex;
            gap: 0.5rem;
        }
        
        .breadcrumb li:not(:last-child)::after {
            content: "›";
            margin-left: 0.5rem;
            color: #6c757d;
        }
        
        @media (max-width: 1024px) {
            .main-content {
                grid-template-columns: 1fr;
            }
            
            .sidebar {
                position: static;
                order: -1;
            }
        }
    </style>
</head>
<body class="page-container">
    <a href="#main-content" class="skip-link" style="position: absolute; top: -40px; left: 6px; background: #000; color: white; padding: 8px; z-index: 1000;">Skip to main content</a>
    
    <header class="site-header" role="banner">
        <div class="header-content" style="max-width: 1400px; margin: 0 auto; display: flex; justify-content: space-between; align-items: center;">
            <div class="logo">
                <h1 style="margin: 0;">Knowledge Base</h1>
            </div>
            <nav aria-label="Primary navigation">
                <a href="/" style="color: var(--text-light); margin: 0 1rem;">Home</a>
                <a href="/articles" style="color: var(--text-light); margin: 0 1rem;">Articles</a>
                <a href="/tutorials" style="color: var(--text-light); margin: 0 1rem;">Tutorials</a>
                <a href="/support" style="color: var(--text-light); margin: 0 1rem;">Support</a>
            </nav>
        </div>
    </header>
    
    <div class="breadcrumb" aria-label="Breadcrumb">
        <ol>
            <li><a href="/">Home</a></li>
            <li><a href="/web-development">Web Development</a></li>
            <li><a href="/html-guides">HTML Guides</a></li>
            <li aria-current="page">Semantic HTML</li>
        </ol>
    </div>
    
    <main id="main-content" class="main-content" role="main">
        <div class="primary-content">
            <article class="content-section featured">
                <header>
                    <h1>Understanding Semantic HTML5</h1>
                    <div class="article-meta" style="color: #6c757d; margin: 1rem 0;">
                        <span>By Sarah Developer</span> • 
                        <time datetime="2024-01-15">January 15, 2024</time> • 
                        <span>8 min read</span>
                    </div>
                </header>
                
                <section aria-labelledby="introduction-heading">
                    <h2 id="introduction-heading">Introduction to Semantic HTML</h2>
                    <p>Semantic HTML refers to using HTML elements that convey meaning about the content they contain. Unlike generic elements like <code>&lt;div&gt;</code> and <code>&lt;span&gt;</code>, semantic elements describe their purpose to both browsers and developers.</p>
                    
                    <div class="card-grid">
                        <div class="card">
                            <h3>Improved Accessibility</h3>
                            <p>Screen readers can better interpret and navigate semantically structured content.</p>
                        </div>
                        <div class="card">
                            <h3>Enhanced SEO</h3>
                            <p>Search engines prioritize content within semantic elements for better rankings.</p>
                        </div>
                        <div class="card">
                            <h3>Better Maintainability</h3>
                            <p>Semantic code is easier to read, understand, and maintain over time.</p>
                        </div>
                    </div>
                </section>
                
                <section aria-labelledby="elements-heading">
                    <h2 id="elements-heading">Key Semantic Elements</h2>
                    
                    <div class="tab-container">
                        <div class="tab-buttons" role="tablist" aria-label="HTML Elements">
                            <button class="tab-button" role="tab" aria-selected="true" aria-controls="structure-panel" id="structure-tab">
                                Structure
                            </button>
                            <button class="tab-button" role="tab" aria-selected="false" aria-controls="content-panel" id="content-tab">
                                Content
                            </button>
                            <button class="tab-button" role="tab" aria-selected="false" aria-controls="text-panel" id="text-tab">
                                Text Semantics
                            </button>
                        </div>
                        
                        <div class="tab-panel" role="tabpanel" aria-hidden="false" aria-labelledby="structure-tab" id="structure-panel">
                            <h3>Structural Elements</h3>
                            <ul>
                                <li><code>&lt;header&gt;</code> - Introductory content</li>
                                <li><code>&lt;nav&gt;</code> - Navigation links</li>
                                <li><code>&lt;main&gt;</code> - Dominant content</li>
                                <li><code>&lt;article&gt;</code> - Self-contained composition</li>
                                <li><code>&lt;section&gt;</code> - Thematic grouping</li>
                                <li><code>&lt;aside&gt;</code> - Tangentially related content</li>
                                <li><code>&lt;footer&gt;</code> - Closing content</li>
                            </ul>
                        </div>
                        
                        <div class="tab-panel" role="tabpanel" aria-hidden="true" aria-labelledby="content-tab" id="content-panel">
                            <h3>Content Elements</h3>
                            <p>Content-specific semantic elements...</p>
                        </div>
                        
                        <div class="tab-panel" role="tabpanel" aria-hidden="true" aria-labelledby="text-tab" id="text-panel">
                            <h3>Text Semantic Elements</h3>
                            <p>Inline semantic elements for text...</p>
                        </div>
                    </div>
                </section>
            </article>
            
            <section class="content-section" aria-labelledby="best-practices-heading">
                <h2 id="best-practices-heading">Best Practices</h2>
                <p>Follow these guidelines when using semantic HTML elements:</p>
                <ul>
                    <li>Use one <code>&lt;main&gt;</code> element per page for the primary content</li>
                    <li>Ensure proper heading hierarchy within sections</li>
                    <li>Use <code>&lt;article&gt;</code> for content that could stand alone</li>
                    <li>Employ <code>&lt;section&gt;</code> for thematic groupings with headings</li>
                    <li>Include ARIA landmarks when needed for complex widgets</li>
                </ul>
            </section>
        </div>
        
        <aside class="sidebar" role="complementary" aria-label="Additional resources">
            <section aria-labelledby="related-heading">
                <h3 id="related-heading">Related Articles</h3>
                <nav aria-label="Related articles">
                    <ul style="list-style: none; padding: 0;">
                        <li style="margin: 0.5rem 0;"><a href="/css-grid-guide">CSS Grid Layout Complete Guide</a></li>
                        <li style="margin: 0.5rem 0;"><a href="/accessibility-basics">Web Accessibility Fundamentals</a></li>
                        <li style="margin: 0.5rem 0;"><a href="/responsive-design">Responsive Design Principles</a></li>
                        <li style="margin: 0.5rem 0;"><a href="/performance-optimization">Web Performance Optimization</a></li>
                    </ul>
                </nav>
            </section>
            
            <section aria-labelledby="toc-heading" style="margin-top: 2rem;">
                <h3 id="toc-heading">Table of Contents</h3>
                <nav aria-label="Page sections">
                    <ol style="padding-left: 1.5rem;">
                        <li><a href="#introduction-heading">Introduction</a></li>
                        <li><a href="#elements-heading">Key Semantic Elements</a></li>
                        <li><a href="#best-practices-heading">Best Practices</a></li>
                    </ol>
                </nav>
            </section>
        </aside>
    </main>
    
    <footer class="site-footer" role="contentinfo">
        <div style="max-width: 1400px; margin: 0 auto;">
            <p>&copy; 2024 Knowledge Base. All rights reserved.</p>
            <nav aria-label="Footer links">
                <a href="/privacy" style="color: var(--text-light); margin: 0 1rem;">Privacy Policy</a>
                <a href="/terms" style="color: var(--text-light); margin: 0 1rem;">Terms of Service</a>
                <a href="/contact" style="color: var(--text-light); margin: 0 1rem;">Contact Us</a>
            </nav>
        </div>
    </footer>

    <script>
        // Tab functionality
        document.querySelectorAll('.tab-button').forEach(button => {
            button.addEventListener('click', () => {
                const tabId = button.id.replace('-tab', '-panel');
                
                // Update tab buttons
                document.querySelectorAll('.tab-button').forEach(btn => {
                    btn.setAttribute('aria-selected', 'false');
                });
                button.setAttribute('aria-selected', 'true');
                
                // Update tab panels
                document.querySelectorAll('.tab-panel').forEach(panel => {
                    panel.setAttribute('aria-hidden', 'true');
                    panel.style.display = 'none';
                });
                
                const activePanel = document.getElementById(tabId);
                activePanel.setAttribute('aria-hidden', 'false');
                activePanel.style.display = 'block';
            });
        });
    </script>
</body>
</html>
```

### Specialized Example: Single Page Application Main Content

This example shows main used in a single page application context.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SPA Main Content Example</title>
    <style>
        .spa-container {
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }
        
        .spa-header {
            background: #2c3e50;
            color: white;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .spa-main {
            flex: 1;
            padding: 0;
            position: relative;
        }
        
        .view {
            display: none;
            padding: 2rem;
            max-width: 1200px;
            margin: 0 auto;
            animation: fadeIn 0.3s ease;
        }
        
        .view.active {
            display: block;
        }
        
        .dashboard-view {
            background: #f8f9fa;
        }
        
        .profile-view {
            background: #fff;
        }
        
        .settings-view {
            background: #f0f8ff;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin: 2rem 0;
        }
        
        .stat-card {
            background: white;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            text-align: center;
        }
        
        .nav-tabs {
            display: flex;
            border-bottom: 2px solid #e9ecef;
            margin-bottom: 2rem;
        }
        
        .nav-tab {
            padding: 1rem 1.5rem;
            background: none;
            border: none;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.3s ease;
        }
        
        .nav-tab.active {
            border-bottom-color: #3498db;
            color: #3498db;
            font-weight: bold;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .loading {
            opacity: 0.6;
            pointer-events: none;
        }
    </style>
</head>
<body class="spa-container">
    <header class="spa-header" role="banner">
        <h1>Single Page Application</h1>
        <nav aria-label="Application navigation">
            <button class="nav-tab active" data-view="dashboard">Dashboard</button>
            <button class="nav-tab" data-view="profile">Profile</button>
            <button class="nav-tab" data-view="settings">Settings</button>
        </nav>
    </header>
    
    <main class="spa-main" role="main">
        <!-- Dashboard View -->
        <section id="dashboard-view" class="view dashboard-view active" aria-labelledby="dashboard-heading">
            <h2 id="dashboard-heading">Dashboard Overview</h2>
            <p>Welcome to your application dashboard. Here's an overview of your current status and activities.</p>
            
            <div class="stats-grid">
                <div class="stat-card">
                    <h3>Projects</h3>
                    <div style="font-size: 2.5rem; font-weight: bold; color: #2c3e50;">12</div>
                    <p>Active projects</p>
                </div>
                <div class="stat-card">
                    <h3>Tasks</h3>
                    <div style="font-size: 2.5rem; font-weight: bold; color: #2c3e50;">47</div>
                    <p>Pending tasks</p>
                </div>
                <div class="stat-card">
                    <h3>Team</h3>
                    <div style="font-size: 2.5rem; font-weight: bold; color: #2c3e50;">8</div>
                    <p>Team members</p>
                </div>
            </div>
            
            <section aria-labelledby="recent-activity-heading">
                <h3 id="recent-activity-heading">Recent Activity</h3>
                <div class="activity-list">
                    <article>
                        <h4>Project Update</h4>
                        <p>Frontend redesign completed and deployed to staging.</p>
                        <time datetime="2024-01-15T10:30:00Z">2 hours ago</time>
                    </article>
                    <article>
                        <h4>New Team Member</h4>
                        <p>Sarah Johnson joined the development team.</p>
                        <time datetime="2024-01-14T14:15:00Z">Yesterday</time>
                    </article>
                </div>
            </section>
        </section>
        
        <!-- Profile View -->
        <section id="profile-view" class="view profile-view" aria-labelledby="profile-heading" hidden>
            <h2 id="profile-heading">User Profile</h2>
            <div style="display: flex; gap: 2rem; align-items: flex-start;">
                <div style="width: 100px; height: 100px; background: #3498db; border-radius: 50%; display: flex; align-items: center; justify-content: center; color: white; font-size: 2rem;">
                    JD
                </div>
                <div>
                    <h3>John Doe</h3>
                    <p>Software Developer</p>
                    <p>Member since January 2023</p>
                </div>
            </div>
            
            <section aria-labelledby="preferences-heading" style="margin-top: 2rem;">
                <h3 id="preferences-heading">Preferences</h3>
                <form>
                    <label>
                        <input type="checkbox" checked> Email notifications
                    </label>
                    <label>
                        <input type="checkbox"> Dark mode
                    </label>
                    <label>
                        <input type="checkbox" checked> Weekly digest
                    </label>
                </form>
            </section>
        </section>
        
        <!-- Settings View -->
        <section id="settings-view" class="view settings-view" aria-labelledby="settings-heading" hidden>
            <h2 id="settings-heading">Application Settings</h2>
            <p>Configure your application preferences and security settings.</p>
            
            <section aria-labelledby="security-heading">
                <h3 id="security-heading">Security</h3>
                <form>
                    <div style="margin: 1rem 0;">
                        <label for="current-password">Current Password</label>
                        <input type="password" id="current-password" style="display: block; width: 100%; max-width: 300px; padding: 0.5rem; margin: 0.5rem 0;">
                    </div>
                    <div style="margin: 1rem 0;">
                        <label for="new-password">New Password</label>
                        <input type="password" id="new-password" style="display: block; width: 100%; max-width: 300px; padding: 0.5rem; margin: 0.5rem 0;">
                    </div>
                    <button type="submit">Update Password</button>
                </form>
            </section>
            
            <section aria-labelledby="privacy-heading" style="margin-top: 2rem;">
                <h3 id="privacy-heading">Privacy</h3>
                <form>
                    <label>
                        <input type="radio" name="data-collection" checked> Basic data collection
                    </label>
                    <label>
                        <input type="radio" name="data-collection"> Enhanced data collection
                    </label>
                    <label>
                        <input type="radio" name="data-collection"> Minimal data collection
                    </label>
                </form>
            </section>
        </section>
    </main>
    
    <footer style="background: #34495e; color: white; text-align: center; padding: 1rem;">
        <p>&copy; 2024 SPA Example. All rights reserved.</p>
    </footer>

    <script>
        // View switching functionality
        document.querySelectorAll('.nav-tab').forEach(tab => {
            tab.addEventListener('click', () => {
                const viewId = tab.dataset.view + '-view';
                
                // Update active tab
                document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
                tab.classList.add('active');
                
                // Update active view
                document.querySelectorAll('.view').forEach(view => {
                    view.classList.remove('active');
                    view.setAttribute('hidden', '');
                });
                
                const activeView = document.getElementById(viewId);
                activeView.classList.add('active');
                activeView.removeAttribute('hidden');
                
                // Update page title and ARIA
                document.title = `${tab.textContent} - SPA Example`;
            });
        });
    </script>
</body>
</html>
```

---

## Notes

* **When to Use `<main>` vs Other Sectioning Elements**:

  - Use `<main>` for the **primary, unique content** of the entire document
  - Use `<article>` for **self-contained, reusable content** within the main content
  - Use `<section>` for **thematic groupings** within articles or main content
  - Use `<div>` for **styling containers** without semantic meaning

* **Accessibility Best Practices**:

  - The element automatically has `role="main"` for screen readers
  - Include a "skip to main content" link for keyboard users
  - Ensure the main content starts with a heading (`<h1>` typically)
  - Use landmark roles appropriately for other page sections
  - Test with screen readers to verify proper navigation

* **SEO Considerations**:

  - Search engines prioritize content within the main element
  - Ensure main content contains relevant, high-quality content
  - Use proper heading hierarchy within main
  - Include structured data markup when appropriate
  - Avoid keyword stuffing - focus on natural, valuable content

* **Common Pitfalls**:

  - Using multiple main elements on a single page
  - Including repeated content (navigation, headers, footers) within main
  - Nesting main within other semantic elements
  - Forgetting to include a skip navigation link
  - Using main for content that isn't the primary focus of the page

* **Browser Support**:

  - Excellent support in all modern browsers
  - Internet Explorer 11 and above support the element
  - The implicit `role="main"` is well-supported in modern screen readers
  - No compatibility issues or polyfills needed

* **Best Practices**:

  - Use exactly one main element per document
  - Place main after header and before footer elements
  - Start main content with an appropriate heading
  - Include unique, valuable content that addresses the page's purpose
  - Use sectioning elements within main for better organization
  - Test accessibility with screen readers and keyboard navigation
  - Ensure main content is clearly distinguishable from other page areas

---
