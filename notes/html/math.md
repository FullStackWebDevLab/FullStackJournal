# `<math>`

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

The `<math>` element is the root container for Mathematical Markup Language (MathML) content, which is used to describe mathematical notation and capture both its structure and content. It enables the display of complex mathematical expressions directly in web pages without relying on images or external plugins, providing accessible, scalable, and semantically meaningful mathematical content.

---

## Syntax and Variants

+ **Standard syntax**: `<math>...</math>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Contains MathML elements and content
+ **Namespace**: Typically used with MathML namespace `xmlns="http://www.w3.org/1998/Math/MathML"`
+ **Display modes**: Can be inline or block-level based on `display` attribute

---

## Attributes

+ **Core attributes**:
  - `display` (optional): Specifies rendering mode - `inline` (default) or `block`
  - `xmlns` (recommended): Namespace declaration for MathML
  - `class`, `style`, `id`: For styling and scripting

+ **Global attributes**: `dir`, `href`, `mathbackground`, `mathcolor`, etc.

+ **Presentation attributes**: `displaystyle`, `scriptlevel`, `mathvariant`

---

## Content Model

+ **Permitted content**: MathML elements only
+ **Primary categories**:
  - **Presentation MathML**: Layout and rendering elements (`<mrow>`, `<msup>`, `<mfrac>`, etc.)
  - **Content MathML**: Semantic meaning elements (`<apply>`, `<ci>`, `<cn>`, etc.)
+ **Common child elements**:
  - Structure: `<mrow>`, `<mfrac>`, `<msqrt>`, `<mroot>`
  - Scripts: `<msup>`, `<msub>`, `<msubsup>`
  - Tokens: `<mi>`, `<mn>`, `<mo>`
  - Tables: `<mtable>`, `<mtr>`, `<mtd>`

---

## Context

+ **Valid parents**: Any element that accepts flow content or phrasing content
+ **Common locations**:
  - Within paragraphs for inline mathematics
  - As standalone blocks for complex equations
  - In scientific and educational content
  - Technical documentation and research papers
+ **Namespace requirement**: Should include MathML namespace for proper rendering
+ **Browser support**: Varies significantly across browsers and may require polyfills

---

## Behavior and Semantics

+ **Default display**: Inline element (when `display="inline"`)
+ **Default styling**:
  - Renders mathematical notation using system fonts
  - Automatic spacing and layout based on mathematical rules
  - Scalable rendering that maintains quality at different sizes
+ **Semantic meaning**:
  - Represents mathematical notation with proper structure
  - Provides accessibility through semantic MathML
  - Enables machine-readable mathematical content
+ **Accessibility**:
  - Screen readers can interpret MathML with proper support
  - Provides semantic structure for assistive technologies
  - Can be converted to speech or braille representations

---

## Examples

**Basic inline equation:**
```html
<p>The Pythagorean theorem states that 
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <msup><mi>a</mi><mn>2</mn></msup>
  <mo>+</mo>
  <msup><mi>b</mi><mn>2</mn></msup>
  <mo>=</mo>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
where c is the hypotenuse.</p>
```

**Fraction display:**
```html
<p>The quadratic formula:
<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline">
  <mi>x</mi>
  <mo>=</mo>
  <mfrac>
    <mrow>
      <mo>-</mo>
      <mi>b</mi>
      <mo>±</mo>
      <msqrt>
        <msup><mi>b</mi><mn>2</mn></msup>
        <mo>-</mo>
        <mn>4</mn>
        <mi>a</mi>
        <mi>c</mi>
      </msqrt>
    </mrow>
    <mrow>
      <mn>2</mn>
      <mi>a</mi>
    </mrow>
  </mfrac>
</math>
</p>
```

**Block-level equation:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mi>E</mi>
    <mo>=</mo>
    <mi>m</mi>
    <msup>
      <mi>c</mi>
      <mn>2</mn>
    </msup>
  </mrow>
</math>
```

