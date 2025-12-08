# `<progress>`

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

The `<progress>` element represents the completion progress of a task, typically displayed as a progress bar. It provides a semantic way to indicate the current status of ongoing operations such as file uploads, form completion, installation processes, or any task that has a defined beginning and end. The element offers both visual feedback to users and programmatic accessibility for assistive technologies.

---

## Syntax and Variants

+ **Standard syntax**: `<progress>...</progress>`
+ **Not void**: Requires both opening and closing tags
+ **Inline element**: Flows with surrounding content
+ **No self-closing variant**: Must have proper opening and closing tags
+ **Content fallback**: Text content inside acts as fallback for unsupported browsers

---

## Attributes

+ **Core attributes**:
  - `value` (optional): Current progress value (number between 0 and max, or 0 and 1 if max is omitted)
  - `max` (optional): Maximum value (number greater than 0, defaults to 1)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Common usage**: 
  - `id` for JavaScript manipulation
  - `class` for styling
  - `data-*` for additional progress metadata

---

## Content Model

+ **Permitted content**: Phrasing content, but typically empty or contains fallback text
+ **Allowed content**:
  - Text content (acts as fallback for unsupported browsers)
  - No other elements should be placed inside
+ **Common practice**: Usually left empty, with text content only as accessibility fallback
+ **Restrictions**: Should not contain interactive elements

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within forms for completion indicators
  - In file upload interfaces
  - Installation wizards and setup processes
  - Loading screens and status indicators
  - Game progress trackers
+ **No usage limits**: Multiple progress elements can be used within a document
+ **Relationship**: Often used with JavaScript for dynamic updates

---

## Behavior and Semantics

+ **Default display**: Inline-block element
+ **Default styling**:
  - `display: inline-block`
  - Browser-specific appearance (varies by OS and browser)
  - Typically shows a horizontal bar with fill animation
  - Includes accessible name and current value
+ **Interactive behavior**:
  - Read-only by default (not user-interactive)
  - Updates programmatically via JavaScript
  - Can be animated through CSS transitions
+ **Semantic meaning**:
  - Represents completion progress of a task
  - Provides machine-readable progress information
  - Supports accessibility through ARIA attributes
+ **Accessibility**:
  - Screen readers announce current progress and maximum value
  - Automatic ARIA role="progressbar" assignment
  - Supports aria-label and aria-describedby for additional context

---

## Examples

**Basic indeterminate progress:**
```html
<p>Processing your request... <progress></progress></p>
```

**Determinate progress with values:**
```html
<p>Download progress: 
<progress value="70" max="100">70%</progress>
</p>
```

**Styled progress element:**
```html
<progress value="45" max="100" class="custom-progress">45%</progress>

<style>
.custom-progress {
  width: 300px;
  height: 20px;
  border-radius: 10px;
  overflow: hidden;
}

/* WebKit browsers */
.custom-progress::-webkit-progress-bar {
  background-color: #f0f0f0;
  border-radius: 10px;
}

.custom-progress::-webkit-progress-value {
  background-color: #4CAF50;
  border-radius: 10px;
  transition: width 0.3s ease;
}

/* Firefox */
.custom-progress::-moz-progress-bar {
  background-color: #4CAF50;
  border-radius: 10px;
}
</style>
```

**File upload progress:**
```html
<div class="upload-container">
  <label for="file-upload">Upload file:</label>
  <input type="file" id="file-upload" onchange="startUpload(this)">
  <progress id="upload-progress" value="0" max="100" style="display: none;">
    0%
  </progress>
  <span id="upload-status"></span>
</div>

<script>
function startUpload(input) {
  const progress = document.getElementById('upload-progress');
  const status = document.getElementById('upload-status');
  
  progress.style.display = 'inline-block';
  status.textContent = 'Uploading...';
  
  // Simulate upload progress
  let value = 0;
  const interval = setInterval(() => {
    value += 10;
    progress.value = value;
    progress.textContent = value + '%';
    
    if (value >= 100) {
      clearInterval(interval);
      status.textContent = 'Upload complete!';
    }
  }, 500);
}
</script>

<style>
.upload-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 400px;
}

#upload-progress {
  width: 100%;
  height: 25px;
}
</style>
```

