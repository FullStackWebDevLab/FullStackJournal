# `<sub>`

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

The `<sub>` element represents subscript text, which appears half a character below the normal line of type and is typically rendered in a smaller font size. It is used for various scientific, mathematical, and technical notations where text needs to be positioned below the baseline, such as chemical formulas, mathematical expressions, footnotes, and variable indices.

---

## Syntax & Variants

+ **Standard syntax**: `<sub>...</sub>`
+ **Not void**: Requires both opening and closing tags
+ **Inline element**: Flows with surrounding text content
+ **No self-closing variant**: Must contain content between tags
+ **No alternative forms**: Single, consistent syntax across implementations

---

## Attributes

+ **No specific attributes**: The `<sub>` element does not have any attributes specific to its function

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Common usage**: Typically used with `class` for additional styling or `id` for referencing

---

## Content Model

+ **Permitted content**: Phrasing content
+ **Allowed content**:
  - Text and character references
  - Other inline elements: `<span>`, `<em>`, `<strong>`, etc.
  - Mathematical symbols and operators
+ **Restricted content**: Cannot contain block-level elements
+ **Nesting**: Can contain other inline elements and be nested within them

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within paragraphs (`<p>`) for scientific notation
  - Inside mathematical expressions
  - In chemical formulas
  - For footnote references
  - Within table cells for data presentation
+ **No usage limits**: Can be used multiple times within a document
+ **Often paired**: Frequently used alongside `<sup>` for superscript notation

---

## Behavior and Semantics

+ **Default display**: Inline element
+ **Default styling**:
  - `display: inline`
  - `vertical-align: sub`
  - `font-size: smaller` (typically 75-80% of parent font size)
  - `line-height: normal` (adjusted for proper vertical alignment)
  - `baseline-shift: sub` (in some rendering engines)
+ **Semantic meaning**:
  - Indicates text that should be rendered as subscript
  - Provides meaningful structure for technical and scientific content
  - Helps maintain proper reading flow and comprehension
+ **Accessibility**:
  - Screen readers typically process subscript text normally
  - Provides semantic meaning for assistive technologies
  - Important for proper interpretation of technical content

---

## Examples

**Basic chemical formulas:**
```html
<p>The chemical formula for water is H<sub>2</sub>O.</p>

<p>Carbon dioxide is written as CO<sub>2</sub>.</p>

<p>Sulfuric acid: H<sub>2</sub>SO<sub>4</sub></p>
```

**Mathematical expressions:**
```html
<p>The quadratic formula: x = (-b ± √(b<sub>2</sub> - 4ac)) / 2a</p>

<p>Variable indices: x<sub>1</sub>, x<sub>2</sub>, x<sub>n</sub></p>

<p>Logarithm base: log<sub>10</sub> 100 = 2</p>
```

**Footnotes and references:**
```html
<p>The study concluded significant results<sub>1</sub> that contradict 
previous findings<sub>2,3</sub>.</p>

<footer>
  <p><sub>1</sub> Smith et al., 2023</p>
  <p><sub>2</sub> Johnson, 2021</p>
  <p><sub>3</sub> Williams, 2020</p>
</footer>
```

**Styled subscript elements:**
```html
<p>Normal text with <sub class="styled-sub">styled subscript</sub> for emphasis.</p>

<p>Chemical notation: C<sub class="chemical">6</sub>H<sub class="chemical">12</sub>O<sub class="chemical">6</sub></p>

<style>
.styled-sub {
  color: #d63384;
  font-weight: bold;
  background-color: #f8f9fa;
  padding: 0 2px;
  border-radius: 2px;
}

.chemical {
  color: #0d6efd;
  font-size: 0.7em;
}
</style>
```

