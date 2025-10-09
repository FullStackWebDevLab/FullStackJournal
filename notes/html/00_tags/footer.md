# `<footer>` 

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

The `<footer>` tag represents a footer for its nearest ancestor sectioning content or sectioning root element, typically containing metadata, copyright information, related documents, contact details, or navigation links for a specific section or the entire document. This element serves as a semantic container for content that concludes or provides supplementary information about a page, article, or section.

---

## Syntax and Variants

+ The `<footer>` tag requires both an opening `<footer>` and closing `</footer>` tag.
+ It is a non-void element that serves as a container for concluding and supplementary content.
+ No alternative or legacy forms exist, as this is an HTML5 semantic element.

---

## Attributes

The `<footer>` tag supports only **global attributes** with no specific attributes of its own:

**Global Attributes:**
- `id`: Useful for creating unique identifiers for footers, enabling direct linking and JavaScript targeting
- `class`, `style`: For CSS styling and visual presentation
- `data-*`: For custom data attributes to store footer-specific information
- `aria-*`: For enhanced accessibility semantics, such as `aria-label` for unlabeled footers or `role="contentinfo"` when used as the main page footer
- `lang`, `dir`: For language and text direction specific to the footer content
- `title`: For advisory information about the footer

**Important Notes:**
- No required attributes
- The `id` attribute is commonly used for JavaScript targeting and styling
- When used as the main page footer (direct child of `<body>`), it implicitly has `role="contentinfo"`
- Multiple footers can exist on a page, each scoped to its parent section

---

## Content Model

The `<footer>` element can contain **flow content**, but it must not contain `<header>`, `<footer>`, or `<main>` element as descendants:

**Permitted Content:**
- Copyright notices and legal information
- Contact information (`<address>` element)
- Navigation links (`<nav>`) - for secondary navigation
- Social media links and icons
- Sitemap links or related documents
- Author information and publication dates
- Back-to-top links
- Attribution and credit information
- Generic containers (`<div>`, `<span>`) for layout purposes

**Restrictions:**
- Cannot contain `<header>`, `<footer>`, or `<main>` elements
- Should not be nested within another `<footer>` element
- Typically should not contain the main content of the page/section
- Contact information should typically use the `<address>` element

---

## Context

+ **Placement**: Can be placed within any sectioning content or sectioning root element, including `<body>`, `<article>`, `<section>`, `<aside>`, `<nav>`, and `<main>` .
+ **Parent Elements**: `<body>`, `<main>`, `<article>`, `<section>`, `<aside>`, `<div>`, and other container elements
+ **Scoping**: The footer's semantic meaning is scoped to its nearest sectioning ancestor
+ **Usage Limits**: 
  - Multiple `<footer>` elements are permitted on a page, each associated with its parent section
  - Only one `<footer>` should be used as the main page footer (direct child of `<body>`)
  - Footers can be nested within different sectioning elements throughout the document

---

## Behavior and Semantics

+ **Rendering**: The `<footer>` tag is a **block-level element** that creates line breaks before and after its content.
+ **Default CSS**: Browsers apply minimal default styling:
  ```css
  footer {
    display: block;
  }
  ```
+ **Semantic Impact**:
  - **Accessibility**: Screen readers recognize footers as landmark regions, improving navigation for visually impaired users
  - **SEO**: Search engines use footer content to understand supplementary information and site structure
  - **Document Structure**: Provides clear semantic meaning for concluding content sections
  - **User Experience**: Helps users find important supplementary information and navigation options

---

## Examples

### Basic Example: Main Page Footer