**Form completion progress:**
```html
<div class="form-progress">
  <h3>Application Progress</h3>
  <progress id="form-progress" value="2" max="5">Step 2 of 5</progress>
  <div class="progress-text">
    <span id="progress-percent">40%</span>
    <span id="progress-steps">Step 2 of 5</span>
  </div>
</div>

<style>
.form-progress {
  background: #f8f9fa;
  padding: 20px;
  border-radius: 8px;
  margin: 20px 0;
}

#form-progress {
  width: 100%;
  height: 12px;
  margin-bottom: 10px;
}

.progress-text {
  display: flex;
  justify-content: space-between;
  font-size: 0.9em;
  color: #666;
}
</style>
```

**Multiple progress bars:**
```html
<div class="multi-progress">
  <h4>System Resources</h4>
  
  <div class="progress-item">
    <label>CPU Usage:</label>
    <progress value="75" max="100" class="cpu-progress">75%</progress>
    <span>75%</span>
  </div>
  
  <div class="progress-item">
    <label>Memory:</label>
    <progress value="60" max="100" class="memory-progress">60%</progress>
    <span>60%</span>
  </div>
  
  <div class="progress-item">
    <label>Storage:</label>
    <progress value="85" max="100" class="storage-progress">85%</progress>
    <span>85%</span>
  </div>
</div>

<style>
.multi-progress {
  max-width: 400px;
}

.progress-item {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 15px;
}

.progress-item label {
  width: 80px;
  font-weight: 500;
}

.progress-item progress {
  flex: 1;
  height: 8px;
}

.progress-item span {
  width: 40px;
  text-align: right;
  font-size: 0.9em;
  color: #666;
}

.cpu-progress::-webkit-progress-value { background-color: #ff6b6b; }
.memory-progress::-webkit-progress-value { background-color: #4ecdc4; }
.storage-progress::-webkit-progress-value { background-color: #45b7d1; }

.cpu-progress::-moz-progress-bar { background-color: #ff6b6b; }
.memory-progress::-moz-progress-bar { background-color: #4ecdc4; }
.storage-progress::-moz-progress-bar { background-color: #45b7d1; }
</style>
```

**Animated progress with CSS:**
```html
<progress id="animated-progress" value="0" max="100"></progress>
<button onclick="startAnimation()">Start Progress</button>

<style>
#animated-progress {
  width: 300px;
  height: 20px;
}

#animated-progress::-webkit-progress-value {
  background: linear-gradient(45deg, #667eea, #764ba2);
  border-radius: 10px;
  transition: width 0.5s ease-in-out;
}

#animated-progress::-moz-progress-bar {
  background: linear-gradient(45deg, #667eea, #764ba2);
  border-radius: 10px;
  transition: width 0.5s ease-in-out;
}
</style>

<script>
function startAnimation() {
  const progress = document.getElementById('animated-progress');
  let value = 0;
  
  const interval = setInterval(() => {
    value += 1;
    progress.value = value;
    
    if (value >= 100) {
      clearInterval(interval);
    }
  }, 50);
}
</script>
```

**Accessible progress with ARIA:**
```html
<div class="accessible-progress">
  <div class="progress-info">
    <span id="progress-label">Processing your order</span>
    <span id="progress-value">0%</span>
  </div>
  <progress 
    id="aria-progress" 
    value="0" 
    max="100"
    aria-labelledby="progress-label"
    aria-describedby="progress-desc">
    0%
  </progress>
  <div id="progress-desc" class="sr-only">
    Progress updates every second until completion
  </div>
</div>

<script>
// Simulate progress updates
const progress = document.getElementById('aria-progress');
const valueDisplay = document.getElementById('progress-value');

let currentValue = 0;
const interval = setInterval(() => {
  currentValue += 10;
  progress.value = currentValue;
  valueDisplay.textContent = currentValue + '%';
  progress.textContent = currentValue + '%';
  
  if (currentValue >= 100) {
    clearInterval(interval);
    valueDisplay.textContent = 'Complete!';
  }
}, 1000);
</script>

<style>
.accessible-progress {
  max-width: 400px;
  margin: 20px 0;
}

.progress-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
  font-size: 0.9em;
}

#aria-progress {
  width: 100%;
  height: 15px;
}

.sr-only {
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

**Quiz or survey progress:**
```html
<div class="quiz-progress">
  <div class="progress-header">
    <h4>Survey Progress</h4>
    <span id="question-count">Question 3 of 10</span>
  </div>
  <progress id="quiz-progress" value="3" max="10">30%</progress>
  <div class="progress-labels">
    <span>Start</span>
    <span>Complete</span>
  </div>