**Complex chemical compounds:**
```html
<p>Common compounds:</p>
<ul>
  <li>Glucose: C<sub>6</sub>H<sub>12</sub>O<sub>6</sub></li>
  <li>Calcium carbonate: CaCO<sub>3</sub></li>
  <li>Ammonium nitrate: NH<sub>4</sub>NO<sub>3</sub></li>
  <li>Ferric oxide: Fe<sub>2</sub>O<sub>3</sub></li>
</ul>
```

**Mathematical sequences and series:**
```html
<p>Fibonacci sequence: F<sub>0</sub> = 0, F<sub>1</sub> = 1, F<sub>n</sub> = F<sub>n-1</sub> + F<sub>n-2</sub></p>

<p>Geometric series: S<sub>n</sub> = a<sub>1</sub>(1 - r<sup>n</sup>) / (1 - r)</p>

<p>Matrix notation: A<sub>ij</sub> where i represents the row and j the column</p>
```

**Combined with superscript for complex notation:**
```html
<p>Ionic compounds: Ba<sup>2+</sup>SO<sub>4</sub><sup>2-</sup></p>

<p>Mathematical expressions: x<sub>i</sub><sup>2</sup> + y<sub>i</sub><sup>2</sup> = r<sup>2</sup></p>

<p>Isotope notation: <sup>14</sup>C<sub>6</sub></p>
```

**Variable naming in programming:**
```html
<p>Array indices: array<sub>0</sub>, array<sub>1</sub>, array<sub>n-1</sub></p>

<p>Mathematical variables: μ<sub>0</sub> (permeability of free space)</p>

<p>Statistical notation: σ<sub>x</sub> (standard deviation of x)</p>
```

**Accessible scientific content:**
```html
<p>The molecular formula for caffeine is 
<span aria-label="C 8 H 10 N 4 O 2">C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub></span>.</p>

<p>Coordinate points: 
<span aria-label="point x 1 y 1">(x<sub>1</sub>, y<sub>1</sub>)</span> 
and <span aria-label="point x 2 y 2">(x<sub>2</sub>, y<sub>2</sub>)</span></p>
```

**Styled mathematical documentation:**
```html
<div class="math-documentation">
  <h3>Polynomial Equations</h3>
  <p>A polynomial of degree <var>n</var> has the general form:</p>
  <p class="equation">
    P<sub><var>n</var></sub>(x) = a<sub>0</sub> + a<sub>1</sub>x + a<sub>2</sub>x<sup>2</sup> + ... + a<sub><var>n</var></sub>x<sup><var>n</var></sup>
  </p>
  <p>Where a<sub>i</sub> represents the coefficient for each term.</p>
</div>

<style>
.math-documentation {
  font-family: 'Times New Roman', serif;
}

.equation {
  text-align: center;
  font-size: 1.2em;
  margin: 20px 0;
  padding: 10px;
  background-color: #f8f9fa;
  border-radius: 4px;
}

var {
  font-style: italic;
  color: #d63384;
}
</style>
```

**Chemical equations with states:**
```html
<div class="chemical-equation">
  <p>Combustion of methane:</p>
  <p>CH<sub>4</sub>(g) + 2O<sub>2</sub>(g) → CO<sub>2</sub>(g) + 2H<sub>2</sub>O(l)</p>
</div>

<div class="chemical-equation">
  <p>Neutralization reaction:</p>
  <p>HCl(aq) + NaOH(aq) → NaCl(aq) + H<sub>2</sub>O(l)</p>
</div>

<style>
.chemical-equation {
  margin: 15px 0;
  padding: 10px;
  border-left: 4px solid #0d6efd;
  background-color: #f8f9fa;
}

.chemical-equation p {
  margin: 0;
  font-family: 'Times New Roman', serif;
}
</style>
```

