# `<cite>`

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

The `<cite>` element represents the title of a creative work, such as a book, paper, essay, poem, song, film, painting, sculpture, exhibition, legal case, report, computer program, website, or other referenced creative work. It provides semantic meaning to citations and references, distinguishing them from regular text and enabling proper attribution of creative content.

---

## Syntax & Variants

+ **Standard syntax**: `<cite>...</cite>`
+ **Not void**: Requires both opening and closing tags
+ **Inline element**: Typically used within text flow
+ **No self-closing variant**: Must contain content between tags
+ **No alternative forms**: Single, consistent syntax across implementations

---

## Attributes

+ **No specific attributes**: The `<cite>` element does not have any attributes specific to its function

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Common usage**: 
  - `class` for additional styling
  - `id` for referencing specific citations
  - `title` for providing additional context
  - `data-*` attributes for metadata (publication date, author, etc.)

---

## Content Model

+ **Permitted content**: Phrasing content
+ **Allowed content**:
  - Text content (the title or name of the work)
  - Character references and entities
  - Other inline elements when necessary
+ **Restricted content**: Should not contain block-level elements
+ **Content guidelines**: Should contain only the title of the work, not author names or publication details

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within paragraphs (`<p>`) for inline citations
  - Inside blockquotes (`<blockquote>`) for source attribution
  - In reference lists and bibliographies
  - Within articles and academic papers
  - In figure captions for attributed works
+ **No usage limits**: Can be used multiple times within a document
+ **Relationship with `<blockquote>`**: Often used together for proper attribution

---

## Behavior and Semantics

+ **Default display**: Inline element
+ **Default styling**:
  - `display: inline`
  - `font-style: italic` (in most browsers)
  - No inherent font weight or color changes
  - Inherits surrounding text properties
+ **Semantic meaning**:
  - Identifies text as the title of a creative work
  - Provides machine-readable citation information
  - Helps search engines and aggregators understand referenced content
  - Supports proper attribution and copyright compliance
+ **Accessibility**:
  - Screen readers may announce as "citation" or change tone
  - Provides semantic distinction from regular text
  - Helps users identify referenced works

---

## Examples

**Basic book citation:**
```html
<p>In his groundbreaking work <cite>A Brief History of Time</cite>, 
Stephen Hawking explores the nature of the universe.</p>
```

**Film title reference:**
```html
<p>The visual effects in <cite>Avatar</cite> revolutionized 
modern filmmaking techniques.</p>
```

**Academic paper citation:**
```html
<p>Recent studies<sup>1</sup> have confirmed the findings 
published in <cite>Journal of Neuroscience, volume 45</cite>.</p>
```

**Styled citation elements:**
```html
<p>The philosophical concepts in <cite class="important-citation">Beyond Good and Evil</cite> 
continue to influence modern thought.</p>

<style>
.important-citation {
  color: #d63384;
  font-weight: 600;
  font-style: normal;
  text-decoration: underline;
  text-underline-offset: 2px;
}
</style>
```

**Multiple citations in context:**
```html
<p>Literary analysis often compares the themes in 
<cite>1984</cite> with those in <cite>Brave New World</cite>, 
both exploring dystopian futures from different perspectives.</p>
```

**Citation with blockquote:**
```html
<blockquote>
  <p>The only way to do great work is to love what you do.</p>
  <footer>— Steve Jobs, <cite>Stanford Commencement Address</cite></footer>
</blockquote>
```

**Website and online resource citation:**
```html
<p>According to the documentation on <cite>MDN Web Docs</cite>, 
the cite element represents the title of a work.</p>

<p>The research was compiled from data available at 
<cite>World Health Organization COVID-19 Dashboard</cite>.</p>
```

**Legal case citation:**
```html
<p>The precedent set by <cite>Roe v. Wade</cite> established 
important legal principles regarding reproductive rights.</p>
```

**Art and exhibition citations:**
```html
<p>Picasso's <cite>Guernica</cite> remains one of the most 
powerful anti-war statements in modern art.</p>

<p>The recent exhibition <cite>Ancient Civilizations Rediscovered</cite> 
at the Metropolitan Museum attracted record attendance.</p>
```

**Music and song citations:**
```html
<p>The album <cite>Abbey Road</cite> features some of 
The Beatles' most innovative studio work.</p>

<p>Her performance of <cite>Moonlight Sonata</cite> 
received critical acclaim for its emotional depth.</p>
```

