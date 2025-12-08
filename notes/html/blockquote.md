# `<blockquote>`

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

The `<blockquote>` element represents a section of content that is quoted from another source. It is used for extended quotations that form one or more paragraphs and are typically displayed as a distinct block within the document flow. The element provides semantic meaning that the enclosed content is attributed to an external source, enabling proper representation by user agents, search engines, and assistive technologies.

---

## Syntax & Variants

+ **Standard syntax**: `<blockquote>...</blockquote>`
+ **Not void**: Requires both opening and closing tags
+ **Block-level element**: Creates a new block formatting context
+ **Optional citation**: Can include `cite` attribute for source URL
+ **No self-closing variant**: Must contain quoted content

---

## Attributes

+ **Core attributes**:
  - `cite` (optional): URL pointing to the source of the quotation
  - `lang` (optional): Language of the quoted content if different from document

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No deprecated attributes**: All original functionality remains supported

---

## Content Model

+ **Permitted content**: Flow content
+ **Allowed content**:
  - Paragraphs, headings, lists, and other block elements
  - Text content and phrasing elements
  - Typically contains one or more paragraphs of quoted text
+ **Common structure**: Often followed by a `<footer>` or `<cite>` element for attribution
+ **Nesting permitted**: Can contain most other HTML elements except another `<blockquote>`

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Articles and blog posts
  - Academic papers and research
  - News articles and interviews
  - Testimonials and reviews
  - Documentation and tutorials
+ **Block-level context**: Creates its own block formatting context
+ **No nesting restriction**: Can contain other block elements but not nested `<blockquote>`

---

## Behavior and Semantics

+ **Default display**: Block-level element (`display: block`)
+ **Default styling**:
  - Typically indented with margins: `margin: 1em 40px`
  - May have different text styling in some browsers
  - No quotation marks added by default
+ **Semantic meaning**:
  - Identifies content as quoted from another source
  - Provides machine-readable context for external citations
  - Helps search engines understand attributed content
+ **Accessibility role**:
  - Screen readers may announce as "quotation" or "block quotation"
  - Provides semantic structure for quoted content
  - Helps users distinguish between original and quoted material

---

## Examples

**Basic blockquote with paragraph:**
```html
<blockquote>
  <p>The only way to do great work is to love what you do.</p>
</blockquote>
```

**Blockquote with citation attribute:**
```html
<blockquote cite="https://example.com/source-article">
  <p>This is a quoted passage from an external source.</p>
</blockquote>
```

**Complete quote with attribution:**
```html
<blockquote>
  <p>Innovation distinguishes between a leader and a follower.</p>
  <footer>— Steve Jobs, <cite>Apple Worldwide Developers Conference, 1997</cite></footer>
</blockquote>
```

**Styled blockquote with CSS:**
```html
<blockquote class="fancy-quote">
  <p>The future belongs to those who believe in the beauty of their dreams.</p>
  <footer>— Eleanor Roosevelt</footer>
</blockquote>

<style>
.fancy-quote {
  border-left: 4px solid #3498db;
  padding: 20px;
  margin: 20px 0;
  background: #f8f9fa;
  font-style: italic;
  font-size: 1.1em;
  line-height: 1.6;
}

.fancy-quote footer {
  margin-top: 10px;
  font-style: normal;
  font-weight: bold;
  color: #666;
}
</style>
```

**Multiple paragraphs in a blockquote:**
```html
<blockquote>
  <p>It is not the strongest of the species that survive, nor the most intelligent, but the one most responsive to change.</p>
  <p>Intelligence is based on how efficient a species became at doing the things they need to survive.</p>
  <footer>— Charles Darwin</footer>
</blockquote>
```

**Academic citation with source:**
```html
<blockquote cite="https://www.gutenberg.org/ebooks/1342">
  <p>It is a truth universally acknowledged, that a single man in possession of a good fortune, must be in want of a wife.</p>
  <footer>
    — Jane Austen, <cite>Pride and Prejudice</cite>
  </footer>
</blockquote>
```