**Footnotes with interactive references:**
```html
<article>
  <h2>Research Findings</h2>
  <p>The experimental data<sup><a href="#fn1" id="ref1">1</a></sup> 
  shows significant correlation between variables<sub><a href="#fn2" id="ref2">2,3</a></sub>.</p>
  
  <p>Further analysis<sub><a href="#fn4" id="ref4">4</a></sub> confirms 
  these observations across multiple trials.</p>
  
  <footer class="footnotes">
    <h3>References</h3>
    <p id="fn1"><sup>1</sup> Experimental Data Collection, 2023</p>
    <p id="fn2"><sub>2,3</sub> Correlation Studies, Smith & Johnson</p>
    <p id="fn4"><sub>4</sub> Multi-trial Analysis, Research Institute</p>
  </footer>
</article>

<style>
.footnotes {
  margin-top: 30px;
  padding-top: 15px;
  border-top: 1px solid #ddd;
  font-size: 0.9em;
}

.footnotes sub, .footnotes sup {
  font-size: 0.8em;
  margin-right: 5px;
}

a {
  color: #0d6efd;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
</style>
```

**Programming documentation with indices:**
```html
<div class="code-docs">
  <h3>Array Manipulation</h3>
  <p>To access elements in a 2D array, use double indices:</p>
  <pre><code>array[i][j]</code></pre>
  <p>Where <var>i</var><sub>row</sub> represents the row index and 
  <var>j</var><sub>col</sub> represents the column index.</p>
</div>

<style>
.code-docs {
  font-family: system-ui, sans-serif;
}

.code-docs sub {
  color: #6c757d;
  font-size: 0.75em;
  text-transform: lowercase;
}
</style>
```

**Physical constants and units:**
```html
<div class="physics-content">
  <h3>Physical Constants</h3>
  <ul>
    <li>Speed of light: c<sub>0</sub> = 299,792,458 m/s</li>
    <li>Planck's constant: h = 6.626 × 10<sup>-34</sup> J⋅s</li>
    <li>Gravitational constant: G = 6.674 × 10<sup>-11</sup> N⋅m<sup>2</sup>/kg<sup>2</sup></li>
    <li>Avogadro's number: N<sub>A</sub> = 6.022 × 10<sup>23</sup> mol<sup>-1</sup></li>
  </ul>
</div>

<style>
.physics-content {
  background-color: #f8f9fa;
  padding: 20px;
  border-radius: 8px;
}

.physics-content li {
  margin-bottom: 8px;
  font-family: 'Times New Roman', serif;
}
</style>
```

**Mathematical proofs with styled subscripts:**
```html
<div class="math-proof">
  <h4>Proof by Induction</h4>
  <p>Let P<sub class="statement">n</sub> be the statement: 
  1 + 2 + 3 + ... + n = n(n + 1)/2</p>
  
  <p><strong>Base case:</strong> P<sub class="case">1</sub> is true because 1 = 1(1 + 1)/2</p>
  
  <p><strong>Inductive step:</strong> Assume P<sub class="assumption">k</sub> is true. 
  Then for P<sub class="step">k+1</sub>:</p>
  
  <p>1 + 2 + ... + k + (k + 1) = k(k + 1)/2 + (k + 1) = (k + 1)(k + 2)/2</p>
</div>

<style>
.math-proof {
  border: 1px solid #e0e0e0;
  padding: 20px;
  border-radius: 4px;
  background-color: #fff;
}

.statement {
  color: #d63384;
  font-weight: bold;
}

.case {
  color: #0d6efd;
}

.assumption {
  color: #198754;
}

.step {
  color: #fd7e14;
}
</style>
```