This example demonstrates a typical main page footer with common elements.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Basic Footer Example</title>
    <style>
        .main-footer {
            background: #2c3e50;
            color: #ecf0f1;
            padding: 2rem 1rem;
            margin-top: 3rem;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }
        
        .footer-section h3 {
            color: #3498db;
            margin-bottom: 1rem;
            font-size: 1.1rem;
        }
        
        .footer-links {
            list-style: none;
            padding: 0;
            margin: 0;
        }
        
        .footer-links li {
            margin-bottom: 0.5rem;
        }
        
        .footer-links a {
            color: #bdc3c7;
            text-decoration: none;
            transition: color 0.3s ease;
        }
        
        .footer-links a:hover {
            color: #3498db;
        }
        
        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }
        
        .social-link {
            color: #bdc3c7;
            text-decoration: none;
            transition: color 0.3s ease;
        }
        
        .social-link:hover {
            color: #3498db;
        }
        
        .footer-bottom {
            max-width: 1200px;
            margin: 2rem auto 0;
            padding-top: 1rem;
            border-top: 1px solid #34495e;
            text-align: center;
            color: #95a5a6;
            font-size: 0.9rem;
        }
    </style>
</head>
<body>
    <main>
        <h1>Welcome to Our Website</h1>
        <p>Main content goes here...</p>
    </main>

    <footer class="main-footer" role="contentinfo">
        <div class="footer-content">
            <div class="footer-section">
                <h3>About Us</h3>
                <p>We are a company dedicated to creating amazing web experiences with semantic HTML and modern CSS.</p>
                <div class="social-links">
                    <a href="#" class="social-link" aria-label="Twitter">🐦 Twitter</a>
                    <a href="#" class="social-link" aria-label="GitHub">🐙 GitHub</a>
                    <a href="#" class="social-link" aria-label="LinkedIn">💼 LinkedIn</a>
                </div>
            </div>
            
            <div class="footer-section">
                <h3>Quick Links</h3>
                <ul class="footer-links">
                    <li><a href="/">Home</a></li>
                    <li><a href="/about">About</a></li>
                    <li><a href="/services">Services</a></li>
                    <li><a href="/blog">Blog</a></li>
                    <li><a href="/contact">Contact</a></li>
                </ul>
            </div>
            
            <div class="footer-section">
                <h3>Resources</h3>
                <ul class="footer-links">
                    <li><a href="/documentation">Documentation</a></li>
                    <li><a href="/tutorials">Tutorials</a></li>
                    <li><a href="/support">Support</a></li>
                    <li><a href="/faq">FAQ</a></li>
                </ul>
            </div>
            
            <div class="footer-section">
                <h3>Contact Info</h3>
                <address>
                    <p>123 Web Street<br>Digital City, DC 10101</p>
                    <p>Email: <a href="mailto:info@example.com">info@example.com</a></p>
                    <p>Phone: <a href="tel:+15551234567">(555) 123-4567</a></p>
                </address>
            </div>
        </div>
        
        <div class="footer-bottom">
            <p>&copy; 2024 Company Name. All rights reserved. | <a href="/privacy">Privacy Policy</a> | <a href="/terms">Terms of Service</a></p>
        </div>
    </footer>
