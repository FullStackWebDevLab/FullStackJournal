# `<article>`

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

The `<article>` tag represents a self-contained composition in a document, page, application, or site that is intended to be independently distributable or reusable. This could include forum posts, magazine or newspaper articles, blog entries, product cards, user-submitted comments, interactive widgets, or any other independent item of content. The key characteristic is that the content makes sense on its own, independent of the surrounding context.

---

## Syntax & Variants

+ The `<article>` tag requires both an opening `<article>` and closing `</article>` tag .
+ It is a non-void element that serves as a sectioning content container .
+ No alternative or legacy forms exist, as this is an HTML5 semantic element .

---

## Attributes

The `<article>` tag supports only **global attributes** with no specific attributes of its own:

**Global Attributes:**
- `id`: Particularly useful for creating unique identifiers for articles, enabling direct linking and JavaScript targeting
- `class`, `style`: For CSS styling and visual presentation
- `data-*`: For custom data attributes to store article-specific metadata (publication date, author, categories, etc.)
- `aria-*`: For enhanced accessibility semantics, such as `aria-labelledby`, `aria-describedby`, or `aria-posinset` in article lists
- `lang`, `dir`: For language and text direction specific to the article content
- `title`: For advisory information about the article
- `itemprop`, `itemscope`, `itemtype`: For microdata markup (Schema.org)

**Important Notes:**
- No required attributes
- The `id` attribute is commonly used for permalinks and social sharing
- `aria-labelledby` can associate an article with its heading for better accessibility
- Microdata attributes can enhance SEO by providing structured data about the article

---

## Content Model

The `<article>` element can contain **flow content**, which includes virtually all elements that can appear in the document body:

**Permitted Content:**
- Text content and phrasing elements
- Heading elements (`<h1>`-`<h6>`) - essential for article identification
- Paragraphs (`<p>`), lists (`<ul>`, `<ol>`, `<dl>`), and other block-level elements
- Embedded content: `<img>`, `<video>`, `<audio>`, `<figure>`, `<canvas>`, `<iframe>`
- Interactive elements: `<button>`, `<form>`, `<input>`, `<details>`
- Sectioning elements: `<section>`, `<header>`, `<footer>`, `<aside>`, `<nav>`
- Other `<article>` elements (for nested articles like comments)
- Generic containers: `<div>`, `<span>`

**Restrictions:**
- Should not contain `<main>` element (only one `<main>` per document)
- Should represent content that is self-contained and independently distributable
- Should not be used as a generic wrapper for non-article content

---

## Context

+ **Placement**: Can be placed within any element that accepts flow content, including `<body>`, `<main>`, `<section>`, `<div>`, `<li>`, and other container elements .
+ **Parent Elements**: `<body>`, `<main>`, `<section>`, `<div>`, `<li>`, `<blockquote>`, `<td>`, and other content containers
+ **Sectioning Root**: The `<article>` element itself is a sectioning element that creates a new section in the document outline
+ **Usage Limits**: 
  - Multiple `<article>` elements are encouraged for content like blog rolls, news feeds, or product listings
  - Can be nested (e.g., comments within a blog post article)
  - Should represent actual self-contained content, not just visual groupings

---

## Behavior and Semantics

+ **Rendering**: The `<article>` tag is a **block-level element** that creates line breaks before and after its content .
+ **Default CSS**: Browsers apply minimal default styling:
  ```css
  article {
    display: block;
  }
  ```
+ **Document Outline**: Creates an entry in the document outline, which can be navigated by assistive technologies
+ **Semantic Impact**:
  - **Accessibility**: Screen readers can identify articles as distinct content units and provide navigation between them
  - **SEO**: Search engines recognize articles as primary content that can be syndicated or featured in search results
  - **Syndication**: Articles are designed to be easily extracted and reused in different contexts (RSS feeds, social media, etc.)
  - **Structured Data**: Provides clear semantic meaning for microdata and rich snippets

---

## Examples

### Basic Example: Blog Post Article