**Accessible citations with ARIA:**
```html
<p>The research methodology follows the guidelines outlined in 
<cite aria-describedby="cite-desc">Qualitative Research Methods</cite> 
by Dr. Sarah Johnson.</p>

<div id="cite-desc" style="display: none;">
  Published by Academic Press, 2022, ISBN 978-0-123456-78-9
</div>
```

**Citation in a bibliography:**
```html
<div class="bibliography">
  <h2>References</h2>
  <ul>
    <li>Hawking, S. (1988). <cite>A Brief History of Time</cite>. Bantam Books.</li>
    <li>Orwell, G. (1949). <cite>Nineteen Eighty-Four</cite>. Secker & Warburg.</li>
    <li>Tolkien, J.R.R. (1954). <cite>The Lord of the Rings</cite>. Allen & Unwin.</li>
  </ul>
</div>

<style>
.bibliography {
  font-family: 'Times New Roman', serif;
}

.bibliography cite {
  font-style: italic;
}

.bibliography li {
  margin-bottom: 8px;
}
</style>
```

**Citation with publication details:**
```html
<p>The study published in <cite>Nature</cite> 
<time datetime="2023-03-15">(March 15, 2023)</time> 
reveals groundbreaking discoveries in quantum computing.</p>
```

**Computer program and software citation:**
```html
<p>The analysis was performed using <cite>R Statistical Software</cite> 
version 4.2.1 with custom scripts.</p>

<p>Documentation for the <cite>React JavaScript Library</cite> 
provides comprehensive guidance for developers.</p>
```

**Styled academic citations:**
```html
<article class="research-paper">
  <h1>Climate Change Impacts on Coastal Ecosystems</h1>
  
  <section>
    <h2>Literature Review</h2>
    <p>Previous research by Smith et al. in <cite class="journal">Marine Biology</cite> 
    established baseline measurements for coral reef health.</p>
    
    <p>The methodology follows the framework described in 
    <cite class="book">Coastal Ecosystem Management</cite> 
    published by Oxford University Press.</p>
  </section>
</article>

<style>
.research-paper {
  max-width: 800px;
  line-height: 1.6;
}

.research-paper .journal {
  color: #0d6efd;
  font-style: italic;
}

.research-paper .book {
  color: #198754;
  font-weight: 500;
  text-decoration: underline dotted;
}
</style>
```

**Citation with hover information:**
```html
<p>The architectural principles in <cite class="hover-cite" data-year="1960" data-author="Jane Jacobs">The Death and Life of Great American Cities</cite> 
remain relevant in urban planning discussions.</p>

<style>
.hover-cite {
  position: relative;
  cursor: help;
  border-bottom: 1px dotted #666;
}

.hover-cite:hover::after {
  content: attr(data-author) " (" attr(data-year) ")";
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  background: #333;
  color: white;
  padding: 4px 8px;
  border-radius: 4px;
  font-size: 0.8em;
  white-space: nowrap;
  z-index: 1000;
}
</style>
```

**News article citation:**
```html
<div class="news-analysis">
  <p>According to the investigative report <cite>Behind the Silicon Curtain</cite> 
  published in <cite>The New York Times</cite>, tech companies face increasing 
  scrutiny over data privacy practices.</p>
</div>
```

**Citation in figure captions:**
```html
<figure>
  <img src="painting.jpg" alt="Starry Night painting by Vincent van Gogh">
  <figcaption>
    Vincent van Gogh, <cite>The Starry Night</cite> (1889). 
    Oil on canvas. Museum of Modern Art, New York.
  </figcaption>
</figure>
```

**Multiple work types in discussion:**
```html
<article class="cultural-review">
  <h2>Modern Cultural Influences</h2>
  <p>The intersection of technology and art is explored in both 
  the film <cite>Her</cite> and the novel <cite>Ready Player One</cite>, 
  each offering unique perspectives on human-computer relationships.</p>
  
  <p>This theme continues in the video game <cite>Detroit: Become Human</cite> 
  and the television series <cite>Black Mirror</cite>, creating a rich 
  dialogue about artificial consciousness.</p>
</article>
```

**Citation with translation note:**
```html
<p>In <cite lang="fr">Les Misérables</cite> 
<span class="translation">(The Miserable Ones)</span>, 
Victor Hugo masterfully intertwines personal stories with social commentary.</p>

<style>
.translation {
  font-size: 0.9em;
  color: #666;
  font-style: italic;
}
</style>
```

