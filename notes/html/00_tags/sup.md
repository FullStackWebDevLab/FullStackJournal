# `<sup>`

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

The `<sup>` element represents superscript text, which appears half a character above the normal line of type and is typically rendered in a smaller font size. It is used for mathematical exponents, footnotes, ordinal indicators, and other typographical conventions where text needs to be raised above the baseline. The element carries semantic meaning beyond mere visual presentation.

---

## Syntax & Variants

+ **Standard syntax**: `<sup>...</sup>`
+ **Not void**: Requires both opening and closing tags
+ **Inline element**: Can be used within text flow
+ **No self-closing variant**: Must contain content
+ **No alternative forms**: Standard syntax only

---

## Attributes

+ **No specific attributes**: The `<sup>` element does not have any element-specific attributes
+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, `lang`, `dir`, etc.
+ **Event handlers**: All global event attributes supported

---

## Content Model

+ **Permitted content**: Phrasing content
+ **Allowed content**:
  - Text and character references
  - Other inline elements: `<em>`, `<strong>`, `<span>`, etc.
  - Mathematical symbols and operators
+ **Restricted content**: Cannot contain block-level elements
+ **Nesting**: Can be nested with other text-level semantic elements

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within paragraphs (`<p>`)
  - Within headings (`<h1>`-`<h6>`)
  - Within list items (`<li>`)
  - Within table cells (`<td>`, `<th>`)
  - Within mathematical expressions
  - Within citations and references
+ **Nesting relationships**:
  - Can contain other phrasing elements
  - Can be nested within other phrasing elements
  - Often used alongside `<sub>` for complex notations

---

## Behavior and Semantics

+ **Default display**: Inline element
+ **Default styling**:
  - `display: inline`
  - `vertical-align: super`
  - `font-size: smaller` (typically 75-80% of parent font size)
  - `line-height: normal` (adjusted to prevent line height issues)
  - No inherent color or weight changes
+ **Semantic meaning**:
  - Indicates superscript text for mathematical or typographical purposes
  - Differentiates from purely presentational raised text
  - Carries meaning for accessibility and machine readability
+ **Accessibility role**:
  - Implicit ARIA role: `subscript` (note: despite the name, this covers both superscript and subscript in ARIA)
  - Screen readers may announce as "superscript" or adjust pronunciation
  - Important for mathematical and scientific content accessibility
+ **SEO significance**: Helps search engines properly interpret mathematical and scientific content

---

## Examples

**Basic mathematical exponents:**
```html
<p>The Pythagorean theorem: a<sup>2</sup> + b<sup>2</sup> = c<sup>2</sup></p>

<p>Euler's identity: e<sup>iπ</sup> + 1 = 0</p>

<p>Quadratic formula: x = (-b ± √(b<sup>2</sup> - 4ac)) / 2a</p>
```

**Scientific notation:**
```html
<p>Speed of light: 3 × 10<sup>8</sup> m/s</p>

<p>Avogadro's number: 6.022 × 10<sup>23</sup> mol<sup>-1</sup></p>

<p>Planck's constant: 6.626 × 10<sup>-34</sup> J⋅s</p>
```

**Footnotes and references:**
```html
<article>
  <h1>The History of Computing</h1>
  
  <p>
    The first electronic computers were developed during World War II, 
    with notable examples including the Colossus<sup><a href="#fn1">1</a></sup> 
    and ENIAC<sup><a href="#fn2">2</a></sup>. These machines paved the way 
    for modern computing architecture.
  </p>
  
  <p>
    The transistor, invented in 1947<sup><a href="#fn3">3</a></sup>, 
    revolutionized computer design and led to the development of 
    integrated circuits in the 1950s.
  </p>
  
  <footer>
    <h2>References</h2>
    <ol>
      <li id="fn1">Flowers, T. H. (1943). Colossus: The First Electronic Computer.</li>
      <li id="fn2">Mauchly, J. W., & Eckert, J. P. (1946). ENIAC Technical Manual.</li>
      <li id="fn3">Bardeen, J., & Brattain, W. H. (1948). The Transistor, A Semi-Conductor Triode.</li>
    </ol>
  </footer>
</article>
```

**Ordinal numbers:**
```html
<p>The 1<sup>st</sup>, 2<sup>nd</sup>, 3<sup>rd</sup>, and 4<sup>th</sup> places have been decided.</p>

<p>We're celebrating our company's 25<sup>th</sup> anniversary this year.</p>

<p>King Louis XIV<sup>th</sup> of France reigned for 72 years.</p>
```