This example demonstrates a standalone blog post using the `<article>` element.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Blog Post Example</title>
    <style>
        article {
            max-width: 800px;
            margin: 2rem auto;
            padding: 2rem;
            background: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            border-radius: 8px;
        }
        
        .article-header {
            border-bottom: 2px solid #f0f0f0;
            padding-bottom: 1rem;
            margin-bottom: 2rem;
        }
        
        .article-meta {
            color: #666;
            font-size: 0.9rem;
        }
        
        .article-content {
            line-height: 1.6;
        }
        
        .article-footer {
            border-top: 1px solid #f0f0f0;
            padding-top: 1rem;
            margin-top: 2rem;
        }
    </style>
</head>
<body>
    <main>
        <article id="post-123" itemscope itemtype="https://schema.org/BlogPosting">
            <header class="article-header">
                <h1 itemprop="headline">Understanding Semantic HTML5 Elements</h1>
                <div class="article-meta">
                    <span itemprop="author" itemscope itemtype="https://schema.org/Person">
                        By <span itemprop="name">Sarah Johnson</span>
                    </span>
                    <time datetime="2024-01-15" itemprop="datePublished">January 15, 2024</time>
                    <span itemprop="keywords">HTML5, Semantic Web, Accessibility</span>
                </div>
            </header>
            
            <div class="article-content" itemprop="articleBody">
                <p>Semantic HTML5 elements provide meaning to web content beyond just presentation. 
                Elements like <code>&lt;article&gt;</code>, <code>&lt;section&gt;</code>, and 
                <code>&lt;nav&gt;</code> help both browsers and developers understand the structure 
                and purpose of content.</p>
                
                <section>
                    <h2>Benefits of Semantic HTML</h2>
                    <p>Using semantic elements improves accessibility, SEO, and maintainability...</p>
                    
                    <h3>Accessibility Improvements</h3>
                    <p>Screen readers can better navigate and interpret properly structured content...</p>
                </section>
                
                <section>
                    <h2>Common Semantic Elements</h2>
                    <p>Here are some of the most important semantic elements in HTML5...</p>
                </section>
            </div>
            
            <footer class="article-footer">
                <div class="article-tags">
                    <strong>Tags:</strong>
                    <span itemprop="keywords">Web Development, HTML5, Semantics</span>
                </div>
                <div class="article-actions">
                    <button>Like</button>
                    <button>Share</button>
                    <button>Bookmark</button>
                </div>
            </footer>
        </article>
    </main>
</body>
</html>
```

### Intermediate Example: News Article List

This example shows multiple articles in a news listing context.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>News Portal</title>
    <style>
        .news-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            padding: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .news-article {
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            overflow: hidden;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }
        
        .news-article:hover {
            transform: translateY(-4px);
            box-shadow: 0 8px 15px rgba(0,0,0,0.15);
        }
        
        .article-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }
        
        .article-content {
            padding: 1.5rem;
        }
        
        .article-category {
            display: inline-block;
            background: #e3f2fd;
            color: #1976d2;
            padding: 0.25rem 0.75rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: bold;
            margin-bottom: 1rem;
        }
        
        .article-meta {
            color: #666;
            font-size: 0.9rem;
            margin: 1rem 0;
        }
        
        .read-more {
            display: inline-block;
            background: #2196f3;
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            text-decoration: none;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <header>
        <h1>Latest News</h1>
    </header>
    
    <main>
        <div class="news-grid">
            <article class="news-article" itemscope itemtype="https://schema.org/NewsArticle">
                <img src="tech-innovation.jpg" alt="Technology innovation" class="article-image" itemprop="image">
                <div class="article-content">
                    <span class="article-category" itemprop="articleSection">Technology</span>
                    <h2 itemprop="headline">New Breakthrough in Quantum Computing Announced</h2>
                    <p itemprop="description">Researchers have achieved a major milestone in quantum computing that could revolutionize data processing...</p>
                    <div class="article-meta">
                        <span itemprop="author">By Alex Chen</span> • 
                        <time datetime="2024-01-15" itemprop="datePublished">3 hours ago</time>
                    </div>
                    <a href="/article/quantum-computing" class="read-more" itemprop="url">Read More</a>
                </div>
            </article>
            
            <article class="news-article" itemscope itemtype="https://schema.org/NewsArticle">
                <img src="climate-summit.jpg" alt="Climate summit" class="article-image" itemprop="image">
                <div class="article-content">
                    <span class="article-category" itemprop="articleSection">Environment</span>
                    <h2 itemprop="headline">Global Climate Summit Reaches Historic Agreement</h2>
                    <p itemprop="description">World leaders have agreed on ambitious new targets for carbon reduction at the latest climate conference...</p>
                    <div class="article-meta">
                        <span itemprop="author">By Maria Rodriguez</span> • 
                        <time datetime="2024-01-14" itemprop="datePublished">1 day ago</time>
                    </div>
                    <a href="/article/climate-summit" class="read-more" itemprop="url">Read More</a>
                </div>
            </article>
            
            <article class="news-article" itemscope itemtype="https://schema.org/NewsArticle">
                <img src="health-research.jpg" alt="Medical research" class="article-image" itemprop="image">
                <div class="article-content">
                    <span class="article-category" itemprop="articleSection">Health</span>
                    <h2 itemprop="headline">New Study Reveals Benefits of Mediterranean Diet</h2>
                    <p itemprop="description">A comprehensive 10-year study confirms significant health benefits associated with the Mediterranean diet...</p>
                    <div class="article-meta">
                        <span itemprop="author">By Dr. James Wilson</span> • 
                        <time datetime="2024-01-13" itemprop="datePublished">2 days ago</time>
                    </div>
                    <a href="/article/mediterranean-diet" class="read-more" itemprop="url">Read More</a>
                </div>
            </article>
        </div>
    </main>
</body>
</html>
```