**News article quotation:**
```html
<article>
  <h1>Breaking News: Major Discovery</h1>
  <p>Researchers at the university announced a groundbreaking finding today:</p>
  
  <blockquote>
    <p>This discovery represents a fundamental shift in our understanding of quantum mechanics. The implications for computing and communication are profound.</p>
    <footer>
      — Dr. Sarah Chen, <cite>Lead Researcher, Quantum Physics Laboratory</cite>
    </footer>
  </blockquote>
  
  <p>The research team plans to publish their complete findings next month.</p>
</article>
```

**Testimonial with styling:**
```html
<div class="testimonial-grid">
  <blockquote class="testimonial">
    <p>This product completely transformed our workflow. The efficiency gains have been remarkable.</p>
    <footer>
      <img src="avatar1.jpg" alt="Photo of John Smith">
      <div>
        <strong>John Smith</strong>
        <span>CTO, Tech Solutions Inc.</span>
      </div>
    </footer>
  </blockquote>
  
  <blockquote class="testimonial">
    <p>Outstanding support and incredible features. We've seen a 40% increase in productivity.</p>
    <footer>
      <img src="avatar2.jpg" alt="Photo of Maria Garcia">
      <div>
        <strong>Maria Garcia</strong>
        <span>Operations Director, Global Corp</span>
      </div>
    </footer>
  </blockquote>
</div>

<style>
.testimonial-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
  margin: 40px 0;
}

.testimonial {
  background: white;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  border-left: 5px solid #e74c3c;
}

.testimonial p {
  font-size: 1.1em;
  line-height: 1.6;
  color: #333;
  margin-bottom: 20px;
}

.testimonial footer {
  display: flex;
  align-items: center;
  gap: 15px;
}

.testimonial img {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  object-fit: cover;
}

.testimonial strong {
  display: block;
  color: #2c3e50;
}

.testimonial span {
  font-size: 0.9em;
  color: #7f8c8d;
}
</style>
```

**Interview excerpt:**
```html
<article class="interview">
  <h1>Exclusive Interview with CEO</h1>
  
  <div class="question">
    <p><strong>Interviewer:</strong> What's your vision for the company's future?</p>
  </div>
  
  <blockquote class="response">
    <p>We're focusing on sustainable growth through innovation. Our goal is to not just lead the market, but to redefine it entirely.</p>
    <p>Over the next five years, we'll be investing heavily in AI research and renewable energy solutions.</p>
    <footer>— Jane Doe, CEO of InnovateCorp</footer>
  </blockquote>
</article>

<style>
.interview {
  max-width: 800px;
  line-height: 1.6;
}

.question {
  margin-bottom: 10px;
}

.response {
  border-left: 3px solid #27ae60;
  padding: 20px;
  margin: 10px 0 30px 20px;
  background: #f8fff8;
}

.response p {
  margin-bottom: 15px;
}

.response p:last-child {
  margin-bottom: 0;
}
</style>
```

**Literary quotation with multiple citations:**
```html
<blockquote class="literary-quote">
  <p>So we beat on, boats against the current, borne back ceaselessly into the past.</p>
  <footer>
    — F. Scott Fitzgerald, 
    <cite>The Great Gatsby</cite>
    <span class="publication-year">(1925)</span>
  </footer>
</blockquote>

<style>
.literary-quote {
  font-family: 'Georgia', serif;
  font-size: 1.2em;
  line-height: 1.8;
  text-align: center;
  padding: 40px;
  margin: 40px 0;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 10px;
  position: relative;
}

.literary-quote::before,
.literary-quote::after {
  content: '"';
  font-size: 4em;
  color: rgba(255,255,255,0.3);
  position: absolute;
}

.literary-quote::before {
  top: 10px;
  left: 20px;
}

.literary-quote::after {
  bottom: 10px;
  right: 20px;
}

.literary-quote footer {
  margin-top: 20px;
  font-size: 0.9em;
  opacity: 0.9;
}

.publication-year {
  font-style: italic;
}
</style>
```

**Technical documentation quote:**
```html
<section class="api-docs">
  <h2>Authentication Endpoint</h2>
  <p>According to the official specification:</p>
  
  <blockquote cite="https://tools.ietf.org/html/rfc6749#section-4.1">
    <p>The authorization code is obtained by using an authorization server as an intermediary between the client and resource owner. Instead of requesting authorization directly from the resource owner, the client directs the resource owner to an authorization server.</p>
    <footer>
      — <cite>RFC 6749, The OAuth 2.0 Authorization Framework</cite>
    </footer>
  </blockquote>
  
  <p>This means you must redirect users to our authorization server first.</p>
</section>
```

