# `<q>`

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

The `<q>` element represents a short inline quotation. It is designed for quotations that are part of the surrounding content and don't require paragraph breaks. The element semantically marks quoted content and automatically provides language-appropriate quotation marks, distinguishing it from manually typed quotes and indicating the quoted text to assistive technologies and search engines.

---

## Syntax & Variants

+ **Standard syntax**: `<q>...</q>`
+ **Not void**: Requires both opening and closing tags
+ **Inline element**: Can be used within text flow
+ **No self-closing variant**: Must contain content
+ **No alternative forms**: Standard syntax only

---

## Attributes

+ **Core attributes**:
  - `cite` (optional): URL pointing to the source of the quotation

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, `lang`, `dir`, etc.

+ **Event handlers**: All global event attributes supported

---

## Content Model

+ **Permitted content**: Phrasing content
+ **Allowed content**:
  - Text and character references
  - Other inline elements: `<em>`, `<strong>`, `<span>`, `<a>`, etc.
  - Nested quotations
+ **Restricted content**: Cannot contain block-level elements
+ **Nesting**: Can contain other phrasing elements and be nested within them

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within paragraphs (`<p>`)
  - Within headings (`<h1>`-`<h6>`)
  - Within list items (`<li>`)
  - Within table cells (`<td>`, `<th>`)
  - Within other text-level semantic elements
+ **Nesting relationships**:
  - Can contain other phrasing elements
  - Can be nested within other phrasing elements
  - Can contain nested `<q>` elements for quotes within quotes

---

## Behavior and Semantics

+ **Default display**: Inline element
+ **Default styling**:
  - `display: inline`
  - Automatically adds quotation marks (language-specific)
  - No inherent color, weight, or style changes
  - Inherits text properties from parent elements
+ **Quotation mark behavior**:
  - English: Adds double quotes (“ ”)
  - Nested quotes: Uses single quotes (‘ ’)
  - Language-specific: Adapts to `lang` attribute
+ **Semantic meaning**:
  - Indicates inline quoted content
  - Differentiates from manually typed quotation marks
  - Provides machine-readable quotation markup
+ **Accessibility role**:
  - Implicit ARIA role: `none` or `presentation`
  - Screen readers may announce as "quote" or adjust intonation
  - Helps users identify quoted content
+ **SEO significance**: Helps search engines identify and properly attribute quoted content

---

## Examples

**Basic inline quotation:**
```html
<p>As Shakespeare wrote, <q>To be, or not to be: that is the question.</q></p>
```

**Quotation with source attribution:**
```html
<p>
  The CEO stated, 
  <q>Our quarterly results demonstrate strong growth in all key metrics.</q>
  during yesterday's earnings call.
</p>
```

**Quotation with cite attribute:**
```html
<p>
  Albert Einstein once said,
  <q cite="https://example.com/einstein-quotes">
    Imagination is more important than knowledge.
  </q>
</p>
```

**Nested quotations:**
```html
<p>
  The reporter explained, 
  <q>
    The witness stated, 
    <q>I saw the entire incident from my window,</q> 
    which contradicts the initial police report.
  </q>
</p>
```

**Multiple quotations in context:**
```html
<article>
  <h1>Customer Feedback Review</h1>
  <p>
    Our latest survey received overwhelmingly positive responses. 
    One customer wrote, <q>This is the best service I've ever experienced!</q> 
    while another mentioned, <q>I would recommend this company to everyone I know.</q>
    The general sentiment was captured by a third respondent who said,
    <q>Outstanding quality and exceptional customer support.</q>
  </p>
</article>
```

**Styled quotations with CSS:**
```html
<p class="testimonial">
  Our client told us, 
  <q class="highlighted-quote">
    The project was delivered ahead of schedule and exceeded all our expectations.
  </q>
  We're proud of such positive feedback.
</p>

<style>
.testimonial {
  font-size: 1.1em;
  line-height: 1.6;
  color: #333;
}

.highlighted-quote {
  background: #fff3cd;
  padding: 2px 6px;
  border-left: 3px solid #ffc107;
  font-style: italic;
  color: #856404;
}

.highlighted-quote::before,
.highlighted-quote::after {
  color: #d4a017;
  font-weight: bold;
}
</style>
```