</div>

<style>
.quiz-progress {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  margin: 20px 0;
}

.progress-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.progress-header h4 {
  margin: 0;
  color: #333;
}

#question-count {
  color: #666;
  font-size: 0.9em;
}

#quiz-progress {
  width: 100%;
  height: 12px;
  margin-bottom: 5px;
}

.progress-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.8em;
  color: #999;
}
</style>
```

**Bootstrap-style progress:**
```html
<div class="bootstrap-progress">
  <div class="progress">
    <progress 
      id="bootstrap-progress" 
      value="65" 
      max="100"
      class="progress-bar"
      role="progressbar"
      aria-valuenow="65" 
      aria-valuemin="0" 
      aria-valuemax="100">
      65%
    </progress>
  </div>
  <div class="progress-label">65% Complete</div>
</div>

<style>
.bootstrap-progress {
  max-width: 500px;
  margin: 20px 0;
}

.progress {
  height: 20px;
  background-color: #e9ecef;
  border-radius: 4px;
  overflow: hidden;
}

.progress-bar {
  width: 100%;
  height: 100%;
  border: none;
}

.progress-bar::-webkit-progress-bar {
  background-color: transparent;
}

.progress-bar::-webkit-progress-value {
  background-color: #007bff;
  transition: width 0.6s ease;
}

.progress-bar::-moz-progress-bar {
  background-color: #007bff;
}

.progress-label {
  text-align: center;
  margin-top: 5px;
  font-size: 0.9em;
  color: #666;
}
</style>
```

**Gradient progress bar:**
```html
<progress id="gradient-progress" value="75" max="100">75%</progress>

<style>
#gradient-progress {
  width: 400px;
  height: 25px;
  border: none;
  border-radius: 12px;
  overflow: hidden;
}

#gradient-progress::-webkit-progress-bar {
  background: #f0f0f0;
  border-radius: 12px;
}

#gradient-progress::-webkit-progress-value {
  background: linear-gradient(90deg, #ff6b6b, #ee5a24);
  border-radius: 12px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.2);
}

#gradient-progress::-moz-progress-bar {
  background: linear-gradient(90deg, #ff6b6b, #ee5a24);
  border-radius: 12px;
}
</style>
```

**Step-based progress:**
```html
<div class="step-progress">
  <div class="steps">
    <div class="step active">1</div>
    <div class="step active">2</div>
    <div class="step">3</div>
    <div class="step">4</div>
    <div class="step">5</div>
  </div>
  <progress value="2" max="5" aria-label="Step 2 of 5"></progress>
</div>

<style>
.step-progress {
  max-width: 400px;
  margin: 30px 0;
}

.steps {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  position: relative;
}

.step {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background: #e9ecef;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  z-index: 2;
}

.step.active {
  background: #007bff;
  color: white;
}

.step-progress progress {
  width: 100%;
  height: 6px;
  position: relative;
  top: -18px;
  z-index: 1;
}
</style>
```

**Progress with estimated time:**
```html
<div class="timed-progress">
  <div class="progress-header">
    <span>Installing updates...</span>
    <span id="time-remaining">About 2 minutes remaining</span>
  </div>
  <progress id="timed-progress" value="25" max="100"></progress>
  <div class="progress-details">
    <span>25%</span>
    <span>Step 4 of 8: Installing components</span>
  </div>
</div>

<style>
.timed-progress {
  background: #f8f9fa;
  padding: 20px;
  border-radius: 8px;
  border: 1px solid #e9ecef;
}

.progress-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  font-weight: 500;
}

#time-remaining {
  color: #666;
  font-size: 0.9em;
}