</body>
</html>
```

### Intermediate Example: Multiple Footers in Different Contexts

This example shows footers used at different levels throughout a document.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Multiple Footers Example</title>
    <style>
        .page-footer {
            background: #34495e;
            color: white;
            padding: 2rem;
            margin-top: 3rem;
        }
        
        .article-footer {
            background: #f8f9fa;
            padding: 1.5rem;
            border-top: 3px solid #3498db;
            margin-top: 2rem;
        }
        
        .section-footer {
            background: #e3f2fd;
            padding: 1rem;
            border-left: 4px solid #2196f3;
            margin: 2rem 0;
            font-size: 0.9rem;
        }
        
        .meta-info {
            color: #666;
            margin-bottom: 1rem;
        }
        
        .tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin: 1rem 0;
        }
        
        .tag {
            background: #3498db;
            color: white;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            font-size: 0.8rem;
        }
        
        .action-buttons {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }
        
        .btn {
            padding: 0.5rem 1rem;
            border: 1px solid #3498db;
            background: white;
            color: #3498db;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .btn:hover {
            background: #3498db;
            color: white;
        }
    </style>
</head>
<body>
    <header>
        <h1>Tech Blog</h1>
        <nav>Main navigation...</nav>
    </header>
    
    <main>
        <article>
            <header>
                <h1>Understanding Semantic HTML5</h1>
                <p>Published on January 15, 2024 by Sarah Developer</p>
            </header>
            
            <div class="article-content">
                <p>Semantic HTML5 elements provide meaning to web content beyond just presentation...</p>
                
                <section>
                    <h2>Benefits of Semantic HTML</h2>
                    <p>Using semantic elements improves accessibility, SEO, and maintainability...</p>
                    
                    <footer class="section-footer">
                        <p><strong>Further Reading:</strong> Check out the <a href="/web-accessibility">Web Accessibility Guide</a> for more information on making your site accessible.</p>
                    </footer>
                </section>
                
                <section>
                    <h2>Common Semantic Elements</h2>
                    <p>Here are some of the most important semantic elements in HTML5...</p>
                </section>
            </div>
            
            <!-- Article-specific footer -->
            <footer class="article-footer">
                <div class="meta-info">
                    <p>This article was last updated on <time datetime="2024-01-15">January 15, 2024</time></p>
                </div>
                
                <div class="tags">
                    <span class="tag">HTML5</span>
                    <span class="tag">Semantic Web</span>
                    <span class="tag">Accessibility</span>
                    <span class="tag">Web Development</span>
                </div>
                
                <div class="action-buttons">
                    <button class="btn">👍 Like (42)</button>
                    <button class="btn">💬 Comment (15)</button>
                    <button class="btn">📤 Share</button>
                    <button class="btn">🔖 Bookmark</button>
                </div>
                
                <nav aria-label="Article navigation">
                    <p>
                        <a href="/previous-article">← Previous Article</a> | 
                        <a href="/next-article">Next Article →</a>
                    </p>
                </nav>
            </footer>
        </article>
        
        <aside>
            <h2>Related Articles</h2>
            <!-- Related articles list -->
            <footer>
                <p><a href="/all-articles">View all articles →</a></p>
            </footer>
        </aside>
    </main>

    <!-- Main page footer -->
    <footer class="page-footer" role="contentinfo">
        <div style="max-width: 1200px; margin: 0 auto; text-align: center;">
            <p>&copy; 2024 Tech Blog. All rights reserved.</p>
            <nav aria-label="Footer navigation">
                <a href="/privacy">Privacy Policy</a> | 
                <a href="/terms">Terms of Service</a> | 
                <a href="/contact">Contact Us</a> | 
                <a href="/sitemap">Sitemap</a>
            </nav>
        </div>
    </footer>
</body>
</html>
```

### Advanced Example: Comprehensive Site Footer