**Quotations in different languages:**
```html
<div lang="en">
  <p>He said, <q>Hello world!</q></p>
</div>

<div lang="fr">
  <p>Il a dit : <q>Bonjour le monde !</q></p>
</div>

<div lang="de">
  <p>Er sagte: <q>Hallo Welt!</q></p>
</div>

<div lang="es">
  <p>Él dijo: <q>¡Hola mundo!</q></p>
</div>
```

**Accessible quotations with ARIA:**
```html
<p>
  In her famous speech, 
  <q role="quote" aria-label="Quote from Maya Angelou">
    I've learned that people will forget what you said, 
    people will forget what you did, but people will never forget 
    how you made them feel.
  </q>
  — Maya Angelou
</p>
```

**Quotations in academic writing:**
```html
<article class="academic-paper">
  <h1>Literary Analysis of Modern Poetry</h1>
  
  <p>
    As noted by Smith (2020), 
    <q cite="#smith2020">
      The poet's use of imagery creates a vivid landscape of emotional turmoil.
    </q> 
    This perspective aligns with Johnson's earlier observation that 
    <q cite="#johnson2018">
      Modern poetry often employs visual metaphors to convey complex psychological states.
    </q>
  </p>
  
  <p>
    The poem itself begins with the striking line, 
    <q class="poem-line">The silent screams of forgotten dreams</q>, 
    which immediately establishes the thematic tension.
  </p>
  
  <footer class="references">
    <h2>References</h2>
    <ul>
      <li id="smith2020">Smith, J. (2020). Modern Poetic Imagery. Literary Press.</li>
      <li id="johnson2018">Johnson, M. (2018). Metaphor and Meaning. Academic Publishing.</li>
    </ul>
  </footer>
</article>

<style>
.academic-paper {
  max-width: 800px;
  margin: 0 auto;
  line-height: 1.7;
  font-family: 'Times New Roman', serif;
}

.poem-line {
  font-style: italic;
  color: #2c5530;
}

.references {
  margin-top: 2rem;
  padding-top: 1rem;
  border-top: 1px solid #ccc;
  font-size: 0.9em;
}

.references h2 {
  color: #555;
  font-size: 1.2em;
}
</style>
```

**Interactive quotation with JavaScript:**
```html
<div class="quote-container">
  <p>
    Customer feedback: 
    <q id="dynamic-quote" cite="https://api.example.com/feedback/123">
      Loading customer comment...
    </q>
  </p>
  <button onclick="loadNewQuote()">Load Another Quote</button>
</div>

<style>
.quote-container {
  background: #f8f9fa;
  padding: 20px;
  border-radius: 8px;
  border: 1px solid #e9ecef;
  max-width: 500px;
  margin: 20px auto;
}

.quote-container q {
  display: block;
  margin: 10px 0;
  padding: 15px;
  background: white;
  border-left: 4px solid #007bff;
  font-style: italic;
  color: #495057;
}

.quote-container button {
  background: #007bff;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 0.9em;
}

.quote-container button:hover {
  background: #0056b3;
}
</style>

<script>
const quotes = [
  {
    text: "The product quality exceeded my expectations. Highly recommended!",
    source: "https://example.com/reviews/1"
  },
  {
    text: "Excellent customer service and fast delivery. Will buy again.",
    source: "https://example.com/reviews/2"
  },
  {
    text: "Outstanding value for money. The features are exactly what I needed.",
    source: "https://example.com/reviews/3"
  }
];

function loadNewQuote() {
  const quoteElement = document.getElementById('dynamic-quote');
  const randomQuote = quotes[Math.floor(Math.random() * quotes.length)];
  
  quoteElement.textContent = randomQuote.text;
  quoteElement.setAttribute('cite', randomQuote.source);
}

// Load initial quote
loadNewQuote();
</script>
```

