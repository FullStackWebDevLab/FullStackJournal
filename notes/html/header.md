# `<header>`

## Key Topics

+ [Definition and Purpose](#definition-and-purpose)
+ [Syntax and Variants](#syntax-and-variants)
+ [Attributes](#attributes)
+ [Content Model](#content-model)
+ [Context](#context)
+ [Behavior and Semantics](#behavior-and-sematics)
+ [Examples](#examples)
+ [Notes](#notes)

---

## Definition and Purpose

The `<header>` tag represents introductory content or navigational aids for its nearest ancestor sectioning content or sectioning root element. Typically containing heading elements, logos, search forms, navigation menus, or author information, this element serves as a semantic container for content that introduces or helps navigate through a document, page, or section.

---

## Syntax & Variants

+ The `<header>` tag requires both an opening `<header>` and closing `</header>` tag.
+ It is a non-void element that serves as a container for introductory and navigational content.
+ No alternative or legacy forms exist, as this is an HTML5 semantic element.

---

## Attributes

The `<header>` tag supports only **global attributes** with no specific attributes of its own:

**Global Attributes:**
- `id`: Useful for creating unique identifiers for headers, enabling direct linking and JavaScript targeting
- `class`, `style`: For CSS styling and visual presentation
- `data-*`: For custom data attributes to store header-specific information
- `aria-*`: For enhanced accessibility semantics, such as `aria-label` for unlabeled headers or `role="banner"` when used as the main page header
- `lang`, `dir`: For language and text direction specific to the header content
- `title`: For advisory information about the header

**Important Notes:**
- No required attributes
- The `id` attribute is commonly used for skip navigation links and JavaScript targeting
- When used as the main page header (direct child of `<body>`), it implicitly has `role="banner"`
- Multiple headers can exist on a page, each scoped to its parent section

---

## Content Model

The `<header>` element can contain **flow content**, but it must not contain `<header>`, `<footer>`, or another `<main>` element as descendants:

**Permitted Content:**
- Heading elements (`<h1>`-`<h6>`) - commonly used for page or section titles
- Navigation elements (`<nav>`) - for primary or secondary navigation
- Logos and branding images (`<img>`, `<svg>`)
- Search forms (`<form>`, `<input type="search">`)
- Author information and publication dates
- Table of contents or breadcrumb navigation
- Social media links or contact information
- Generic containers (`<div>`, `<span>`) for layout purposes

**Restrictions:**
- Cannot contain `<header>`, `<footer>`, or `<main>` elements
- Should not be nested within another `<header>` element
- Typically should not contain the main content of the page/section

---

## Context

+ **Placement**: Can be placed within any sectioning content or sectioning root element, including `<body>`, `<article>`, `<section>`, `<aside>`, `<nav>`, and `<main>` .
+ **Parent Elements**: `<body>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<div>`, and other container elements
+ **Scoping**: The header's semantic meaning is scoped to its nearest sectioning ancestor
+ **Usage Limits**: 
  - Multiple `<header>` elements are permitted on a page, each associated with its parent section
  - Only one `<header>` should be used as the main page banner (direct child of `<body>`)
  - Headers can be nested within different sectioning elements throughout the document

---

## Behavior and Semantics

+ **Rendering**: The `<header>` tag is a **block-level element** that creates line breaks before and after its content.
+ **Default CSS**: Browsers apply minimal default styling:
  ```css
  header {
    display: block;
  }
  ```
+ **Semantic Impact**:
  - **Accessibility**: Screen readers recognize headers as landmark regions, improving navigation for visually impaired users
  - **SEO**: Search engines use header content to understand page structure and identify important introductory information
  - **Document Structure**: Provides clear semantic meaning for introductory content sections
  - **User Experience**: Helps users quickly identify the purpose and navigation options for each section

---

## Examples

### Basic Example: Main Page Header

This example demonstrates a typical main page header with navigation and branding.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Basic Header Example</title>
    <style>
        .main-header {
            background: #2c3e50;
            color: white;
            padding: 1rem 2rem;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .header-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            text-decoration: none;
            color: white;
        }
        
        .main-nav ul {
            display: flex;
            list-style: none;
            margin: 0;
            padding: 0;
            gap: 2rem;
        }
        
        .main-nav a {
            color: white;
            text-decoration: none;
            transition: color 0.3s ease;
        }
        
        .main-nav a:hover {
            color: #3498db;
        }
        
        .search-form {
            display: flex;
            gap: 0.5rem;
        }
        
        .search-input {
            padding: 0.5rem;
            border: 1px solid #34495e;
            border-radius: 4px;
            background: #34495e;
            color: white;
        }
        
        .search-input::placeholder {
            color: #bdc3c7;
        }
    </style>
</head>
<body>
    <header class="main-header" role="banner">
        <div class="header-content">
            <div class="branding">
                <a href="/" class="logo">Company Name</a>
            </div>
            
            <nav class="main-nav" aria-label="Main navigation">
                <ul>
                    <li><a href="/">Home</a></li>
                    <li><a href="/about">About</a></li>
                    <li><a href="/services">Services</a></li>
                    <li><a href="/blog">Blog</a></li>
                    <li><a href="/contact">Contact</a></li>
                </ul>
            </nav>
            
            <form class="search-form" role="search">
                <input type="search" class="search-input" placeholder="Search..." aria-label="Search website">
                <button type="submit">Search</button>
            </form>
        </div>
    </header>
    
    <main>
        <h1>Welcome to Our Website</h1>
        <p>Main content goes here...</p>
    </main>
</body>
</html>
```

### Intermediate Example: Multiple Headers in Different Contexts

This example shows headers used at different levels throughout a document.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Multiple Headers Example</title>
    <style>
        .page-header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 2rem;
            text-align: center;
        }
        
        .article-header {
            background: #f8f9fa;
            padding: 2rem;
            border-bottom: 3px solid #3498db;
            margin-bottom: 2rem;
        }
        
        .section-header {
            background: #e3f2fd;
            padding: 1rem 1.5rem;
            border-left: 4px solid #2196f3;
            margin: 2rem 0;
        }
        
        .meta-info {
            color: #666;
            font-size: 0.9rem;
            margin-top: 1rem;
        }
        
        .tag {
            display: inline-block;
            background: #e3f2fd;
            color: #1976d2;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            font-size: 0.8rem;
            margin-right: 0.5rem;
        }
    </style>
</head>
<body>
    <!-- Main page header -->
    <header class="page-header" role="banner">
        <h1>Tech Blog</h1>
        <p>Latest insights and tutorials on web development</p>
        <nav aria-label="Primary navigation">
            <a href="/">Home</a> |
            <a href="/categories">Categories</a> |
            <a href="/about">About</a> |
            <a href="/contact">Contact</a>
        </nav>
    </header>
    
    <main>
        <article>
            <!-- Article-specific header -->
            <header class="article-header">
                <h1>Understanding Semantic HTML5</h1>
                <div class="meta-info">
                    <span>By <strong>Sarah Developer</strong></span> • 
                    <time datetime="2024-01-15">January 15, 2024</time> • 
                    <span>8 min read</span>
                </div>
                <div class="tags">
                    <span class="tag">HTML5</span>
                    <span class="tag">Semantic Web</span>
                    <span class="tag">Accessibility</span>
                </div>
            </header>
            
            <div class="article-content">
                <p>Semantic HTML5 elements provide meaning to web content beyond just presentation...</p>
                
                <section>
                    <!-- Section header within article -->
                    <header class="section-header">
                        <h2>Benefits of Semantic HTML</h2>
                        <p>Why you should care about semantic markup</p>
                    </header>
                    <p>Using semantic elements improves accessibility, SEO, and maintainability...</p>
                </section>
                
                <section>
                    <header class="section-header">
                        <h2>Common Semantic Elements</h2>
                        <p>Key elements and their proper usage</p>
                    </header>
                    <p>Here are some of the most important semantic elements in HTML5...</p>
                </section>
            </div>
        </article>
        
        <aside>
            <!-- Header for sidebar section -->
            <header>
                <h2>Related Articles</h2>
            </header>
            <ul>
                <li><a href="/css-grid-guide">Complete Guide to CSS Grid</a></li>
                <li><a href="/responsive-design">Responsive Design Principles</a></li>
                <li><a href="/web-accessibility">Web Accessibility Fundamentals</a></li>
            </ul>
        </aside>
    </main>
</body>
</html>
```

### Advanced Example: Complex Header with Responsive Design

This example demonstrates a sophisticated header with responsive behavior and multiple features.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Header Example</title>
    <style>
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --text-light: #ecf0f1;
            --spacing: 1rem;
        }
        
        .main-header {
            background: var(--primary-color);
            color: var(--text-light);
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .header-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 var(--spacing);
        }
        
        .header-top {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            text-decoration: none;
            color: var(--text-light);
            font-size: 1.5rem;
            font-weight: bold;
        }
        
        .logo-icon {
            width: 32px;
            height: 32px;
            background: var(--secondary-color);
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .nav-container {
            display: flex;
            align-items: center;
            gap: 2rem;
        }
        
        .main-nav ul {
            display: flex;
            list-style: none;
            margin: 0;
            padding: 0;
            gap: 1.5rem;
        }
        
        .main-nav a {
            color: var(--text-light);
            text-decoration: none;
            padding: 0.5rem 0;
            position: relative;
            transition: color 0.3s ease;
        }
        
        .main-nav a:hover {
            color: var(--secondary-color);
        }
        
        .main-nav a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--secondary-color);
            transition: width 0.3s ease;
        }
        
        .main-nav a:hover::after {
            width: 100%;
        }
        
        .header-actions {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .search-toggle, .menu-toggle {
            background: none;
            border: none;
            color: var(--text-light);
            cursor: pointer;
            padding: 0.5rem;
        }
        
        .search-form {
            display: none;
            padding: 1rem 0;
            border-top: 1px solid #34495e;
        }
        
        .search-form.active {
            display: block;
        }
        
        .search-input {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #34495e;
            border-radius: 4px;
            background: #34495e;
            color: var(--text-light);
            font-size: 1rem;
        }
        
        .mobile-nav {
            display: none;
            background: #34495e;
            padding: 1rem;
        }
        
        .mobile-nav.active {
            display: block;
        }
        
        .mobile-nav ul {
            list-style: none;
            margin: 0;
            padding: 0;
        }
        
        .mobile-nav li {
            margin: 0.5rem 0;
        }
        
        .mobile-nav a {
            color: var(--text-light);
            text-decoration: none;
            display: block;
            padding: 0.5rem;
        }
        
        /* Responsive design */
        @media (max-width: 768px) {
            .main-nav {
                display: none;
            }
            
            .menu-toggle {
                display: block;
            }
        }
        
        @media (min-width: 769px) {
            .menu-toggle {
                display: none;
            }
            
            .mobile-nav {
                display: none !important;
            }
        }
    </style>
</head>
<body>
    <header class="main-header" role="banner">
        <div class="header-container">
            <div class="header-top">
                <a href="/" class="logo">
                    <div class="logo-icon">C</div>
                    <span>Company</span>
                </a>
                
                <div class="nav-container">
                    <nav class="main-nav" aria-label="Main navigation">
                        <ul>
                            <li><a href="/products">Products</a></li>
                            <li><a href="/solutions">Solutions</a></li>
                            <li><a href="/pricing">Pricing</a></li>
                            <li><a href="/docs">Documentation</a></li>
                            <li><a href="/support">Support</a></li>
                        </ul>
                    </nav>
                    
                    <div class="header-actions">
                        <button class="search-toggle" aria-label="Toggle search">
                            🔍
                        </button>
                        <button class="menu-toggle" aria-label="Toggle menu">
                            ☰
                        </button>
                    </div>
                </div>
            </div>
            
            <form class="search-form" role="search">
                <input type="search" class="search-input" placeholder="Search products, documentation, support..." aria-label="Search website">
            </form>
            
            <nav class="mobile-nav" aria-label="Mobile navigation">
                <ul>
                    <li><a href="/products">Products</a></li>
                    <li><a href="/solutions">Solutions</a></li>
                    <li><a href="/pricing">Pricing</a></li>
                    <li><a href="/docs">Documentation</a></li>
                    <li><a href="/support">Support</a></li>
                </ul>
            </nav>
        </div>
    </header>
    
    <main style="padding: 2rem;">
        <h1>Welcome to Our Platform</h1>
        <p>Main content goes here...</p>
    </main>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const searchToggle = document.querySelector('.search-toggle');
            const searchForm = document.querySelector('.search-form');
            const menuToggle = document.querySelector('.menu-toggle');
            const mobileNav = document.querySelector('.mobile-nav');
            
            searchToggle.addEventListener('click', function() {
                searchForm.classList.toggle('active');
                if (searchForm.classList.contains('active')) {
                    searchForm.querySelector('.search-input').focus();
                }
            });
            
            menuToggle.addEventListener('click', function() {
                mobileNav.classList.toggle('active');
            });
        });
    </script>
</body>
</html>
```

### Specialized Example: Article Header with Rich Metadata

This example shows a detailed article header with comprehensive metadata and social features.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Article Header Example</title>
    <style>
        .article-header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 3rem 2rem;
            margin-bottom: 2rem;
        }
        
        .header-content {
            max-width: 800px;
            margin: 0 auto;
        }
        
        .article-title {
            font-size: 2.5rem;
            margin: 0 0 1rem 0;
            line-height: 1.2;
        }
        
        .article-subtitle {
            font-size: 1.25rem;
            opacity: 0.9;
            margin: 0 0 2rem 0;
            font-weight: normal;
        }
        
        .article-meta {
            display: flex;
            flex-wrap: wrap;
            gap: 2rem;
            align-items: center;
            margin-bottom: 2rem;
        }
        
        .author-info {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .author-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(255,255,255,0.2);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }
        
        .author-details h3 {
            margin: 0;
            font-size: 1.1rem;
        }
        
        .author-details p {
            margin: 0;
            opacity: 0.8;
            font-size: 0.9rem;
        }
        
        .reading-stats {
            display: flex;
            gap: 1rem;
        }
        
        .stat {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.9rem;
        }
        
        .article-actions {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }
        
        .action-btn {
            background: rgba(255,255,255,0.2);
            border: 1px solid rgba(255,255,255,0.3);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            transition: background 0.3s ease;
        }
        
        .action-btn:hover {
            background: rgba(255,255,255,0.3);
        }
        
        .tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-top: 1rem;
        }
        
        .tag {
            background: rgba(255,255,255,0.2);
            padding: 0.25rem 0.75rem;
            border-radius: 20px;
            font-size: 0.8rem;
        }
    </style>
</head>
<body>
    <article>
        <header class="article-header">
            <div class="header-content">
                <h1 class="article-title">The Future of Web Development: Trends to Watch in 2024</h1>
                <p class="article-subtitle">Exploring the technologies and methodologies that will shape the next generation of web experiences</p>
                
                <div class="article-meta">
                    <div class="author-info">
                        <div class="author-avatar">AJ</div>
                        <div class="author-details">
                            <h3>Alex Johnson</h3>
                            <p>Senior Frontend Developer • Published January 15, 2024</p>
                        </div>
                    </div>
                    
                    <div class="reading-stats">
                        <div class="stat">⏱️ 8 min read</div>
                        <div class="stat">👁️ 2.4K views</div>
                        <div class="stat">💬 42 comments</div>
                    </div>
                </div>
                
                <div class="article-actions">
                    <button class="action-btn">👍 Like</button>
                    <button class="action-btn">🔖 Bookmark</button>
                    <button class="action-btn">📤 Share</button>
                    <button class="action-btn">📧 Subscribe</button>
                </div>
                
                <div class="tags">
                    <span class="tag">Web Development</span>
                    <span class="tag">Trends 2024</span>
                    <span class="tag">JavaScript</span>
                    <span class="tag">React</span>
                    <span class="tag">Web3</span>
                    <span class="tag">AI</span>
                </div>
            </div>
        </header>
        
        <div class="article-content" style="max-width: 800px; margin: 0 auto; padding: 0 2rem;">
            <p>Article content begins here...</p>
        </div>
    </article>
</body>
</html>
```

---

## Notes

* **When to Use `<header>` vs `<div>`**:

  - Use `<header>` for **introductory content** or **navigational aids** at the beginning of sections
  - Use `<div>` for **generic containers** without semantic meaning
  - If the content introduces a section or provides navigation for it, use `<header>`

* **Multiple Headers on a Page**:

  - A page can have multiple `<header>` elements, each scoped to its parent section
  - Only one `<header>` should be the main page banner (direct child of `<body>`)
  - Headers within `<article>`, `<section>`, or `<aside>` are scoped to those elements

* **Accessibility Best Practices**:

  - The main page header (direct child of `<body>`) implicitly has `role="banner"`
  - Use `aria-label` or `aria-labelledby` for headers without visible text labels
  - Ensure headers contain appropriate heading elements for screen reader navigation
  - Use landmark roles appropriately when headers serve specific purposes
 
* **SEO Considerations**:
 
  - Header content helps search engines understand page structure and importance
  - Important keywords in headers can improve content relevance
  - Avoid keyword stuffing in header content
  - Ensure header content accurately represents the section it introduces

* **Common Pitfalls**:

  - Using `<header>` as a generic wrapper for any top content
  - Nesting headers within headers (invalid structure)
  - Creating headers without proper heading elements
  - Using multiple main page headers (should only have one banner role)

* **Browser Support**:

  - Excellent support in all modern browsers
  - Internet Explorer 9+ supports `<header>` with basic styling
  - The implicit `role="banner"` is well-supported in modern screen readers

* **Best Practices**:

  - Include at least one heading element (`<h1>`-`<h6>`) in each header
  - Use the main page header for site-wide navigation and branding
  - Scope headers appropriately to their parent sections
  - Keep header content relevant to the section it introduces
  - Use ARIA attributes when the native semantics need enhancement
  - Test header structure with screen readers and accessibility tools

---
