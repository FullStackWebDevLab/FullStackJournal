# `<output>`

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

The `<output>` element represents the result of a calculation or user action, typically within a form context. It provides a semantic way to display computed values, calculation results, or other output generated from form inputs, making the relationship between input and output explicit for both users and assistive technologies.

---

## Syntax and Variants

+ **Standard syntax**: `<output>...</output>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain text and inline elements
+ **No self-closing variant**: Must contain content
+ **Dynamic content**: Typically populated via JavaScript calculations

---

## Attributes

+ **Core attributes**:
  - `for` (optional): Space-separated list of element IDs that contributed to the calculation
  - `name` (optional): Name for the output element (useful for form submission)
  - `form` (optional): Associates output with a form (by form ID)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **No deprecated attributes**: All original attributes remain supported

---

## Content Model

+ **Permitted content**: Phrasing content
+ **Allowed content**:
  - Text and character references
  - Phrasing elements: `<strong>`, `<em>`, `<span>`, etc.
  - Images and other inline elements
+ **Dynamic content**: Typically updated via JavaScript
+ **Initial state**: Can contain default text or be empty

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within `<form>` elements for calculated results
  - Near related input controls that affect the output
  - In calculators, converters, and interactive tools
  - As display areas for real-time computations
+ **Form association**: Can be inside or outside associated forms

---

## Behavior and Semantics

+ **Default display**: Inline element
+ **Default styling**:
  - `display: inline`
  - No inherent visual styling (appears as plain text)
  - Inherits font properties from parent
+ **Interactive behavior**:
  - Non-interactive (users cannot directly edit the content)
  - Content typically updates dynamically based on user input
  - Can be focused programmatically for accessibility
+ **Semantic meaning**:
  - Represents the result of a calculation or operation
  - Screen readers announce as "output" or similar
  - Provides explicit semantic meaning for computed values
+ **Accessibility**: Helps screen reader users understand that content is computed rather than static

---

## Examples

**Basic calculation output:**
```html
<form oninput="result.value = parseInt(a.value) + parseInt(b.value)">
  <input type="number" id="a" name="a" value="10"> +
  <input type="number" id="b" name="b" value="20"> =
  <output name="result" for="a b">30</output>
</form>
```

**Real-time price calculator:**
```html
<form class="price-calculator">
  <label for="quantity">Quantity:</label>
  <input type="number" id="quantity" name="quantity" value="1" min="1" max="100">
  
  <label for="price">Unit Price: $</label>
  <input type="number" id="price" name="price" value="25" min="0" step="0.01">
  
  <div class="result">
    Total: <output id="total" for="quantity price">$25.00</output>
  </div>
</form>

<script>
function calculateTotal() {
  const quantity = document.getElementById('quantity').value;
  const price = document.getElementById('price').value;
  const total = (quantity * price).toFixed(2);
  document.getElementById('total').textContent = `$${total}`;
}

document.getElementById('quantity').addEventListener('input', calculateTotal);
document.getElementById('price').addEventListener('input', calculateTotal);
</script>

<style>
.price-calculator {
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  max-width: 300px;
}

.result {
  margin-top: 15px;
  font-weight: bold;
  font-size: 1.2em;
}

output {
  color: #2ecc71;
  font-weight: bold;
}
</style>
```

**Tip calculator:**
```html
<form class="tip-calculator">
  <h3>Tip Calculator</h3>
  
  <div class="input-group">
    <label for="bill-amount">Bill Amount:</label>
    <input type="number" id="bill-amount" name="bill_amount" value="50" min="0" step="0.01">
  </div>
  
  <div class="input-group">
    <label for="tip-percent">Tip Percentage:</label>
    <input type="range" id="tip-percent" name="tip_percent" min="0" max="30" value="15">
    <span id="tip-percent-display">15%</span>
  </div>
  
  <div class="results">
    <div class="result-item">
      <span>Tip Amount:</span>
      <output id="tip-amount" for="bill-amount tip-percent">$7.50</output>
    </div>
    <div class="result-item">
      <span>Total Amount:</span>
      <output id="total-amount" for="bill-amount tip-percent">$57.50</output>
    </div>
  </div>
</form>

<script>
function calculateTip() {
  const billAmount = parseFloat(document.getElementById('bill-amount').value) || 0;
  const tipPercent = parseInt(document.getElementById('tip-percent').value);
  
  const tipAmount = billAmount * (tipPercent / 100);
  const totalAmount = billAmount + tipAmount;
  
  document.getElementById('tip-percent-display').textContent = `${tipPercent}%`;
  document.getElementById('tip-amount').textContent = `$${tipAmount.toFixed(2)}`;
  document.getElementById('total-amount').textContent = `$${totalAmount.toFixed(2)}`;
}