**Quotations in conversation format:**
```html
<div class="conversation">
  <h3>Team Meeting Discussion</h3>
  
  <p><strong>Manager:</strong> <q>What's the status of the project?</q></p>
  
  <p><strong>Developer:</strong> <q>We're on track for Friday's deadline.</q></p>
  
  <p><strong>Designer:</strong> <q>The final mockups are ready for review.</q></p>
  
  <p><strong>Manager:</strong> <q>Excellent! Let's schedule a demo for Thursday.</q></p>
</div>

<style>
.conversation {
  background: #e8f4f8;
  padding: 20px;
  border-radius: 8px;
  border-left: 4px solid #17a2b8;
}

.conversation h3 {
  margin-top: 0;
  color: #055160;
  border-bottom: 1px solid #9fcdd7;
  padding-bottom: 8px;
}

.conversation p {
  margin: 12px 0;
  padding: 8px 12px;
  background: white;
  border-radius: 4px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
}

.conversation strong {
  color: #055160;
  display: inline-block;
  min-width: 80px;
}
</style>
```

**Blockquote vs inline quote comparison:**
```html
<article>
  <h1>Understanding HTML Quotation Elements</h1>
  
  <section>
    <h2>Inline Quotations with &lt;q&gt;</h2>
    <p>
      Use <code>&lt;q&gt;</code> for short quotes within text flow. 
      For example: The professor said, <q>Always validate your HTML markup.</q>
    </p>
  </section>
  
  <section>
    <h2>Block Quotations with &lt;blockquote&gt;</h2>
    <p>Use <code>&lt;blockquote&gt;</code> for longer, standalone quotes:</p>
    <blockquote cite="https://example.com/long-quote">
      <p>
        This is a longer quotation that should be set off from the main text. 
        It typically spans multiple lines and is displayed as a separate block 
        with indentation or other styling to distinguish it from regular content.
      </p>
      <footer>— Source Author, <cite>Book Title</cite></footer>
    </blockquote>
  </section>
</article>

<style>
article {
  max-width: 700px;
  margin: 0 auto;
  line-height: 1.6;
}

section {
  margin: 2rem 0;
  padding: 1.5rem;
  background: #f8f9fa;
  border-radius: 6px;
}

blockquote {
  background: white;
  padding: 1.5rem;
  border-left: 4px solid #6c757d;
  margin: 1rem 0;
  font-style: italic;
  color: #495057;
}

blockquote footer {
  margin-top: 1rem;
  font-style: normal;
  color: #6c757d;
  text-align: right;
}

code {
  background: #e9ecef;
  padding: 2px 6px;
  border-radius: 3px;
  font-family: 'Monaco', 'Menlo', monospace;
  font-size: 0.9em;
}
</style>
```

**Quotations with citation links:**
```html
<div class="attributed-quotes">
  <h3>Famous Quotes</h3>
  
  <div class="quote-item">
    <p>
      <q cite="https://www.goodreads.com/quotes/7">
        It is not the strongest of the species that survives, 
        nor the most intelligent that survives. It is the one 
        that is most adaptable to change.
      </q>
    </p>
    <p class="attribution">
      — <a href="https://en.wikipedia.org/wiki/Charles_Darwin">Charles Darwin</a>
    </p>
  </div>
  
  <div class="quote-item">
    <p>
      <q cite="https://www.goodreads.com/quotes/200">
        The only way to do great work is to love what you do.
      </q>
    </p>
    <p class="attribution">
      — <a href="https://en.wikipedia.org/wiki/Steve_Jobs">Steve Jobs</a>
    </p>
  </div>
</div>

<style>
.attributed-quotes {
  max-width: 600px;
  margin: 0 auto;
}

.quote-item {
  background: white;
  padding: 20px;
  margin: 20px 0;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  border-left: 4px solid #4a90e2;
}

.quote-item q {
  font-size: 1.1em;
  line-height: 1.6;
  color: #333;
  display: block;
  margin-bottom: 10px;
}

.attribution {
  text-align: right;
  color: #666;
  font-style: italic;
  margin: 0;
}

.attribution a {
  color: #4a90e2;
  text-decoration: none;
}

.attribution a:hover {
  text-decoration: underline;
}
</style>
```