**Square root and exponents:**
```html
<p>Solve for x:
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <msqrt>
    <mrow>
      <msup><mi>x</mi><mn>2</mn></msup>
      <mo>+</mo>
      <mn>4</mn>
    </mrow>
  </msqrt>
  <mo>=</mo>
  <mn>5</mn>
</math>
</p>
```

**Styled math elements:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" 
      class="styled-math" 
      style="color: blue; font-size: 1.2em;">
  <mrow>
    <mi>f</mi>
    <mo>(</mo>
    <mi>x</mi>
    <mo>)</mo>
    <mo>=</mo>
    <msup>
      <mi>x</mi>
      <mn>2</mn>
    </msup>
  </mrow>
</math>

<style>
.styled-math {
  background-color: #f0f8ff;
  padding: 5px;
  border-radius: 4px;
}
</style>
```

**Summation notation:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <munderover>
      <mo>∑</mo>
      <mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow>
      <mi>n</mi>
    </munderover>
    <msup><mi>i</mi><mn>2</mn></msup>
    <mo>=</mo>
    <mfrac>
      <mrow><mi>n</mi><mo>(</mo><mi>n</mi><mo>+</mo><mn>1</mn><mo>)</mo><mo>(</mo><mn>2</mn><mi>n</mi><mo>+</mo><mn>1</mn><mo>)</mo></mrow>
      <mn>6</mn>
    </mfrac>
  </mrow>
</math>
```

**Integral with limits:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <msubsup>
      <mo>∫</mo>
      <mn>0</mn>
      <mi>∞</mi>
    </msubsup>
    <msup>
      <mi>e</mi>
      <mrow><mo>-</mo><mi>x</mi></mrow>
    </msup>
    <mi>d</mi>
    <mi>x</mi>
    <mo>=</mo>
    <mn>1</mn>
  </mrow>
</math>
```

**Matrix representation:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mi>A</mi>
    <mo>=</mo>
    <mfenced open="[" close="]">
      <mtable>
        <mtr>
          <mtd><mn>1</mn></mtd>
          <mtd><mn>2</mn></mtd>
        </mtr>
        <mtr>
          <mtd><mn>3</mn></mtd>
          <mtd><mn>4</mn></mtd>
        </mtr>
      </mtable>
    </mfenced>
  </mrow>
</math>
```

**Chemical equation:**
```html
<p>Chemical reaction:
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mrow>
    <mn>2</mn>
    <msub><mi>H</mi><mn>2</mn></msub>
    <mo>+</mo>
    <msub><mi>O</mi><mn>2</mn></msub>
    <mo>→</mo>
    <mn>2</mn>
    <msub><mi>H</mi><mn>2</mn></msub>
    <mi>O</mi>
  </mrow>
</math>
</p>
```

**Accessible math with ARIA labels:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" 
      role="math"
      aria-label="E equals m c squared">
  <mrow>
    <mi>E</mi>
    <mo>=</mo>
    <mi>m</mi>
    <msup>
      <mi>c</mi>
      <mn>2</mn>
    </msup>
  </mrow>
</math>
```

**Complex fraction with nested elements:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mfrac>
    <mrow>
      <mn>1</mn>
      <mo>+</mo>
      <mfrac>
        <mn>1</mn>
        <mrow>
          <mn>1</mn>
          <mo>+</mo>
          <mfrac>
            <mn>1</mn>
            <mi>x</mi>
          </mfrac>
        </mrow>
      </mfrac>
    </mrow>
    <mn>2</mn>
  </mfrac>
</math>
```

**Inequality expressions:**
```html
<p>Solution range:
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mrow>
    <mo>-</mo>
    <mn>5</mn>
    <mo>≤</mo>
    <mi>x</mi>
    <mo><</mo>
    <mn>3</mn>
  </mrow>
</math>
</p>
```