### Advanced Example: Forum Post with Nested Articles

This example demonstrates nested articles for forum posts and comments.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Forum Discussion</title>
    <style>
        .forum-container {
            max-width: 900px;
            margin: 2rem auto;
            padding: 0 1rem;
        }
        
        .main-post {
            background: white;
            border: 1px solid #e0e0e0;
            border-radius: 8px;
            margin-bottom: 2rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .post-header {
            padding: 1.5rem;
            border-bottom: 1px solid #f0f0f0;
            background: #fafafa;
        }
        
        .post-content {
            padding: 1.5rem;
            line-height: 1.6;
        }
        
        .comments-section {
            margin-top: 2rem;
        }
        
        .comment {
            background: white;
            border: 1px solid #e0e0e0;
            border-radius: 6px;
            margin-bottom: 1rem;
            padding: 1rem;
        }
        
        .comment-meta {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 0.5rem;
        }
        
        .nested-comments {
            margin-left: 2rem;
            margin-top: 1rem;
        }
        
        .vote-buttons {
            display: flex;
            gap: 0.5rem;
            margin-top: 1rem;
        }
        
        .vote-btn {
            background: #f8f9fa;
            border: 1px solid #ddd;
            padding: 0.25rem 0.75rem;
            border-radius: 4px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="forum-container">
        <!-- Main forum post as article -->
        <article class="main-post" itemscope itemtype="https://schema.org/DiscussionForumPosting">
            <header class="post-header">
                <h1 itemprop="headline">Best Practices for Responsive Web Design in 2024</h1>
                <div class="post-meta">
                    <span itemprop="author">Posted by <strong>WebDevExpert</strong></span>
                    <time datetime="2024-01-15T14:30:00Z" itemprop="datePublished">January 15, 2024 at 2:30 PM</time>
                    <span itemprop="category">in Web Development</span>
                </div>
            </header>
            
            <div class="post-content" itemprop="text">
                <p>With the ever-evolving landscape of web devices, responsive design continues to be crucial. 
                Here are the current best practices I've found most effective:</p>
                
                <section>
                    <h2>1. Mobile-First Approach</h2>
                    <p>Starting with mobile constraints forces you to focus on essential content and functionality...</p>
                </section>
                
                <section>
                    <h2>2. CSS Grid and Flexbox</h2>
                    <p>Modern CSS layout techniques provide powerful tools for creating flexible, responsive layouts...</p>
                </section>
                
                <section>
                    <h2>3. Performance Considerations</h2>
                    <p>Responsive design isn't just about layout—it's also about delivering the right assets for each device...</p>
                </section>
                
                <p>What are your thoughts? Have you found any particular techniques especially effective recently?</p>
            </div>
            
            <div class="vote-buttons">
                <button class="vote-btn">👍 42</button>
                <button class="vote-btn">👎 2</button>
                <button class="vote-btn">💬 15 comments</button>
            </div>
        </article>
        
        <!-- Comments section with nested articles -->
        <section class="comments-section" aria-labelledby="comments-heading">
            <h2 id="comments-heading">Comments</h2>
            
            <!-- Comment as nested article -->
            <article class="comment" itemprop="comment" itemscope itemtype="https://schema.org/Comment">
                <div class="comment-meta">
                    <strong itemprop="author">DesignPro</strong>
                    <time datetime="2024-01-15T15:45:00Z" itemprop="datePublished">3:45 PM</time>
                </div>
                <div class="comment-content" itemprop="text">
                    <p>Great points! I'd add that container queries are becoming a game-changer for component-level responsiveness. 
                    They allow components to adapt based on their container size rather than just the viewport.</p>
                </div>
                <div class="vote-buttons">
                    <button class="vote-btn">👍 8</button>
                    <button class="vote-btn">Reply</button>
                </div>
                
                <!-- Nested comment -->
                <div class="nested-comments">
                    <article class="comment" itemprop="comment" itemscope itemtype="https://schema.org/Comment">
                        <div class="comment-meta">
                            <strong itemprop="author">WebDevExpert</strong>
                            <time datetime="2024-01-15T16:20:00Z" itemprop="datePublished">4:20 PM</time>
                        </div>
                        <div class="comment-content" itemprop="text">
                            <p>Excellent addition! Container queries are indeed revolutionary. 
                            Have you found good browser support for them in production projects?</p>
                        </div>
                        <div class="vote-buttons">
                            <button class="vote-btn">👍 3</button>
                            <button class="vote-btn">Reply</button>
                        </div>
                    </article>
                </div>
            </article>
            
            <!-- Another top-level comment -->
            <article class="comment" itemprop="comment" itemscope itemtype="https://schema.org/Comment">
                <div class="comment-meta">
                    <strong itemprop="author">AccessibilityAdvocate</strong>
                    <time datetime="2024-01-15T17:30:00Z" itemprop="datePublished">5:30 PM</time>
                </div>
                <div class="comment-content" itemprop="text">
                    <p>Don't forget about responsive typography! Using relative units (em, rem) and viewport units 
                    for font sizes ensures text remains readable across all devices.</p>
                </div>
                <div class="vote-buttons">
                    <button class="vote-btn">👍 5</button>
                    <button class="vote-btn">Reply</button>
                </div>
            </article>
        </section>
    </div>
</body>
</html>
```

### Specialized Example: Product Cards in E-commerce

This example shows articles used for product listings in an e-commerce context.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Product Catalog</title>
    <style>
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 1.5rem;
            padding: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .product-card {
            background: white;
            border: 1px solid #e0e0e0;
            border-radius: 8px;
            padding: 1.5rem;
            text-align: center;
            transition: all 0.3s ease;
            position: relative;
        }
        
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
            border-color: #2196f3;
        }
        
        .product-badge {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: #ff5722;
            color: white;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            font-size: 0.8rem;
            font-weight: bold;
        }
        
        .product-image {
            width: 100%;
            height: 200px;
            object-fit: contain;
            margin-bottom: 1rem;
        }
        
        .product-price {
            font-size: 1.25rem;
            font-weight: bold;
            color: #2196f3;
            margin: 0.5rem 0;
        }
        
        .original-price {
            text-decoration: line-through;
            color: #999;
            font-size: 1rem;
            margin-left: 0.5rem;
        }
        
        .add-to-cart {
            background: #4caf50;
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            width: 100%;
            margin-top: 1rem;
        }
        
        .rating {
            color: #ffc107;
            margin: 0.5rem 0;
        }
    </style>
</head>
<body>
    <header>
        <h1>Featured Products</h1>
    </header>
    
    <main>
        <div class="products-grid">
            <article class="product-card" itemscope itemtype="https://schema.org/Product">
                <div class="product-badge" itemprop="offers" itemscope itemtype="https://schema.org/Offer">
                    Sale
                </div>
                <img src="wireless-headphones.jpg" alt="Wireless Noise-Cancelling Headphones" class="product-image" itemprop="image">
                <h2 itemprop="name">Wireless Noise-Cancelling Headphones</h2>
                <div class="rating" itemprop="aggregateRating" itemscope itemtype="https://schema.org/AggregateRating">
                    ★★★★☆ <span itemprop="ratingValue">4.2</span> (<span itemprop="reviewCount">128</span> reviews)
                </div>
                <p itemprop="description">Premium wireless headphones with active noise cancellation and 30-hour battery life.</p>
                <div class="product-price">
                    <span itemprop="price" content="199.99">$199.99</span>
                    <span class="original-price">$249.99</span>
                </div>
                <span itemprop="priceCurrency" content="USD">USD</span>
                <button class="add-to-cart">Add to Cart</button>
            </article>
            
            <article class="product-card" itemscope itemtype="https://schema.org/Product">
                <img src="smart-watch.jpg" alt="Smart Fitness Watch" class="product-image" itemprop="image">
                <h2 itemprop="name">Smart Fitness Watch</h2>
                <div class="rating" itemprop="aggregateRating" itemscope itemtype="https://schema.org/AggregateRating">
                    ★★★★★ <span itemprop="ratingValue">4.8</span> (<span itemprop="reviewCount">256</span> reviews)
                </div>
                <p itemprop="description">Advanced fitness tracking with heart rate monitoring, GPS, and 7-day battery.</p>
                <div class="product-price">
                    <span itemprop="price" content="179.99">$179.99</span>
                </div>
                <span itemprop="priceCurrency" content="USD">USD</span>
                <button class="add-to-cart">Add to Cart</button>
            </article>
            
            <article class="product-card" itemscope itemtype="https://schema.org/Product">
                <img src="portable-speaker.jpg" alt="Waterproof Portable Speaker" class="product-image" itemprop="image">
                <h2 itemprop="name">Waterproof Portable Speaker</h2>
                <div class="rating" itemprop="aggregateRating" itemscope itemtype="https://schema.org/AggregateRating">
                    ★★★★☆ <span itemprop="ratingValue">4.5</span> (<span itemprop="reviewCount">89</span> reviews)
                </div>
                <p itemprop="description">IPX7 waterproof Bluetooth speaker with 360° sound and 12-hour playtime.</p>
                <div class="product-price">
                    <span itemprop="price" content="79.99">$79.99</span>
                </div>
                <span itemprop="priceCurrency" content="USD">USD</span>
                <button class="add-to-cart">Add to Cart</button>
            </article>
        </div>
    </main>
</body>
</html>
```

---

## Notes

* **When to Use `<article>` vs `<section>`**:

  - Use `<article>` for **self-contained, reusable content** that makes sense on its own
  - Use `<section>` for **thematic groupings within content** that are part of a larger whole
  - **Test**: If the content can be syndicated via RSS and still make sense, use `<article>`
  - **Examples**: Blog posts (article) vs introduction section (section)

* **When to Use `<article>` vs `<div>`**:

  - Use `<article>` for **substantial, independent content units**
  - Use `<div>` for **styling wrappers** or **generic containers** without semantic meaning
  - If the content could be read and understood in isolation, consider `<article>`

* **Nested Articles**:

  - Articles can be nested within other articles (e.g., comments within a blog post)
  - Each nested article should be independently meaningful
  - Common in blog comments, forum replies, or review systems

* **Accessibility Best Practices**:

  - **Always include a heading** within each article for proper identification
  - Use `aria-labelledby` to associate the article with its heading
  - Consider using `role="article"` for dynamic content that can't use the native element
  - Ensure articles are properly labeled for screen reader navigation

* **SEO and Structured Data**:

  - Articles are highly valued by search engines as primary content
  - Use Schema.org markup (`itemtype`, `itemprop`) for rich snippets
  - Include relevant metadata: author, publication date, categories, etc.
  - Articles can appear in Google's "Top Stories" and other specialized results

* **Common Pitfalls**:

  - Using `<article>` for every content block (overuse dilutes semantic meaning)
  - Creating articles without proper headings (poor accessibility)
  - Using articles for non-self-contained content
  - Forgetting that articles should make sense when removed from context

* **Browser Support**:

  - Excellent support in all modern browsers
  - Internet Explorer 9+ supports `<article>` with basic styling
  - The document outline algorithm is well-supported in modern browsers

* **Best Practices**:

  - Start each article with a heading element (`<h1>`-`<h6>`)
  - Use the `id` attribute for direct linking to articles
  - Include appropriate metadata (author, date, categories)
  - Consider using microdata for enhanced SEO
  - Test that articles make sense when viewed in isolation
  - Use consistent article structure across your site

---