**Responsive quotation design:**
```html
<div class="testimonial-grid">
  <div class="testimonial-card">
    <q>
      This service transformed our business operations. 
      The efficiency gains have been remarkable.
    </q>
    <div class="client">— Sarah Chen, Tech Solutions Inc.</div>
  </div>
  
  <div class="testimonial-card">
    <q>
      Outstanding support and incredible product quality. 
      We've been customers for over three years and couldn't be happier.
    </q>
    <div class="client">— Marcus Johnson, Global Enterprises</div>
  </div>
  
  <div class="testimonial-card">
    <q>
      The implementation was seamless and the results exceeded 
      our expectations. Highly recommended for any growing business.
    </q>
    <div class="client">— Elena Rodriguez, Innovation Labs</div>
  </div>
</div>

<style>
.testimonial-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  margin: 2rem 0;
}

.testimonial-card {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
}

.testimonial-card q {
  display: block;
  font-size: 1.1em;
  line-height: 1.6;
  margin-bottom: 15px;
  font-style: italic;
}

.testimonial-card q::before,
.testimonial-card q::after {
  color: rgba(255,255,255,0.7);
  font-size: 1.5em;
  font-weight: bold;
}

.client {
  text-align: right;
  font-weight: 600;
  opacity: 0.9;
  font-size: 0.9em;
}

@media (max-width: 768px) {
  .testimonial-grid {
    grid-template-columns: 1fr;
    gap: 15px;
  }
  
  .testimonial-card {
    padding: 20px;
  }
}
</style>
```

**Quotations in legal documents:**
```html
<div class="legal-document">
  <h2>Service Agreement</h2>
  
  <p>
    The Client agrees to the following terms: 
    <q class="legal-quote">
      All intellectual property developed during the engagement 
      shall remain the property of the Service Provider until 
      full payment is received.
    </q>
  </p>
  
  <p>
    Additionally, 
    <q class="legal-quote">
      Confidential information shared between parties shall not 
      be disclosed to third parties without written consent.
    </q>
  </p>
  
  <div class="signature">
    <p>Accepted and agreed:</p>
    <q class="signature-line">[Client Signature]</q>
  </div>
</div>

<style>
.legal-document {
  max-width: 700px;
  margin: 0 auto;
  background: white;
  padding: 2rem;
  border: 1px solid #ddd;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.legal-quote {
  background: #f8f9fa;
  padding: 10px 15px;
  border-left: 3px solid #dc3545;
  display: block;
  margin: 10px 0;
  font-family: 'Times New Roman', serif;
}

.signature {
  margin-top: 3rem;
  padding-top: 1rem;
  border-top: 2px solid #333;
  text-align: center;
}

.signature-line {
  display: inline-block;
  min-width: 200px;
  border-bottom: 1px solid #333;
  padding: 0 20px;
  font-style: normal;
}
</style>
```

---

## Notes

* **Semantic vs. presentational**: 
  - `<q>` conveys semantic meaning (inline quotation)
  - Manually typing quotes is purely presentational
  - Use `<q>` when the quotation has semantic significance
* **Automatic quotation marks**:
  - Browsers automatically add language-appropriate quotes
  - Nested quotes automatically switch to single quotes
  - Quotes adapt to the `lang` attribute of parent elements
* **Accessibility considerations**:
  - Screen readers may announce quoted content differently
  - The `cite` attribute provides machine-readable source information
  - Don't rely solely on visual quotation marks for meaning
* **Browser support**: Universally supported across all modern browsers
* **Common misuse**:
  - Using `<q>` for block-level quotations (use `<blockquote>` instead)
  - Manually adding quotation marks inside `<q>` elements
  - Using for non-quotation purposes like emphasis
* **Styling considerations**:
  - Default quote styling can be overridden with CSS `quotes` property
  - Use `::before` and `::after` pseudo-elements for custom quotes
  - Maintain sufficient contrast and readability
* **Internationalization**: 
  - Quotation marks vary by language and culture
  - The `lang` attribute ensures correct quote rendering
  - Consider right-to-left languages for proper quote placement
* **Performance**: Minimal performance impact as it's a simple inline element
* **Best practices**:
  - Use for genuine quotations, not for emphasis or decoration
  - Include the `cite` attribute when referencing online sources
  - Nest properly for quotes within quotes
  - Combine with other semantic elements for rich content
* **SEO benefits**: Helps search engines identify and attribute quoted content properly

---