**Chemical reactions with conditions:**
```html
<div class="reaction-container">
  <h3>Industrial Processes</h3>
  
  <div class="reaction">
    <p>Haber process for ammonia synthesis:</p>
    <p class="reaction-equation">
      N<sub>2</sub> + 3H<sub>2</sub> 
      <span class="reaction-arrow">⇌</span> 
      2NH<sub>3</sub>
    </p>
    <p class="reaction-conditions">
      Conditions: 400-500°C, 150-200 atm, Fe<sub>3</sub>O<sub>4</sub> catalyst
    </p>
  </div>
  
  <div class="reaction">
    <p>Contact process for sulfuric acid:</p>
    <p class="reaction-equation">
      2SO<sub>2</sub> + O<sub>2</sub> 
      <span class="reaction-arrow">→</span> 
      2SO<sub>3</sub>
    </p>
    <p class="reaction-conditions">
      Conditions: 400-450°C, V<sub>2</sub>O<sub>5</sub> catalyst
    </p>
  </div>
</div>

<style>
.reaction-container {
  max-width: 600px;
}

.reaction {
  margin-bottom: 30px;
  padding: 15px;
  border: 1px solid #e9ecef;
  border-radius: 6px;
  background-color: #f8f9fa;
}

.reaction-equation {
  text-align: center;
  font-size: 1.3em;
  margin: 15px 0;
  font-family: 'Times New Roman', serif;
}

.reaction-arrow {
  margin: 0 20px;
  color: #6c757d;
}

.reaction-conditions {
  font-size: 0.9em;
  color: #6c757d;
  text-align: center;
  margin: 10px 0 0 0;
}
</style>
```

**Accessibility-enhanced mathematical content:**
```html
<div class="accessible-math">
  <h3>Quadratic Formula</h3>
  <p>The solutions to the equation ax<sup>2</sup> + bx + c = 0 are given by:</p>
  
  <div class="equation" role="math" aria-label="x equals negative b plus or minus the square root of b squared minus 4 a c, all divided by 2 a">
    <p>
      x = <span class="fraction">
        <span class="numerator">-b ± √(b<sup>2</sup> - 4ac)</span>
        <span class="denominator">2a</span>
      </span>
    </p>
  </div>
  
  <p>Where the discriminant Δ = b<sub>2</sub> - 4ac determines the nature of the roots.</p>
</div>

<style>
.accessible-math {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  border: 1px solid #e0e0e0;
}

.equation {
  text-align: center;
  margin: 20px 0;
  font-size: 1.2em;
}

.fraction {
  display: inline-block;
  text-align: center;
  vertical-align: middle;
}

.numerator {
  display: block;
  padding: 0 10px;
  border-bottom: 1px solid #000;
}

.denominator {
  display: block;
  padding: 5px 10px 0 10px;
}
</style>
```

---

## Notes

* **Semantic importance**: 
  - Provides meaningful structure for technical and scientific content
  - Helps maintain proper reading flow and comprehension
  - Essential for accurate representation of mathematical and chemical notation
* **Typography considerations**:
  - Default font size reduction varies by browser (typically 75-80%)
  - Vertical alignment is handled by the browser's rendering engine
  - Line height is automatically adjusted to accommodate subscript text
* **Browser compatibility**: Universally supported across all browsers
* **Accessibility considerations**:
  - Screen readers typically process subscript text as normal text
  - For complex notation, consider providing additional context with `aria-label`
  - Ensure sufficient color contrast when applying custom styles
  - Test with screen readers for technical content comprehension
* **Common use cases**:
  - Chemical formulas and compound notation
  - Mathematical variables and indices
  - Footnote and reference markers
  - Scientific and technical documentation
  - Variable naming in programming contexts
* **Best practices**:
  - Use for semantic purposes, not purely for visual styling
  - Combine with `<sup>` when both subscript and superscript are needed
  - Provide accessible alternatives for complex notations
  - Maintain readability with appropriate font sizes
  - Use CSS for additional styling when needed
* **Common mistakes**:
  - Using for visual effects rather than semantic meaning
  - Overusing in non-technical content
  - Forgetting to close the tag properly
  - Applying excessive custom styling that reduces readability
* **CSS alternatives**: 
  - `vertical-align: sub` can create similar visual effect
  - `font-size` and `position` can mimic subscript behavior
  - However, these lack the semantic meaning of `<sub>`
* **Mobile considerations**:
  - Ensure subscript text remains readable on small screens
  - Test touch interactions with subscript links or interactive elements
  - Verify proper rendering across different mobile browsers

---