#timed-progress {
  width: 100%;
  height: 15px;
  margin-bottom: 10px;
}

.progress-details {
  display: flex;
  justify-content: space-between;
  font-size: 0.8em;
  color: #666;
}
</style>
```

**Circular progress indicator (using CSS with HTML progress):**
```html
<div class="circular-progress-container">
  <progress id="circular-progress" value="75" max="100" class="circular">75%</progress>
  <div class="circular-label">
    <span id="circular-value">75%</span>
    <span>Complete</span>
  </div>
</div>

<style>
.circular-progress-container {
  position: relative;
  width: 120px;
  height: 120px;
  margin: 20px;
}

.circular {
  width: 100%;
  height: 100%;
  transform: rotate(-90deg);
  border-radius: 50%;
  background: conic-gradient(#007bff 0% 75%, #e9ecef 75% 100%);
}

.circular::-webkit-progress-bar {
  background: transparent;
}

.circular::-webkit-progress-value {
  background: transparent;
}

.circular::-moz-progress-bar {
  background: transparent;
}

.circular-label {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}

#circular-value {
  display: block;
  font-size: 1.5em;
  font-weight: bold;
  color: #007bff;
}

.circular-label span:last-child {
  font-size: 0.8em;
  color: #666;
}
</style>
```

**Progress with JavaScript animation:**
```html
<div class="animated-progress-container">
  <progress id="js-progress" value="0" max="100">0%</progress>
  <div class="controls">
    <button onclick="startProgress()">Start</button>
    <button onclick="pauseProgress()">Pause</button>
    <button onclick="resetProgress()">Reset</button>
  </div>
</div>

<script>
let progressInterval;
const progress = document.getElementById('js-progress');

function startProgress() {
  clearInterval(progressInterval);
  
  progressInterval = setInterval(() => {
    if (progress.value < 100) {
      progress.value += 1;
      progress.textContent = progress.value + '%';
    } else {
      clearInterval(progressInterval);
    }
  }, 50);
}

function pauseProgress() {
  clearInterval(progressInterval);
}

function resetProgress() {
  clearInterval(progressInterval);
  progress.value = 0;
  progress.textContent = '0%';
}
</script>

<style>
.animated-progress-container {
  max-width: 400px;
  margin: 20px 0;
}

#js-progress {
  width: 100%;
  height: 20px;
  margin-bottom: 15px;
}

.controls {
  display: flex;
  gap: 10px;
  justify-content: center;
}

.controls button {
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  background: #007bff;
  color: white;
  cursor: pointer;
}

.controls button:hover {
  background: #0056b3;
}
</style>
```

---

## Notes

* **Browser compatibility**: 
  - Well supported in modern browsers
  - Styling capabilities vary across browsers
  - Always provide text content as fallback
* **Styling limitations**:
  - Different browsers use different pseudo-elements for styling
  - WebKit: `::-webkit-progress-bar` and `::-webkit-progress-value`
  - Firefox: `::-moz-progress-bar`
  - Limited styling options in some browsers
* **Accessibility best practices**:
  - Use `aria-label` or `aria-labelledby` for clear descriptions
  - Provide current value and maximum through ARIA attributes
  - Ensure sufficient color contrast for progress indicators
  - Update progress values programmatically with clear feedback
* **Common mistakes**:
  - Using without proper value/max attributes for determinate progress
  - Forgetting to update both value attribute and text content
  - Overly complex styling that reduces usability
  - Not providing fallback content for unsupported browsers
* **Best practices**:
  - Use indeterminate progress (`<progress>`) for unknown durations
  - Use determinate progress (`<progress value="X" max="Y">`) for known progress
  - Update progress frequently enough to provide smooth feedback
  - Provide additional context about what's being loaded
  - Use appropriate colors (green for success, yellow for warning, red for errors)
* **Performance considerations**:
  - Frequent updates can impact performance on low-end devices
  - Use CSS transitions for smooth animations
  - Consider debouncing rapid progress updates
* **Mobile considerations**:
  - Ensure progress bars are large enough for touch interfaces
  - Test color contrast in different lighting conditions
  - Consider battery impact for long-running progress indicators

---