**Pull quote in article layout:**
```html
<article class="feature-article">
  <h1>The Future of Web Development</h1>
  
  <p>As we look toward the next decade of web development, several trends are emerging that will shape how we build for the web.</p>
  
  <blockquote class="pull-quote">
    <p>Web components represent the most significant shift in frontend development since the introduction of React and Vue.</p>
  </blockquote>
  
  <p>The adoption of web standards like web components is accelerating, with major browsers now offering full support. This standardization promises to reduce framework lock-in and improve performance.</p>
  
  <p>Meanwhile, the rise of edge computing is changing how we think about application architecture...</p>
</article>

<style>
.feature-article {
  max-width: 800px;
  line-height: 1.7;
  margin: 0 auto;
}

.pull-quote {
  float: right;
  width: 300px;
  margin: 10px 0 20px 30px;
  padding: 20px;
  background: #f8f9fa;
  border-left: 4px solid #3498db;
  font-size: 1.1em;
  font-weight: 600;
  color: #2c3e50;
}

@media (max-width: 768px) {
  .pull-quote {
    float: none;
    width: auto;
    margin: 20px 0;
  }
}
</style>
```

**Accessible blockquote with ARIA:**
```html
<blockquote role="blockquote" aria-labelledby="quote-source">
  <p id="quote-content">The greatest glory in living lies not in never falling, but in rising every time we fall.</p>
  <footer id="quote-source">
    — Nelson Mandela
  </footer>
</blockquote>
```

**Nested content in blockquote:**
```html
<blockquote class="complex-quote">
  <p>In his famous speech, the president outlined three key priorities:</p>
  
  <ul>
    <li>Economic recovery and job creation</li>
    <li>Healthcare reform and accessibility</li>
    <li>Environmental sustainability</li>
  </ul>
  
  <p>He emphasized that these priorities are interconnected and essential for national progress.</p>
  
  <footer>
    — Presidential Address, 
    <time datetime="2024-01-15">January 15, 2024</time>
  </footer>
</blockquote>

<style>
.complex-quote {
  background: #fff;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 30px;
  margin: 30px 0;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.complex-quote ul {
  margin: 20px 0;
  padding-left: 20px;
}

.complex-quote li {
  margin-bottom: 8px;
  line-height: 1.5;
}
</style>
```

**Multilingual quotation:**
```html
<blockquote lang="fr" cite="https://example.com/french-source">
  <p>Je pense, donc je suis.</p>
  <footer>— René Descartes, <cite>Discours de la Méthode</cite></footer>
</blockquote>

<blockquote lang="de" cite="https://example.com/german-source">
  <p>Zwei Dinge sind unendlich, das Universum und die menschliche Dummheit, aber bei dem Universum bin ich mir noch nicht ganz sicher.</p>
  <footer>— Albert Einstein</footer>
</blockquote>
```

**Blockquote with responsive design:**
```html
<blockquote class="responsive-quote">
  <div class="quote-content">
    <p>Success is not final, failure is not fatal: it is the courage to continue that counts.</p>
  </div>
  <footer class="quote-footer">
    <div class="author-avatar">
      <img src="churchill.jpg" alt="Portrait of Winston Churchill">
    </div>
    <div class="author-info">
      <strong>Winston Churchill</strong>
      <span>Former Prime Minister of the United Kingdom</span>
    </div>
  </footer>
</blockquote>

<style>
.responsive-quote {
  display: flex;
  flex-direction: column;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 15px;
  overflow: hidden;
  margin: 30px 0;
}

.quote-content {
  padding: 40px 40px 20px;
  flex-grow: 1;
}

.quote-content p {
  font-size: 1.3em;
  line-height: 1.6;
  margin: 0;
  text-align: center;
}

.quote-footer {
  display: flex;
  align-items: center;
  gap: 15px;
  padding: 20px 40px;
  background: rgba(0,0,0,0.2);
}

.author-avatar img {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid rgba(255,255,255,0.3);
}

.author-info {
  display: flex;
  flex-direction: column;
}

.author-info strong {
  font-size: 1.1em;
}

.author-info span {
  opacity: 0.8;
  font-size: 0.9em;
}

@media (max-width: 768px) {
  .responsive-quote {
    margin: 20px 0;
  }
  
  .quote-content {
    padding: 30px 20px 15px;
  }
  
  .quote-content p {
    font-size: 1.1em;
  }
  
  .quote-footer {
    padding: 15px 20px;
    flex-direction: column;
    text-align: center;
  }
}
</style>
```