document.getElementById('bill-amount').addEventListener('input', calculateTip);
document.getElementById('tip-percent').addEventListener('input', calculateTip);

// Initial calculation
calculateTip();
</script>

<style>
.tip-calculator {
  max-width: 400px;
  padding: 20px;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  background: #f9f9f9;
}

.input-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: 600;
}

input[type="number"] {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

input[type="range"] {
  width: 70%;
  vertical-align: middle;
}

#tip-percent-display {
  display: inline-block;
  width: 25%;
  text-align: center;
  font-weight: bold;
}

.results {
  margin-top: 20px;
  padding: 15px;
  background: white;
  border-radius: 4px;
  border: 1px solid #ddd;
}

.result-item {
  display: flex;
  justify-content: space-between;
  margin-bottom: 8px;
  font-size: 1.1em;
}

.result-item:last-child {
  margin-bottom: 0;
  font-weight: bold;
  font-size: 1.2em;
  border-top: 1px solid #eee;
  padding-top: 8px;
}

output {
  font-weight: bold;
  color: #27ae60;
}
</style>
```

**Currency converter:**
```html
<form class="currency-converter">
  <h3>Currency Converter</h3>
  
  <div class="conversion-inputs">
    <div class="input-group">
      <label for="amount">Amount:</label>
      <input type="number" id="amount" name="amount" value="100" min="0" step="0.01">
    </div>
    
    <div class="input-group">
      <label for="from-currency">From:</label>
      <select id="from-currency" name="from_currency">
        <option value="USD">USD - US Dollar</option>
        <option value="EUR">EUR - Euro</option>
        <option value="GBP">GBP - British Pound</option>
        <option value="JPY">JPY - Japanese Yen</option>
      </select>
    </div>
    
    <div class="input-group">
      <label for="to-currency">To:</label>
      <select id="to-currency" name="to_currency">
        <option value="EUR">EUR - Euro</option>
        <option value="USD">USD - US Dollar</option>
        <option value="GBP">GBP - British Pound</option>
        <option value="JPY">JPY - Japanese Yen</option>
      </select>
    </div>
  </div>
  
  <div class="conversion-result">
    <output id="converted-amount" for="amount from-currency to-currency">85.00 EUR</output>
  </div>
</form>

<script>
// Mock exchange rates (in real app, fetch from API)
const exchangeRates = {
  USD: { EUR: 0.85, GBP: 0.73, JPY: 110.0, USD: 1 },
  EUR: { USD: 1.18, GBP: 0.86, JPY: 129.41, EUR: 1 },
  GBP: { USD: 1.37, EUR: 1.16, JPY: 150.68, GBP: 1 },
  JPY: { USD: 0.0091, EUR: 0.0077, GBP: 0.0066, JPY: 1 }
};

function convertCurrency() {
  const amount = parseFloat(document.getElementById('amount').value) || 0;
  const fromCurrency = document.getElementById('from-currency').value;
  const toCurrency = document.getElementById('to-currency').value;
  
  if (fromCurrency === toCurrency) {
    document.getElementById('converted-amount').textContent = `${amount.toFixed(2)} ${toCurrency}`;
    return;
  }
  
  const rate = exchangeRates[fromCurrency][toCurrency];
  const convertedAmount = amount * rate;
  
  document.getElementById('converted-amount').textContent = 
    `${convertedAmount.toFixed(2)} ${toCurrency}`;
}

document.getElementById('amount').addEventListener('input', convertCurrency);
document.getElementById('from-currency').addEventListener('change', convertCurrency);
document.getElementById('to-currency').addEventListener('change', convertCurrency);

// Initial conversion
convertCurrency();
</script>

<style>
.currency-converter {
  max-width: 400px;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: #f8f9fa;
}

.conversion-inputs {
  display: grid;
  gap: 15px;
  margin-bottom: 20px;
}

.input-group label {
  display: block;
  margin-bottom: 5px;
  font-weight: 600;
}

.input-group input,
.input-group select {
  width: 100%;
  padding: 8px 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}

.conversion-result {
  text-align: center;
  padding: 20px;
  background: white;
  border-radius: 6px;
  border: 2px solid #3498db;
}