**Chemical formulas:**
```html
<p>Water: H<sub>2</sub>O</p>

<p>Sulfuric acid: H<sub>2</sub>SO<sub>4</sub></p>

<p>Glucose: C<sub>6</sub>H<sub>12</sub>O<sub>6</sub></p>

<p>Ionic compounds: Na<sup>+</sup>Cl<sup>-</sup>, Ca<sup>2+</sup>O<sup>2-</sup></p>
```

**Styled mathematical expressions:**
```html
<div class="math-expression">
  <p>Binomial theorem:</p>
  <p class="formula">
    (a + b)<sup>n</sup> = 
    ∑<sub>k=0</sub><sup>n</sup> 
    <span class="binom">n</span>
    a<sup>n-k</sup>b<sup>k</sup>
  </p>
  
  <p>Taylor series expansion:</p>
  <p class="formula">
    f(x) = 
    ∑<sub>n=0</sub><sup>∞</sup> 
    <span class="fraction">
      <span>f<sup>(n)</sup>(a)</span>
      <span>n!</span>
    </span>
    (x - a)<sup>n</sup>
  </p>
</div>

<style>
.math-expression {
  background: #f8f9fa;
  padding: 20px;
  border-radius: 8px;
  border-left: 4px solid #4a90e2;
}

.formula {
  font-family: 'Times New Roman', serif;
  font-size: 1.2em;
  text-align: center;
  margin: 15px 0;
}

.binom {
  display: inline-block;
  vertical-align: middle;
  margin: 0 2px;
}

.fraction {
  display: inline-block;
  vertical-align: middle;
  text-align: center;
  margin: 0 5px;
}

.fraction span {
  display: block;
}

.fraction span:first-child {
  border-bottom: 1px solid #000;
  padding: 0 5px;
}
</style>
```

**Trademark and copyright symbols:**
```html
<div class="product-info">
  <h2>SuperWidget<sup>®</sup> Pro</h2>
  
  <p>
    SuperWidget<sup>®</sup> is a registered trademark of 
    Tech Innovations Inc.<sup>™</sup>
  </p>
  
  <p class="copyright">
    Copyright<sup>©</sup> 2024 Tech Innovations Inc. All rights reserved.
  </p>
  
  <p>
    This product is protected by US Patent No. 9,876,543<sup>†</sup>
  </p>
</div>

<style>
.product-info {
  background: white;
  padding: 20px;
  border: 1px solid #e0e0e0;
  border-radius: 6px;
  max-width: 500px;
}

.copyright {
  color: #666;
  font-size: 0.9em;
  border-top: 1px solid #f0f0f0;
  padding-top: 10px;
}
</style>
```

**Date formats and abbreviations:**
```html
<div class="document-meta">
  <p>Effective date: January 1<sup>st</sup>, 2024</p>
  
  <p>Meeting scheduled for the 3<sup>rd</sup> Thursday of each month</p>
  
  <p>Reference: ISO 8601 date format: 2024-01-01<sup>*</sup></p>
  
  <p class="footnote">
    <sup>*</sup> International standard for date and time representation
  </p>
</div>

<style>
.document-meta {
  background: #fff3cd;
  padding: 15px;
  border: 1px solid #ffeaa7;
  border-radius: 4px;
}

.footnote {
  margin-top: 10px;
  padding-top: 10px;
  border-top: 1px dashed #ffc107;
  font-size: 0.9em;
  color: #856404;
}
</style>
```

**Accessible mathematical content with ARIA:**
```html
<div class="accessible-math">
  <h3>Quadratic Equation Solution</h3>
  
  <p 
    role="math" 
    aria-label="x equals negative b plus or minus the square root of b squared minus 4 times a times c, all divided by 2 times a">
    x = (-b ± √(b<sup>2</sup> - 4ac)) / 2a
  </p>
  
  <p 
    role="math" 
    aria-label="e to the power of i times pi plus 1 equals 0">
    e<sup>iπ</sup> + 1 = 0
  </p>
  
  <p 
    role="math" 
    aria-label="The integral from a to b of f of x dx">
    ∫<sub>a</sub><sup>b</sup> f(x) dx
  </p>
</div>

<style>
.accessible-math {
  background: #e8f4f8;
  padding: 20px;
  border-radius: 8px;
  font-family: 'Times New Roman', serif;
}

.accessible-math p[role="math"] {
  font-size: 1.3em;
  text-align: center;
  margin: 15px 0;
  padding: 10px;
  background: white;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
</style>
```