**Greek letters and symbols:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mi>π</mi>
    <mo>≈</mo>
    <mn>3.14159</mn>
  </mrow>
</math>

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mi>θ</mi>
    <mo>=</mo>
    <mfrac>
      <mi>π</mi>
      <mn>4</mn>
    </mfrac>
  </mrow>
</math>
```

**Binomial coefficient:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mo>(</mo>
    <mfrac linethickness="0">
      <mi>n</mi>
      <mi>k</mi>
    </mfrac>
    <mo>)</mo>
    <mo>=</mo>
    <mfrac>
      <mrow><mi>n</mi><mo>!</mo></mrow>
      <mrow><mi>k</mi><mo>!</mo><mo>(</mo><mi>n</mi><mo>-</mo><mi>k</mi><mo>)</mo><mo>!</mo></mrow>
    </mfrac>
  </mrow>
</math>
```

**Limit expression:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <munder>
      <mi>lim</mi>
      <mrow><mi>x</mi><mo>→</mo><mn>0</mn></mrow>
    </munder>
    <mfrac>
      <mrow><mi>sin</mi><mi>x</mi></mrow>
      <mi>x</mi>
    </mfrac>
    <mo>=</mo>
    <mn>1</mn>
  </mrow>
</math>
```

**Physics equations:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mi>F</mi>
    <mo>=</mo>
    <mi>m</mi>
    <mi>a</mi>
  </mrow>
</math>

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mi>V</mi>
    <mo>=</mo>
    <mi>I</mi>
    <mi>R</mi>
  </mrow>
</math>
```

**Statistical formulas:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mi>σ</mi>
    <mo>=</mo>
    <msqrt>
      <mfrac>
        <mrow>
          <munderover>
            <mo>∑</mo>
            <mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow>
            <mi>n</mi>
          </munderover>
          <msup>
            <mrow><mo>(</mo><msub><mi>x</mi><mi>i</mi></msub><mo>-</mo><mi>μ</mi><mo>)</mo></mrow>
            <mn>2</mn>
          </msup>
        </mrow>
        <mi>n</mi>
      </mfrac>
    </msqrt>
  </mrow>
</math>
```

**Math with text annotations:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mi>P</mi>
    <mo>(</mo>
    <mi>A</mi>
    <mo>|</mo>
    <mi>B</mi>
    <mo>)</mo>
    <mo>=</mo>
    <mfrac>
      <mrow>
        <mi>P</mi>
        <mo>(</mo>
        <mi>A</mi>
        <mo>∩</mo>
        <mi>B</mi>
        <mo>)</mo>
      </mrow>
      <mrow>
        <mi>P</mi>
        <mo>(</mo>
        <mi>B</mi>
        <mo>)</mo>
      </mrow>
    </mfrac>
  </mrow>
</math>
<mtext> (conditional probability)</mtext>
```

**Complex number operations:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mi>z</mi>
    <mo>=</mo>
    <mi>a</mi>
    <mo>+</mo>
    <mi>b</mi>
    <mi>i</mi>
  </mrow>
</math>

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mo>|</mo>
    <mi>z</mi>
    <mo>|</mo>
    <mo>=</mo>
    <msqrt>
      <mrow>
        <msup><mi>a</mi><mn>2</mn></msup>
        <mo>+</mo>
        <msup><mi>b</mi><mn>2</mn></msup>
      </mrow>
    </msqrt>
  </mrow>
</math>
```

**Differential equations:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mfrac>
      <mrow><mi>d</mi><mi>y</mi></mrow>
      <mrow><mi>d</mi><mi>x</mi></mrow>
    </mfrac>
    <mo>=</mo>
    <mi>k</mi>
    <mi>y</mi>
  </mrow>
</math>
```