This example demonstrates a sophisticated footer with multiple sections and responsive design.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Footer Example</title>
    <style>
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --text-light: #ecf0f1;
            --text-muted: #bdc3c7;
            --spacing: 1rem;
        }
        
        .site-footer {
            background: var(--primary-color);
            color: var(--text-light);
            margin-top: 4rem;
        }
        
        .footer-main {
            padding: 3rem var(--spacing);
            border-bottom: 1px solid #34495e;
        }
        
        .footer-container {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }
        
        .footer-column h3 {
            color: var(--secondary-color);
            margin-bottom: 1.5rem;
            font-size: 1.1rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .footer-links {
            list-style: none;
            padding: 0;
            margin: 0;
        }
        
        .footer-links li {
            margin-bottom: 0.75rem;
        }
        
        .footer-links a {
            color: var(--text-muted);
            text-decoration: none;
            transition: color 0.3s ease;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .footer-links a:hover {
            color: var(--secondary-color);
        }
        
        .contact-info {
            color: var(--text-muted);
        }
        
        .contact-info p {
            margin: 0.5rem 0;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .newsletter-form {
            margin-top: 1rem;
        }
        
        .newsletter-input {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #34495e;
            border-radius: 4px;
            background: #34495e;
            color: var(--text-light);
            margin-bottom: 0.5rem;
        }
        
        .newsletter-btn {
            background: var(--secondary-color);
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            transition: background 0.3s ease;
        }
        
        .newsletter-btn:hover {
            background: #2980b9;
        }
        
        .social-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 0.5rem;
            margin-top: 1rem;
        }
        
        .social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            background: #34495e;
            color: var(--text-light);
            text-decoration: none;
            padding: 0.5rem;
            border-radius: 4px;
            transition: all 0.3s ease;
        }
        
        .social-link:hover {
            background: var(--secondary-color);
            transform: translateY(-2px);
        }
        
        .footer-bottom {
            padding: 1.5rem var(--spacing);
            background: #1a252f;
        }
        
        .footer-bottom-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
        }
        
        .copyright {
            color: var(--text-muted);
            font-size: 0.9rem;
        }
        
        .legal-links {
            display: flex;
            gap: 1.5rem;
        }
        
        .legal-links a {
            color: var(--text-muted);
            text-decoration: none;
            font-size: 0.9rem;
            transition: color 0.3s ease;
        }
        
        .legal-links a:hover {
            color: var(--secondary-color);
        }
        
        .back-to-top {
            background: var(--secondary-color);
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        
        .back-to-top:hover {
            background: #2980b9;
        }
        
        @media (max-width: 768px) {
            .footer-bottom-content {
                flex-direction: column;
                text-align: center;
            }
            
            .legal-links {
                order: -1;
            }
        }
    </style>
</head>
<body>
    <main>
        <h1>Website Content</h1>
        <p>Main content area...</p>
    </main>

    <footer class="site-footer" role="contentinfo">
        <div class="footer-main">
            <div class="footer-container">
                <div class="footer-column">
                    <h3>Company</h3>
                    <ul class="footer-links">
                        <li><a href="/about">About Us</a></li>
                        <li><a href="/team">Our Team</a></li>
                        <li><a href="/careers">Careers</a></li>
                        <li><a href="/press">Press Kit</a></li>
                        <li><a href="/blog">Blog</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Products</h3>
                    <ul class="footer-links">
                        <li><a href="/features">Features</a></li>
                        <li><a href="/pricing">Pricing</a></li>
                        <li><a href="/api">API</a></li>
                        <li><a href="/integrations">Integrations</a></li>
                        <li><a href="/changelog">Changelog</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Support</h3>
                    <ul class="footer-links">
                        <li><a href="/help">Help Center</a></li>
                        <li><a href="/contact">Contact Us</a></li>
                        <li><a href="/status">System Status</a></li>
                        <li><a href="/community">Community</a></li>
                        <li><a href="/docs">Documentation</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Contact</h3>
                    <div class="contact-info">
                        <p>📍 123 Business Avenue, Suite 100<br>San Francisco, CA 94107</p>
                        <p>📞 <a href="tel:+15551234567">(555) 123-4567</a></p>
                        <p>✉️ <a href="mailto:hello@company.com">hello@company.com</a></p>
                    </div>
                    
                    <div class="newsletter-form">
                        <h4>Stay Updated</h4>
                        <input type="email" class="newsletter-input" placeholder="Enter your email" aria-label="Email for newsletter">
                        <button type="submit" class="newsletter-btn">Subscribe</button>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="footer-bottom">
            <div class="footer-bottom-content">
                <div class="copyright">
                    &copy; 2024 Company Name. All rights reserved.
                </div>
                
                <div class="legal-links">
                    <a href="/privacy">Privacy Policy</a>
                    <a href="/terms">Terms of Service</a>
                    <a href="/cookies">Cookie Policy</a>
                    <a href="/security">Security</a>
                </div>
                
                <div class="social-grid">
                    <a href="#" class="social-link" aria-label="Twitter">🐦</a>
                    <a href="#" class="social-link" aria-label="Facebook">📘</a>
                    <a href="#" class="social-link" aria-label="LinkedIn">💼</a>
                    <a href="#" class="social-link" aria-label="GitHub">🐙</a>
                </div>
                
                <button class="back-to-top" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">
                    ↑ Back to Top
                </button>
            </div>
        </div>
    </footer>
</body>
</html>
```

### Specialized Example: Article Footer with Comments and Related Content

This example shows a detailed article footer with interactive elements.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Article Footer Example</title>
    <style>
        .article-footer {
            background: #f8f9fa;
            border-top: 3px solid #3498db;
            margin-top: 3rem;
            padding: 2rem;
        }
        
        .footer-section {
            margin-bottom: 2rem;
        }
        
        .footer-section:last-child {
            margin-bottom: 0;
        }
        
        .author-bio {
            display: flex;
            gap: 1.5rem;
            align-items: flex-start;
            padding: 1.5rem;
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .author-avatar {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: #3498db;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.5rem;
            font-weight: bold;
            flex-shrink: 0;
        }
        
        .author-info h3 {
            margin: 0 0 0.5rem 0;
            color: #2c3e50;
        }
        
        .author-title {
            color: #7f8c8d;
            margin: 0 0 1rem 0;
            font-size: 0.9rem;
        }
        
        .author-bio-text {
            color: #34495e;
            line-height: 1.6;
        }
        
        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }
        
        .social-link {
            color: #3498db;
            text-decoration: none;
            font-size: 0.9rem;
        }
        
        .comments-section {
            background: white;
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .comment-form {
            margin-top: 1.5rem;
        }
        
        .form-group {
            margin-bottom: 1rem;
        }
        
        .form-input, .form-textarea {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #bdc3c7;
            border-radius: 4px;
            font-family: inherit;
        }
        
        .form-textarea {
            min-height: 100px;
            resize: vertical;
        }
        
        .submit-btn {
            background: #3498db;
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 4px;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        
        .submit-btn:hover {
            background: #2980b9;
        }
        
        .related-articles {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1rem;
            margin-top: 1rem;
        }
        
        .related-article {
            background: white;
            padding: 1rem;
            border-radius: 6px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
        }
        
        .related-article:hover {
            transform: translateY(-2px);
        }
        
        .related-article h4 {
            margin: 0 0 0.5rem 0;
            font-size: 1rem;
        }
        
        .related-article a {
            color: #2c3e50;
            text-decoration: none;
        }
        
        .article-actions {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            margin-top: 1rem;
        }
        
        .action-btn {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.5rem 1rem;
            border: 1px solid #bdc3c7;
            background: white;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .action-btn:hover {
            background: #f8f9fa;
            border-color: #3498db;
        }
    </style>
</head>
<body>
    <article>
        <header>
            <h1>The Future of Web Development</h1>
            <!-- Article content -->
        </header>
        
        <div class="article-content">
            <p>Article content goes here...</p>
        </div>
        
        <footer class="article-footer">
            <div class="footer-section">
                <div class="author-bio">
                    <div class="author-avatar">SJ</div>
                    <div class="author-info">
                        <h3>Sarah Johnson</h3>
                        <p class="author-title">Senior Frontend Developer & Technical Writer</p>
                        <p class="author-bio-text">
                            Sarah is a passionate web developer with over 8 years of experience in creating 
                            accessible and performant web applications. She specializes in modern JavaScript 
                            frameworks and semantic HTML.
                        </p>
                        <div class="social-links">
                            <a href="#" class="social-link">Twitter</a>
                            <a href="#" class="social-link">GitHub</a>
                            <a href="#" class="social-link">LinkedIn</a>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="footer-section">
                <div class="article-actions">
                    <button class="action-btn">👍 Like Article</button>
                    <button class="action-btn">🔖 Bookmark</button>
                    <button class="action-btn">📤 Share</button>
                    <button class="action-btn">📧 Subscribe</button>
                </div>
            </div>
            
            <div class="footer-section">
                <h3>Comments (5)</h3>
                <div class="comments-section">
                    <p>Join the discussion and share your thoughts below.</p>
                    <form class="comment-form">
                        <div class="form-group">
                            <input type="text" class="form-input" placeholder="Your name" aria-label="Your name">
                        </div>
                        <div class="form-group">
                            <textarea class="form-textarea" placeholder="Add your comment..." aria-label="Your comment"></textarea>
                        </div>
                        <button type="submit" class="submit-btn">Post Comment</button>
                    </form>
                </div>
            </div>
            
            <div class="footer-section">
                <h3>Related Articles</h3>
                <div class="related-articles">
                    <div class="related-article">
                        <h4><a href="/web-components">Web Components: The Future of Reusable UI</a></h4>
                        <p>Exploring the potential of native web components...</p>
                    </div>
                    <div class="related-article">
                        <h4><a href="/css-grid">Mastering CSS Grid Layout</a></h4>
                        <p>Advanced techniques for modern web layouts...</p>
                    </div>
                    <div class="related-article">
                        <h4><a href="/performance">Web Performance Optimization</a></h4>
                        <p>Strategies for faster loading websites...</p>
                    </div>
                </div>
            </div>
            
            <div class="footer-section">
                <nav aria-label="Article navigation">
                    <div style="display: flex; justify-content: space-between;">
                        <a href="/previous-article" style="color: #3498db; text-decoration: none;">
                            ← Previous: JavaScript ES2023 Features
                        </a>
                        <a href="/next-article" style="color: #3498db; text-decoration: none;">
                            Next: CSS Container Queries →
                        </a>
                    </div>
                </nav>
            </div>
        </footer>
    </article>
</body>
</html>
```

---

## Notes

* **When to Use `<footer>` vs `<div>`**:

  - Use `<footer>` for **concluding content** or **supplementary information** at the end of sections
  - Use `<div>` for **generic containers** without semantic meaning
  - If the content concludes a section or provides metadata about it, use `<footer>`

* **Multiple Footers on a Page**:

  - A page can have multiple `<footer>` elements, each scoped to its parent section
  - Only one `<footer>` should be the main page footer (direct child of `<body>`)
  - Footers within `<article>`, `<section>`, or `<aside>` are scoped to those elements

* **Accessibility Best Practices**:

  - The main page footer (direct child of `<body>`) implicitly has `role="contentinfo"`
  - Use `aria-label` or `aria-labelledby` for footers without visible text labels
  - Ensure footer content is properly structured for screen reader navigation
  - Use landmark roles appropriately when footers serve specific purposes

* **SEO Considerations**:

  - Footer content helps search engines understand site structure and supplementary information
  - Important links in footers can improve site navigation and indexing
  - Avoid keyword stuffing in footer content
  - Ensure footer links are relevant and useful to users

* **Common Pitfalls**:

  - Using `<footer>` as a generic wrapper for any bottom content
  - Nesting footers within footers (invalid structure)
  - Putting primary navigation in footers (use `<nav>` in header instead)
  - Using multiple main page footers (should only have one contentinfo role)

* **Browser Support**:

  - Excellent support in all modern browsers
  - Internet Explorer 9+ supports `<footer>` with basic styling
  - The implicit `role="contentinfo"` is well-supported in modern screen readers

* **Best Practices**:

  - Use the main page footer for site-wide information and links
  - Scope footers appropriately to their parent sections
  - Include relevant metadata and navigation in section footers
  - Use `<address>` for contact information in footers
  - Keep footer content relevant and useful
  - Test footer structure with screen readers and accessibility tools

---