**Complex nested superscripts:**
```html
<div class="complex-notation">
  <p>Double exponent: x<sup>y<sup>2</sup></sup></p>
  
  <p>Nested operations: (a<sup>2</sup>)<sup>3</sup> = a<sup>6</sup></p>
  
  <p>Function composition: f<sup>n</sup>(x) = f(f<sup>n-1</sup>(x))</p>
  
  <p>Tensor notation: R<sup>α</sup><sub>βγδ</sub></p>
</div>

<style>
.complex-notation {
  font-family: 'Cambria Math', 'Times New Roman', serif;
  padding: 15px;
  background: #f5f5f5;
  border-radius: 6px;
}

.complex-notation p {
  margin: 10px 0;
  padding: 8px;
  background: white;
  border-radius: 4px;
  text-align: center;
}
</style>
```

**Styled footnotes with hover effects:**
```html
<article class="research-paper">
  <h1>Climate Change Impacts on Biodiversity</h1>
  
  <p>
    Recent studies indicate that global temperatures have risen by 
    approximately 1.1°C since pre-industrial levels<sup class="footnote-ref">1</sup>. 
    This warming has led to significant shifts in species distribution 
    and population dynamics<sup class="footnote-ref">2</sup>.
  </p>
  
  <p>
    The Intergovernmental Panel on Climate Change (IPCC) projects 
    that under current emission scenarios, global warming could 
    reach 1.5°C between 2030 and 2052<sup class="footnote-ref">3</sup>. 
    This threshold is critical for many ecosystems<sup class="footnote-ref">4</sup>.
  </p>
  
  <aside class="footnotes">
    <h3>References</h3>
    <ol>
      <li id="ref1">IPCC AR6 WG1, 2021</li>
      <li id="ref2">Pecl et al., Nature, 2017</li>
      <li id="ref3">IPCC Special Report, 2018</li>
      <li id="ref4">Hoegh-Guldberg et al., Science, 2018</li>
    </ol>
  </aside>
</article>

<style>
.research-paper {
  max-width: 800px;
  margin: 0 auto;
  line-height: 1.7;
  font-family: 'Georgia', serif;
}

.footnote-ref {
  color: #007bff;
  text-decoration: none;
  cursor: pointer;
  font-size: 0.8em;
  padding: 1px 3px;
  border-radius: 2px;
  transition: all 0.2s ease;
}

.footnote-ref:hover {
  background: #007bff;
  color: white;
}

.footnotes {
  margin-top: 40px;
  padding-top: 20px;
  border-top: 2px solid #e9ecef;
  font-size: 0.9em;
}

.footnotes h3 {
  color: #495057;
  margin-bottom: 15px;
}

.footnotes ol {
  color: #6c757d;
  line-height: 1.6;
}
</style>
```

**Chemical equations with proper formatting:**
```html
<div class="chemical-equations">
  <h3>Chemical Reactions</h3>
  
  <p>Photosynthesis:</p>
  <p class="equation">
    6CO<sub>2</sub> + 6H<sub>2</sub>O → C<sub>6</sub>H<sub>12</sub>O<sub>6</sub> + 6O<sub>2</sub>
  </p>
  
  <p>Combustion of methane:</p>
  <p class="equation">
    CH<sub>4</sub> + 2O<sub>2</sub> → CO<sub>2</sub> + 2H<sub>2</sub>O
  </p>
  
  <p>Acid-base reaction:</p>
  <p class="equation">
    H<sup>+</sup> + OH<sup>-</sup> → H<sub>2</sub>O
  </p>
  
  <p>Redox reaction:</p>
  <p class="equation">
    2Na + Cl<sub>2</sub> → 2Na<sup>+</sup>Cl<sup>-</sup>
  </p>
</div>

<style>
.chemical-equations {
  background: #f8f9fa;
  padding: 20px;
  border-radius: 8px;
  border: 1px solid #dee2e6;
}

.chemical-equations h3 {
  color: #2c5530;
  margin-top: 0;
  border-bottom: 2px solid #2c5530;
  padding-bottom: 8px;
}

.equation {
  font-family: 'Cambria Math', 'Times New Roman', serif;
  font-size: 1.3em;
  text-align: center;
  margin: 15px 0;
  padding: 10px;
  background: white;
  border-radius: 4px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
}
</style>
```