**Set notation:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mrow>
    <mi>A</mi>
    <mo>=</mo>
    <mo>{</mo>
    <mi>x</mi>
    <mo>∈</mo>
    <mi>ℝ</mi>
    <mo>|</mo>
    <mi>x</mi>
    <mo>></mo>
    <mn>0</mn>
    <mo>}</mo>
  </mrow>
</math>
```

**Math with responsive sizing:**
```html
<div class="responsive-math">
  <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
    <mrow>
      <munderover>
        <mo>∑</mo>
        <mrow><mi>n</mi><mo>=</mo><mn>1</mn></mrow>
        <mi>∞</mi>
      </munderover>
      <mfrac>
        <mn>1</mn>
        <msup><mi>n</mi><mn>2</mn></msup>
      </mfrac>
      <mo>=</mo>
      <mfrac>
        <msup><mi>π</mi><mn>2</mn></msup>
        <mn>6</mn>
      </mfrac>
    </mrow>
  </math>
</div>

<style>
.responsive-math {
  max-width: 100%;
  overflow-x: auto;
}

.responsive-math math {
  font-size: clamp(1rem, 2vw, 1.5rem);
}
</style>
```

**Interactive math with JavaScript:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML" id="interactive-math">
  <mrow>
    <mi>f</mi>
    <mo>(</mo>
    <mi>x</mi>
    <mo>)</mo>
    <mo>=</mo>
    <msup><mi>x</mi><mn>2</mn></msup>
  </mrow>
</math>

<button onclick="changeExponent()">Change to x³</button>

<script>
function changeExponent() {
  const mathElement = document.getElementById('interactive-math');
  mathElement.innerHTML = `
    <mrow>
      <mi>f</mi>
      <mo>(</mo>
      <mi>x</mi>
      <mo>)</mo>
      <mo>=</mo>
      <msup><mi>x</mi><mn>3</mn></msup>
    </mrow>
  `;
}
</script>
```

**Math with error handling for unsupported browsers:**
```html
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mrow>
    <mi>E</mi>
    <mo>=</mo>
    <mi>m</mi>
    <msup>
      <mi>c</mi>
      <mn>2</mn>
    </msup>
  </mrow>
</math>
<noscript>
  <p><i>E = mc²</i> (Energy equals mass times the speed of light squared)</p>
</noscript>

<script>
// Check for MathML support
if (!document.createElement('math').getAttribute('display')) {
  document.write('<p><i>E = mc²</i> (Fallback rendering)</p>');
}
</script>
```

---

## Notes

* **Browser compatibility**: 
  - Native support in Firefox
  - Safari has basic support
  - Chrome/Edge require polyfills or extensions
  - Always provide fallbacks for unsupported browsers
* **Polyfills and alternatives**:
  - MathJax: JavaScript library for cross-browser math rendering
  - KaTeX: Fast math typesetting library
  - Web fonts with mathematical symbols
* **Accessibility considerations**:
  - Use `role="math"` and `aria-label` for complex expressions
  - Provide text alternatives for screen readers
  - Consider using MathML with Content MathML for better semantics
  - Test with screen readers and accessibility tools
* **Performance implications**:
  - Complex MathML can impact rendering performance
  - Consider server-side rendering for heavy mathematical content
  - Use appropriate display modes to optimize layout
* **Common mistakes**:
  - Forgetting the MathML namespace declaration
  - Using HTML entities instead of MathML elements
  - Not providing fallbacks for unsupported browsers
  - Creating overly complex nested structures
* **Best practices**:
  - Always include the MathML namespace
  - Use `display="block"` for complex equations
  - Provide text alternatives for accessibility
  - Test across different browsers and devices
  - Consider using established libraries for better compatibility
* **SEO benefits**:
  - Mathematical content can be indexed and understood by search engines
  - Provides semantic structure for technical content
  - Enhances content quality for educational and scientific websites
* **Mobile considerations**:
  - Ensure equations are readable on small screens
  - Use responsive sizing and scrolling for complex expressions
  - Test touch interactions with interactive math content

---