**Blockquote in a grid layout:**
```html
<div class="testimonials-section">
  <h2>What Our Customers Say</h2>
  <div class="testimonials-grid">
    <blockquote class="testimonial-card">
      <div class="rating">★★★★★</div>
      <p>"This service exceeded all our expectations. The team was professional and delivered ahead of schedule."</p>
      <footer>
        <strong>Sarah Johnson</strong>
        <span>Marketing Director</span>
      </footer>
    </blockquote>
    
    <blockquote class="testimonial-card">
      <div class="rating">★★★★★</div>
      <p>"Outstanding results! We saw a 300% ROI within the first quarter. Highly recommended!"</p>
      <footer>
        <strong>Michael Chen</strong>
        <span>CEO, TechStart</span>
      </footer>
    </blockquote>
    
    <blockquote class="testimonial-card">
      <div class="rating">★★★★☆</div>
      <p>"Great product with excellent support. The implementation was smooth and our team adapted quickly."</p>
      <footer>
        <strong>Emily Rodriguez</strong>
        <span>Operations Manager</span>
      </footer>
    </blockquote>
  </div>
</div>

<style>
.testimonials-section {
  padding: 60px 20px;
  background: #f8f9fa;
}

.testimonials-section h2 {
  text-align: center;
  margin-bottom: 40px;
  color: #2c3e50;
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
  max-width: 1200px;
  margin: 0 auto;
}

.testimonial-card {
  background: white;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  display: flex;
  flex-direction: column;
}

.rating {
  color: #f39c12;
  font-size: 1.2em;
  margin-bottom: 15px;
}

.testimonial-card p {
  flex-grow: 1;
  font-style: italic;
  line-height: 1.6;
  margin-bottom: 20px;
}

.testimonial-card footer {
  border-top: 1px solid #eee;
  padding-top: 15px;
}

.testimonial-card strong {
  display: block;
  color: #2c3e50;
}

.testimonial-card span {
  font-size: 0.9em;
  color: #7f8c8d;
}
</style>
```

---

## Notes

* **Accessibility considerations**:
  - Screen readers typically announce as "block quotation"
  - Use `cite` attribute for machine-readable source references
  - Consider providing visible attribution for user clarity
  - Ensure proper color contrast for styled blockquotes

* **Browser support**: Universally supported across all browsers
* **Common mistakes**:
  - Using for inline quotations (use `<q>` instead)
  - Forgetting to provide proper attribution
  - Using purely for visual styling without semantic need
  - Nesting blockquotes within each other

* **Styling considerations**:
  - Default indentation can be overridden with CSS
  - Common to add quotation marks with pseudo-elements
  - Can be styled to match site design while maintaining semantics
  - Consider responsive design for blockquotes in layouts

* **Best practices**:
  - Always provide proper attribution for quoted content
  - Use `cite` attribute for source URLs when available
  - Consider the context and length of the quotation
  - Maintain semantic meaning while applying visual styles
  - Test with screen readers for accessibility

* **SEO implications**:
  - Search engines understand quoted content semantics
  - Proper attribution can help with content credibility
  - `cite` attribute provides machine-readable source information

* **Alternative approaches**:
  - Use `<q>` for short inline quotations
  - Use `<cite>` for source attribution within or after blockquotes
  - Use CSS for purely visual block-level styling without semantics

* **Legal considerations**:
  - Ensure you have rights to reproduce quoted content
  - Provide proper attribution to avoid plagiarism concerns
  - Consider fair use guidelines for lengthy quotations

* **Internationalization**:
  - Quotation mark styles vary by language and region
  - Consider `lang` attribute for quotations in different languages
  - Some cultures have specific quotation presentation conventions

* **Progressive enhancement**:
  - Can be enhanced with JavaScript for interactive features
  - Consider showing source information on click/hover
  - Provide fallback styling for older browsers

---