**Responsive typography with superscript:**
```html
<div class="responsive-content">
  <h2>Mathematical Constants</h2>
  
  <div class="constant-grid">
    <div class="constant">
      <span class="name">π (Pi)</span>
      <span class="value">3.14159<sup>†</sup></span>
    </div>
    
    <div class="constant">
      <span class="name">e (Euler's number)</span>
      <span class="value">2.71828<sup>†</sup></span>
    </div>
    
    <div class="constant">
      <span class="name">φ (Golden ratio)</span>
      <span class="value">1.61803<sup>*</sup></span>
    </div>
    
    <div class="constant">
      <span class="name">c (Speed of light)</span>
      <span class="value">3 × 10<sup>8</sup> m/s</span>
    </div>
  </div>
  
  <div class="legend">
    <p><sup>†</sup> Irrational number</p>
    <p><sup>*</sup> Algebraic number</p>
  </div>
</div>

<style>
.responsive-content {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.constant-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 15px;
  margin: 20px 0;
}

.constant {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px;
  background: white;
  border: 1px solid #e0e0e0;
  border-radius: 6px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}

.name {
  font-weight: 600;
  color: #333;
}

.value {
  font-family: 'Monaco', 'Menlo', monospace;
  color: #007bff;
}

.legend {
  background: #f8f9fa;
  padding: 15px;
  border-radius: 4px;
  font-size: 0.9em;
  color: #666;
}

.legend p {
  margin: 5px 0;
}

@media (max-width: 480px) {
  .constant {
    flex-direction: column;
    align-items: flex-start;
    gap: 5px;
  }
  
  .constant-grid {
    grid-template-columns: 1fr;
  }
}
</style>
```

**Dynamic superscript with JavaScript:**
```html
<div class="interactive-math">
  <h3>Exponent Calculator</h3>
  
  <div class="calculator">
    <label>
      Base:
      <input type="number" id="base" value="2" step="any">
    </label>
    
    <label>
      Exponent:
      <input type="number" id="exponent" value="3" step="any">
    </label>
    
    <div class="result">
      <span id="expression">2<sup>3</sup></span> = <span id="output">8</span>
    </div>
  </div>
</div>

<style>
.interactive-math {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 30px;
  border-radius: 12px;
  max-width: 400px;
  margin: 20px auto;
}

.calculator {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.calculator label {
  display: flex;
  justify-content: between;
  align-items: center;
  gap: 10px;
}

.calculator input {
  padding: 8px 12px;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  width: 80px;
}

.result {
  margin-top: 15px;
  padding: 15px;
  background: rgba(255,255,255,0.1);
  border-radius: 6px;
  text-align: center;
  font-size: 1.3em;
  font-family: 'Times New Roman', serif;
}

#expression {
  font-weight: bold;
}
</style>

<script>
function updateExpression() {
  const base = document.getElementById('base').value;
  const exponent = document.getElementById('exponent').value;
  const expression = document.getElementById('expression');
  const output = document.getElementById('output');
  
  expression.innerHTML = `${base}<sup>${exponent}</sup>`;
  output.textContent = Math.pow(parseFloat(base), parseFloat(exponent));
}

document.getElementById('base').addEventListener('input', updateExpression);
document.getElementById('exponent').addEventListener('input', updateExpression);
</script>
```

---

## Notes

* **Semantic vs. presentational**: 
  - `<sup>` conveys semantic meaning (superscript text)
  - CSS `vertical-align: super` is purely presentational
  - Use `<sup>` when the raised text has mathematical or typographical significance
* **Accessibility considerations**:
  - Screen readers may announce superscript content differently
  - For complex mathematical expressions, use MathML or provide ARIA labels
  - Ensure superscript text remains readable and doesn't break line height
* **Browser support**: Universally supported across all browsers
* **Common misuse**:
  - Using `<sup>` for purely visual effects without semantic meaning
  - Overusing for minor typographical elements
  - Confusing with `<sub>` (subscript)
* **Styling considerations**:
  - Default styling can be overridden with CSS
  - Consider adjusting `line-height` to prevent layout issues
  - Ensure sufficient size and contrast for readability
* **Mathematical best practices**:
  - Use with `<sub>` for complex notations
  - Consider MathML for advanced mathematical expressions
  - Provide alternative text descriptions for screen readers
* **Performance**: Minimal performance impact as it's a simple inline element
* **Internationalization**: 
  - Superscript conventions may vary across languages and cultures
  - Ensure proper rendering in different writing systems
* **Line height issues**: Superscript elements can affect line spacing; use CSS adjustments when necessary

---