.conversion-result output {
  font-size: 1.5em;
  font-weight: bold;
  color: #2c3e50;
}
</style>
```

**Accessible output with ARIA:**
```html
<form class="accessible-calculator" aria-labelledby="calculator-title">
  <h3 id="calculator-title">Accessible Calculator</h3>
  
  <div class="input-group">
    <label for="num1">First Number:</label>
    <input type="number" id="num1" name="num1" value="5" 
           aria-describedby="num1-desc">
    <span id="num1-desc" class="visually-hidden">Enter the first number for calculation</span>
  </div>
  
  <div class="input-group">
    <label for="num2">Second Number:</label>
    <input type="number" id="num2" name="num2" value="3"
           aria-describedby="num2-desc">
    <span id="num2-desc" class="visually-hidden">Enter the second number for calculation</span>
  </div>
  
  <div class="operation-group">
    <label>Operation:</label>
    <div role="group" aria-labelledby="operation-label">
      <span id="operation-label" class="visually-hidden">Choose mathematical operation</span>
      <label>
        <input type="radio" name="operation" value="add" checked>
        Addition
      </label>
      <label>
        <input type="radio" name="operation" value="subtract">
        Subtraction
      </label>
      <label>
        <input type="radio" name="operation" value="multiply">
        Multiplication
      </label>
      <label>
        <input type="radio" name="operation" value="divide">
        Division
      </label>
    </div>
  </div>
  
  <div class="result-group" aria-live="polite" aria-atomic="true">
    <span class="result-label">Result:</span>
    <output id="calc-result" 
            for="num1 num2" 
            role="status"
            aria-label="Calculation result">
      8
    </output>
  </div>
</form>

<script>
function calculate() {
  const num1 = parseFloat(document.getElementById('num1').value) || 0;
  const num2 = parseFloat(document.getElementById('num2').value) || 0;
  const operation = document.querySelector('input[name="operation"]:checked').value;
  
  let result;
  switch (operation) {
    case 'add':
      result = num1 + num2;
      break;
    case 'subtract':
      result = num1 - num2;
      break;
    case 'multiply':
      result = num1 * num2;
      break;
    case 'divide':
      result = num2 !== 0 ? num1 / num2 : 'Cannot divide by zero';
      break;
  }
  
  document.getElementById('calc-result').textContent = result;
}

// Add event listeners to all inputs
document.querySelectorAll('#num1, #num2, input[name="operation"]').forEach(input => {
  input.addEventListener('input', calculate);
  input.addEventListener('change', calculate);
});

// Initial calculation
calculate();
</script>

<style>
.accessible-calculator {
  max-width: 400px;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
}

.operation-group {
  margin: 15px 0;
}

.operation-group label:first-child {
  display: block;
  margin-bottom: 8px;
  font-weight: 600;
}

.operation-group [role="group"] {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.result-group {
  margin-top: 20px;
  padding: 15px;
  background: #e8f5e8;
  border-radius: 4px;
  border: 1px solid #4caf50;
}

.result-label {
  font-weight: 600;
  margin-right: 10px;
}

#calc-result {
  font-weight: bold;
  font-size: 1.2em;
  color: #2e7d32;
}

.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
</style>
```

**BMI Calculator:**
```html
<form class="bmi-calculator">
  <h3>BMI Calculator</h3>
  
  <div class="input-section">
    <div class="input-group">
      <label for="height">Height (cm):</label>
      <input type="number" id="height" name="height" value="170" min="100" max="250">
    </div>
    
    <div class="input-group">
      <label for="weight">Weight (kg):</label>
      <input type="number" id="weight" name="weight" value="70" min="30" max="200">
    </div>
  </div>
  
  <div class="results-section">
    <div class="bmi-result">
      <span>Your BMI:</span>
      <output id="bmi-value" for="height weight">24.22</output>
    </div>
    
    <div class="bmi-category">
      <span>Category:</span>
      <output id="bmi-category" for="height weight">Normal weight</output>
    </div>
  </div>
  
  <div class="bmi-chart">
    <div class="chart-bar">
      <div class="chart-segment underweight" data-range="Underweight (<18.5)"></div>
      <div class="chart-segment normal" data-range="Normal (18.5-24.9)"></div>
      <div class="chart-segment overweight" data-range="Overweight (25-29.9)"></div>
      <div class="chart-segment obese" data-range="Obese (≥30)"></div>
    </div>
    <div class="chart-marker" id="bmi-marker"></div>
  </div>
</form>

<script>
function calculateBMI() {
  const height = parseFloat(document.getElementById('height').value) / 100; // Convert to meters
  const weight = parseFloat(document.getElementById('weight').value);
  
  if (height > 0 && weight > 0) {
    const bmi = weight / (height * height);
    const bmiRounded = bmi.toFixed(2);
    
    document.getElementById('bmi-value').textContent = bmiRounded;
    
    // Determine category
    let category;
    if (bmi < 18.5) category = "Underweight";
    else if (bmi < 25) category = "Normal weight";
    else if (bmi < 30) category = "Overweight";
    else category = "Obese";
    
    document.getElementById('bmi-category').textContent = category;
    
    // Update marker position (0-100% scale for BMI 15-40)
    const markerPosition = Math.max(0, Math.min(100, ((bmi - 15) / 25) * 100));
    document.getElementById('bmi-marker').style.left = `${markerPosition}%`;
  }
}