**Academic citation with DOI reference:**
```html
<div class="academic-reference">
  <p>Supporting evidence can be found in the comprehensive study 
  <cite>Global Warming of 1.5°C</cite> published by the 
  Intergovernmental Panel on Climate Change (IPCC).</p>
  
  <p class="doi-reference">
    DOI: <a href="https://doi.org/10.1017/9781009157940">10.1017/9781009157940</a>
  </p>
</div>

<style>
.academic-reference {
  background-color: #f8f9fa;
  padding: 15px;
  border-left: 4px solid #0d6efd;
}

.doi-reference {
  font-size: 0.9em;
  color: #666;
  margin-top: 8px;
}
</style>
```

**Citation in legal documentation:**
```html
<div class="legal-document">
  <h2>Legal Precedents</h2>
  <p>This case builds upon the principles established in 
  <cite>Brown v. Board of Education</cite>, 347 U.S. 483 (1954), 
  which declared state laws establishing separate public schools 
  for black and white students to be unconstitutional.</p>
  
  <p>Furthermore, the reasoning in <cite>Loving v. Virginia</cite>, 
  388 U.S. 1 (1967) supports the argument for marriage equality.</p>
</div>

<style>
.legal-document {
  font-family: 'Times New Roman', serif;
  line-height: 1.8;
}

.legal-document cite {
  font-style: italic;
  font-weight: 500;
}
</style>
```

**Interactive citation with JavaScript:**
```html
<p>The research presented in <cite id="main-citation" data-pubdate="2023" data-publisher="Springer">Advanced Machine Learning Techniques</cite> 
demonstrates significant improvements in predictive accuracy.</p>

<button onclick="showCitationInfo()">Show Citation Details</button>
<div id="citation-info" style="display: none; margin-top: 10px; padding: 10px; background: #f0f0f0;"></div>

<script>
function showCitationInfo() {
  const cite = document.getElementById('main-citation');
  const info = document.getElementById('citation-info');
  
  const pubDate = cite.getAttribute('data-pubdate');
  const publisher = cite.getAttribute('data-publisher');
  
  info.innerHTML = `
    <strong>Publication Details:</strong><br>
    Year: ${pubDate}<br>
    Publisher: ${publisher}
  `;
  info.style.display = 'block';
}
</script>
```

**Citation in multimedia context:**
```html
<div class="multimedia-review">
  <h3>Cinematic Analysis</h3>
  <p>The documentary <cite>An Inconvenient Truth</cite> brought climate 
  change awareness to mainstream audiences, while its sequel 
  <cite>An Inconvenient Sequel: Truth to Power</cite> updated the 
  conversation with recent scientific findings.</p>
  
  <p>Both films complement the book <cite>This Changes Everything: 
  Capitalism vs. The Climate</cite> in presenting compelling 
  environmental arguments.</p>
</div>
```

**Citation with proper punctuation:**
```html
<div class="proper-citation">
  <p>As Shakespeare wrote in <cite>Hamlet</cite>, 
  "To be, or not to be: that is the question."</p>
  
  <p>The study, published in <cite>Science Magazine</cite>, 
  confirms the hypothesis proposed in earlier research.</p>
</div>
```

---

## Notes

* **Semantic importance**: 
  - Provides machine-readable meaning for citations
  - Helps search engines understand referenced works
  - Supports academic integrity and proper attribution
  - Enhances accessibility for assistive technologies
* **Content scope**: 
  - Should contain only the title of the work, not author names
  - Can include subtitles when referencing complete works
  - Should not include publication details or URLs
* **Browser compatibility**: Universally supported across all modern browsers
* **Styling considerations**:
  - Default italic styling follows traditional publishing conventions
  - Custom styling should maintain visual distinction from regular text
  - Consider cultural differences in citation formatting
* **Accessibility considerations**:
  - Screen readers may announce as "citation" or change tone
  - Ensure sufficient color contrast when applying custom styles
  - Provide additional context when citing unfamiliar works
  - Use `lang` attribute when citing works in different languages
* **Common mistakes**:
  - Using for author names instead of work titles
  - Including publication details within the element
  - Using for general emphasis rather than citations
  - Confusing with `<blockquote>` for quotation attribution
* **Best practices**:
  - Use for referencing specific creative works only
  - Maintain consistent citation style throughout document
  - Combine with `<blockquote>` for quoted content with attribution
  - Provide complete reference information in bibliographies
  - Use appropriate punctuation and formatting
* **Relationship with other elements**:
  - Often used with `<blockquote>` for quoted content
  - Can be used with `<q>` for short inline quotations
  - Works well with `<footer>` for attribution in blockquotes
  - Can be combined with `<time>` for publication dates
* **SEO benefits**: 
  - Helps search engines understand content relationships
  - Provides context for referenced works
  - Supports rich snippets and structured data

---