document.getElementById('height').addEventListener('input', calculateBMI);
document.getElementById('weight').addEventListener('input', calculateBMI);

// Initial calculation
calculateBMI();
</script>

<style>
.bmi-calculator {
  max-width: 400px;
  padding: 20px;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  background: #fafafa;
}

.input-section {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15px;
  margin-bottom: 20px;
}

.input-group label {
  display: block;
  margin-bottom: 5px;
  font-weight: 600;
}

.input-group input {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.results-section {
  margin-bottom: 20px;
}

.bmi-result, .bmi-category {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  padding: 10px;
  background: white;
  border-radius: 4px;
}

.bmi-result {
  font-size: 1.2em;
  font-weight: bold;
  color: #2c3e50;
}

#bmi-value {
  color: #27ae60;
  font-weight: bold;
}

#bmi-category {
  color: #3498db;
  font-weight: 600;
}

.bmi-chart {
  position: relative;
  height: 40px;
  margin-top: 10px;
}

.chart-bar {
  display: flex;
  height: 20px;
  border-radius: 10px;
  overflow: hidden;
}

.chart-segment {
  flex: 1;
  position: relative;
}

.chart-segment::after {
  content: attr(data-range);
  position: absolute;
  top: 25px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 0.7em;
  color: #666;
  white-space: nowrap;
}

.underweight { background: #3498db; }
.normal { background: #27ae60; }
.overweight { background: #f39c12; }
.obese { background: #e74c3c; }

.chart-marker {
  position: absolute;
  top: -5px;
  width: 10px;
  height: 30px;
  background: #2c3e50;
  border-radius: 5px;
  transform: translateX(-50%);
  transition: left 0.3s ease;
}
</style>
```

**Character counter with output:**
```html
<form class="character-counter">
  <label for="message">Your Message:</label>
  <textarea id="message" name="message" 
            maxlength="200"
            placeholder="Type your message here..."></textarea>
  
  <div class="counter-display">
    <output id="char-count" for="message">0</output>
    <span>/ 200 characters</span>
  </div>
</form>

<script>
document.getElementById('message').addEventListener('input', function() {
  const count = this.value.length;
  const maxLength = this.maxLength;
  const counter = document.getElementById('char-count');
  
  counter.textContent = count;
  
  // Visual feedback
  if (count > maxLength * 0.9) {
    counter.style.color = '#e74c3c';
  } else if (count > maxLength * 0.75) {
    counter.style.color = '#f39c12';
  } else {
    counter.style.color = '#27ae60';
  }
});
</script>

<style>
.character-counter {
  max-width: 500px;
}

label {
  display: block;
  margin-bottom: 8px;
  font-weight: 600;
}

textarea {
  width: 100%;
  height: 120px;
  padding: 12px;
  border: 2px solid #ddd;
  border-radius: 6px;
  font-family: inherit;
  font-size: 16px;
  resize: vertical;
}

.counter-display {
  margin-top: 8px;
  text-align: right;
  font-size: 0.9em;
  color: #666;
}

#char-count {
  font-weight: bold;
  font-size: 1.1em;
}
</style>
```

---

## Notes

* **Semantic importance**: Provides explicit meaning for calculated or dynamic content
* **Accessibility benefits**:
  - Screen readers announce output elements appropriately
  - `for` attribute helps establish relationships with source inputs
  - `aria-live` can be added for dynamic updates
* **Browser support**: Well-supported in all modern browsers
* **Common mistakes**:
  - Using `<span>` or `<div>` instead of `<output>` for calculated results
  - Forgetting to update output content dynamically
  - Not using the `for` attribute to associate with source elements
  - Using output for static content instead of computed results
* **Form submission**: 
  - Output values can be included in form data if they have a `name` attribute
  - Useful for submitting calculated results along with user inputs
* **Styling flexibility**: Can be styled like any other inline element
* **Dynamic updates**: 
  - Typically updated via JavaScript in response to input changes
  - Can use `innerHTML` or `textContent` for updates
  - Consider accessibility when updating (use `aria-live` if important)
* **Best practices**:
  - Use for genuinely computed or derived values
  - Associate with source inputs using `for` attribute
  - Provide clear context for what the output represents
  - Ensure timely updates when source values change
  - Test with screen readers for proper announcement

---
