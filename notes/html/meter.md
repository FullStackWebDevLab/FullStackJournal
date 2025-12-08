# `<meter>`

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

The `<meter>` element represents a scalar measurement within a known range, or a fractional value. It is designed to display gauges and measurements such as disk usage, vote counts, or completion percentages. Unlike `<progress>`, which indicates task completion, `<meter>` shows a measurement within a defined range with optional optimal and suboptimal zones.

---

## Syntax and Variants

+ **Standard syntax**: `<meter>...</meter>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain fallback text content
+ **No self-closing variant**: Must have closing tag
+ **No alternative forms**: Standard syntax only

---

## Attributes

+ **Core attributes**:
  - `value` (required): Current numeric value of the measurement
  - `min` (optional): Lower bound of the range (default: 0)
  - `max` (optional): Upper bound of the range (default: 1)
  - `low` (optional): Point marking the upper bound of the low range
  - `high` (optional): Point marking the lower bound of the high range
  - `optimum` (optional): Optimal numeric value
  - `form` (optional): Associates with a form element

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, `lang`, `dir`, etc.

+ **Event handlers**: All global event attributes supported

---

## Content Model

+ **Permitted content**: Phrasing content, but no `<meter>` descendants
+ **Allowed content**:
  - Text content for fallback display
  - Phrasing elements when styled appropriately
+ **Restricted content**: Cannot contain other `<meter>` elements
+ **Fallback content**: Text content is shown when meter is not supported

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within paragraphs for inline measurements
  - Within list items for status indicators
  - Within table cells for data visualization
  - In dashboards and monitoring interfaces
+ **Nesting relationships**:
  - Can be contained within most inline contexts
  - Often paired with labels and value displays
  - Can be styled with CSS for custom appearances

---

## Behavior and Semantics

+ **Default display**: Inline-block element
+ **Default styling**:
  - `display: inline-block`
  - Browser-specific visual representation
  - Typically shows as a horizontal bar with color zones
  - Colors indicate value ranges (green for good, yellow for medium, red for low)
+ **Semantic meaning**:
  - Represents a scalar measurement within a known range
  - Indicates quantitative data with contextual ranges
  - Provides machine-readable measurement data
+ **Accessibility role**:
  - Implicit ARIA role: `meter`
  - Screen readers announce value, min, max, and sometimes range context
  - Important to provide accessible labels and descriptions
+ **Range interpretation**:
  - Values between `min` and `low`: Considered low
  - Values between `low` and `high`: Considered medium
  - Values between `high` and `max`: Considered high
  - Position relative to `optimum` affects color coding

---

## Examples

**Basic disk usage meter:**
```html
<label for="diskUsage">Disk Usage:</label>
<meter id="diskUsage" value="0.7" min="0" max="1">70% used</meter>
<span>70%</span>
```

**Storage capacity with ranges:**
```html
<div class="storage-meter">
  <label>Storage Capacity: <output id="storageValue">750GB</output> used</label>
  <meter value="750" min="0" max="1000" low="200" high="800" optimum="400">
    750GB out of 1000GB used
  </meter>
  <div class="meter-labels">
    <span>0GB</span>
    <span>1000GB</span>
  </div>
</div>

<style>
.storage-meter {
  max-width: 400px;
  margin: 20px 0;
}

.storage-meter label {
  display: block;
  margin-bottom: 8px;
  font-weight: bold;
}

.meter-labels {
  display: flex;
  justify-content: space-between;
  margin-top: 4px;
  font-size: 0.8em;
  color: #666;
}
</style>
```

**Voting results with optimal range:**
```html
<div class="vote-results">
  <h3>Vote Results</h3>
  
  <div class="vote-item">
    <label>Candidate A:</label>
    <meter value="45" min="0" max="100" low="25" high="75" optimum="50">45%</meter>
    <span class="vote-percent">45%</span>
  </div>
  
  <div class="vote-item">
    <label>Candidate B:</label>
    <meter value="35" min="0" max="100" low="25" high="75" optimum="50">35%</meter>
    <span class="vote-percent">35%</span>
  </div>
  
  <div class="vote-item">
    <label>Candidate C:</label>
    <meter value="20" min="0" max="100" low="25" high="75" optimum="50">20%</meter>
    <span class="vote-percent">20%</span>
  </div>
</div>

<style>
.vote-results {
  max-width: 500px;
  margin: 20px 0;
  padding: 20px;
  background: #f8f9fa;
  border-radius: 8px;
}

.vote-results h3 {
  margin-top: 0;
  color: #333;
}

.vote-item {
  display: flex;
  align-items: center;
  margin-bottom: 12px;
  gap: 12px;
}

.vote-item label {
  min-width: 100px;
  font-weight: 500;
}

.vote-item meter {
  flex: 1;
  height: 20px;
}

.vote-percent {
  min-width: 40px;
  text-align: right;
  font-weight: bold;
  color: #333;
}
</style>
```

**Project completion status:**
```html
<div class="project-status">
  <h3>Project Completion</h3>
  
  <div class="status-item">
    <label>Design Phase:</label>
    <meter value="100" min="0" max="100" optimum="100">100% complete</meter>
    <span class="status-badge complete">Complete</span>
  </div>
  
  <div class="status-item">
    <label>Development:</label>
    <meter value="75" min="0" max="100" optimum="100">75% complete</meter>
    <span class="status-badge in-progress">In Progress</span>
  </div>
  
  <div class="status-item">
    <label>Testing:</label>
    <meter value="25" min="0" max="100" optimum="100">25% complete</meter>
    <span class="status-badge not-started">Not Started</span>
  </div>
</div>

<style>
.project-status {
  max-width: 500px;
  margin: 20px 0;
  padding: 20px;
  background: white;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
}

.project-status h3 {
  margin-top: 0;
  color: #333;
  border-bottom: 2px solid #007bff;
  padding-bottom: 8px;
}

.status-item {
  display: flex;
  align-items: center;
  margin-bottom: 15px;
  gap: 15px;
}

.status-item label {
  min-width: 120px;
  font-weight: 500;
  color: #555;
}

.status-item meter {
  flex: 1;
  height: 16px;
}

.status-badge {
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 0.8em;
  font-weight: bold;
  min-width: 80px;
  text-align: center;
}

.status-badge.complete {
  background: #d4edda;
  color: #155724;
}

.status-badge.in-progress {
  background: #fff3cd;
  color: #856404;
}

.status-badge.not-started {
  background: #f8d7da;
  color: #721c24;
}
</style>
```

**Custom styled meter with CSS:**
```html
<div class="custom-meter-container">
  <label for="customMeter">Performance Score:</label>
  <div class="meter-wrapper">
    <meter id="customMeter" 
           value="0.8" 
           min="0" 
           max="1" 
           low="0.3" 
           high="0.7" 
           optimum="0.8">
      80% performance
    </meter>
    <div class="meter-fill" aria-hidden="true"></div>
  </div>
  <output for="customMeter" class="meter-value">80%</output>
</div>

<style>
.custom-meter-container {
  max-width: 400px;
  margin: 20px 0;
}

.meter-wrapper {
  position: relative;
  height: 24px;
  background: #f0f0f0;
  border-radius: 12px;
  overflow: hidden;
  margin: 8px 0;
}

/* Hide default meter appearance */
#customMeter {
  position: absolute;
  width: 100%;
  height: 100%;
  opacity: 0;
  pointer-events: none;
}

.meter-fill {
  height: 100%;
  background: linear-gradient(90deg, #dc3545, #ffc107, #28a745);
  border-radius: 12px;
  width: 80%; /* Matches meter value */
  transition: width 0.3s ease;
  position: relative;
}

.meter-fill::after {
  content: '';
  position: absolute;
  right: 0;
  top: 0;
  bottom: 0;
  width: 4px;
  background: rgba(0, 0, 0, 0.3);
  border-radius: 0 12px 12px 0;
}

.meter-value {
  display: block;
  text-align: center;
  font-weight: bold;
  color: #333;
  font-size: 1.1em;
}

/* Update fill based on meter value */
#customMeter[value="0.1"] ~ .meter-fill { width: 10%; }
#customMeter[value="0.2"] ~ .meter-fill { width: 20%; }
#customMeter[value="0.3"] ~ .meter-fill { width: 30%; }
#customMeter[value="0.4"] ~ .meter-fill { width: 40%; }
#customMeter[value="0.5"] ~ .meter-fill { width: 50%; }
#customMeter[value="0.6"] ~ .meter-fill { width: 60%; }
#customMeter[value="0.7"] ~ .meter-fill { width: 70%; }
#customMeter[value="0.8"] ~ .meter-fill { width: 80%; }
#customMeter[value="0.9"] ~ .meter-fill { width: 90%; }
#customMeter[value="1"] ~ .meter-fill { width: 100%; }
</style>
```

**Skill assessment dashboard:**
```html
<div class="skills-dashboard">
  <h3>Technical Skills Assessment</h3>
  
  <div class="skill-category">
    <h4>Frontend Development</h4>
    <div class="skill-item">
      <label>HTML/CSS:</label>
      <meter value="90" min="0" max="100" low="60" high="85" optimum="90">90%</meter>
      <span class="skill-level">Expert</span>
    </div>
    <div class="skill-item">
      <label>JavaScript:</label>
      <meter value="80" min="0" max="100" low="60" high="85" optimum="90">80%</meter>
      <span class="skill-level">Advanced</span>
    </div>
    <div class="skill-item">
      <label>React:</label>
      <meter value="75" min="0" max="100" low="60" high="85" optimum="90">75%</meter>
      <span class="skill-level">Proficient</span>
    </div>
  </div>
  
  <div class="skill-category">
    <h4>Backend Development</h4>
    <div class="skill-item">
      <label>Node.js:</label>
      <meter value="70" min="0" max="100" low="60" high="85" optimum="90">70%</meter>
      <span class="skill-level">Proficient</span>
    </div>
    <div class="skill-item">
      <label>Database Design:</label>
      <meter value="65" min="0" max="100" low="60" high="85" optimum="90">65%</meter>
      <span class="skill-level">Intermediate</span>
    </div>
  </div>
</div>

<style>
.skills-dashboard {
  max-width: 600px;
  margin: 20px 0;
  padding: 24px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.skills-dashboard h3 {
  margin-top: 0;
  color: #2c3e50;
  text-align: center;
  border-bottom: 2px solid #3498db;
  padding-bottom: 12px;
}

.skill-category {
  margin-bottom: 24px;
}

.skill-category h4 {
  margin: 0 0 16px 0;
  color: #34495e;
  font-size: 1.1em;
  padding-left: 8px;
  border-left: 4px solid #3498db;
}

.skill-item {
  display: flex;
  align-items: center;
  margin-bottom: 12px;
  gap: 15px;
}

.skill-item label {
  min-width: 120px;
  font-weight: 500;
  color: #555;
}

.skill-item meter {
  flex: 1;
  height: 14px;
}

.skill-level {
  min-width: 100px;
  font-size: 0.9em;
  font-weight: 500;
  text-align: right;
  color: #666;
}

/* Custom meter colors for skill levels */
.skill-item meter::-webkit-meter-bar {
  background: #f0f0f0;
  border-radius: 7px;
}

.skill-item meter::-webkit-meter-optimum-value {
  background: #27ae60;
  border-radius: 7px;
}

.skill-item meter::-webkit-meter-suboptimum-value {
  background: #f39c12;
  border-radius: 7px;
}

.skill-item meter::-webkit-meter-even-less-good-value {
  background: #e74c3c;
  border-radius: 7px;
}
</style>
```

**Dynamic meter with JavaScript updates:**
```html
<div class="dynamic-meter">
  <h3>Resource Monitor</h3>
  
  <div class="resource">
    <label>CPU Usage:</label>
    <meter id="cpuMeter" value="30" min="0" max="100" low="50" high="80" optimum="30">
      30%
    </meter>
    <output id="cpuValue">30%</output>
  </div>
  
  <div class="resource">
    <label>Memory Usage:</label>
    <meter id="memoryMeter" value="65" min="0" max="100" low="50" high="80" optimum="30">
      65%
    </meter>
    <output id="memoryValue">65%</output>
  </div>
  
  <div class="resource">
    <label>Disk I/O:</label>
    <meter id="diskMeter" value="45" min="0" max="100" low="50" high="80" optimum="30">
      45%
    </meter>
    <output id="diskValue">45%</output>
  </div>
  
  <div class="controls">
    <button onclick="startMonitoring()">Start Monitoring</button>
    <button onclick="stopMonitoring()">Stop Monitoring</button>
    <button onclick="resetMeters()">Reset</button>
  </div>
</div>

<script>
let monitoringInterval;

function getRandomValue(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

function updateMeters() {
  const cpuValue = getRandomValue(20, 90);
  const memoryValue = getRandomValue(40, 95);
  const diskValue = getRandomValue(10, 70);
  
  document.getElementById('cpuMeter').value = cpuValue;
  document.getElementById('cpuValue').textContent = cpuValue + '%';
  
  document.getElementById('memoryMeter').value = memoryValue;
  document.getElementById('memoryValue').textContent = memoryValue + '%';
  
  document.getElementById('diskMeter').value = diskValue;
  document.getElementById('diskValue').textContent = diskValue + '%';
}

function startMonitoring() {
  if (monitoringInterval) return;
  monitoringInterval = setInterval(updateMeters, 2000);
  updateMeters(); // Initial update
}

function stopMonitoring() {
  if (monitoringInterval) {
    clearInterval(monitoringInterval);
    monitoringInterval = null;
  }
}

function resetMeters() {
  stopMonitoring();
  
  document.getElementById('cpuMeter').value = 0;
  document.getElementById('cpuValue').textContent = '0%';
  
  document.getElementById('memoryMeter').value = 0;
  document.getElementById('memoryValue').textContent = '0%';
  
  document.getElementById('diskMeter').value = 0;
  document.getElementById('diskValue').textContent = '0%';
}

// Clean up on page unload
window.addEventListener('beforeunload', stopMonitoring);
</script>

<style>
.dynamic-meter {
  max-width: 500px;
  margin: 20px 0;
  padding: 24px;
  background: #2c3e50;
  color: white;
  border-radius: 12px;
  font-family: 'Segoe UI', system-ui, sans-serif;
}

.dynamic-meter h3 {
  margin-top: 0;
  text-align: center;
  color: #ecf0f1;
  border-bottom: 1px solid #34495e;
  padding-bottom: 12px;
}

.resource {
  display: flex;
  align-items: center;
  margin-bottom: 16px;
  gap: 15px;
}

.resource label {
  min-width: 100px;
  font-weight: 500;
  color: #bdc3c7;
}

.resource meter {
  flex: 1;
  height: 20px;
}

.resource output {
  min-width: 50px;
  text-align: right;
  font-weight: bold;
  color: #ecf0f1;
  font-family: 'Monaco', 'Menlo', monospace;
}

.controls {
  display: flex;
  gap: 10px;
  justify-content: center;
  margin-top: 20px;
}

.controls button {
  padding: 8px 16px;
  border: none;
  border-radius: 6px;
  background: #3498db;
  color: white;
  cursor: pointer;
  font-size: 14px;
  transition: background 0.2s;
}

.controls button:hover {
  background: #2980b9;
}

.controls button:last-child {
  background: #e74c3c;
}

.controls button:last-child:hover {
  background: #c0392b;
}

/* Custom styling for meters in dark theme */
.resource meter::-webkit-meter-bar {
  background: #34495e;
  border-radius: 10px;
}

.resource meter::-webkit-meter-optimum-value {
  background: #27ae60;
  border-radius: 10px;
}

.resource meter::-webkit-meter-suboptimum-value {
  background: #f39c12;
  border-radius: 10px;
}

.resource meter::-webkit-meter-even-less-good-value {
  background: #e74c3c;
  border-radius: 10px;
}
</style>
```

**Accessible meter with ARIA attributes:**
```html
<div class="accessible-meter" role="region" aria-labelledby="meterTitle">
  <h3 id="meterTitle">Battery Status</h3>
  
  <div class="meter-group">
    <div class="meter-info">
      <span id="batteryDesc">Battery level at 75 percent</span>
      <span class="sr-only" id="batteryRange">Minimum 0 percent, maximum 100 percent</span>
    </div>
    
    <meter id="batteryMeter"
           value="75"
           min="0"
           max="100"
           low="20"
           high="80"
           optimum="100"
           aria-labelledby="batteryDesc"
           aria-describedby="batteryRange">
      75% battery remaining
    </meter>
    
    <div class="meter-labels" aria-hidden="true">
      <span>0%</span>
      <span>50%</span>
      <span>100%</span>
    </div>
    
    <div class="status-message" id="statusMessage" aria-live="polite">
      Battery level is good.
    </div>
  </div>
</div>

<script>
const batteryMeter = document.getElementById('batteryMeter');
const batteryDesc = document.getElementById('batteryDesc');
const statusMessage = document.getElementById('statusMessage');

function updateBatteryStatus() {
  const value = batteryMeter.value;
  const low = batteryMeter.low || 20;
  const high = batteryMeter.high || 80;
  
  batteryDesc.textContent = `Battery level at ${value} percent`;
  
  if (value <= low) {
    statusMessage.textContent = 'Battery level is critical. Please charge soon.';
    statusMessage.style.color = '#e74c3c';
  } else if (value <= high) {
    statusMessage.textContent = 'Battery level is acceptable.';
    statusMessage.style.color = '#f39c12';
  } else {
    statusMessage.textContent = 'Battery level is good.';
    statusMessage.style.color = '#27ae60';
  }
}

// Simulate battery changes for demo
setInterval(() => {
  const currentValue = parseInt(batteryMeter.value);
  const newValue = Math.max(0, Math.min(100, currentValue + (Math.random() * 10 - 5)));
  batteryMeter.value = newValue;
  updateBatteryStatus();
}, 3000);

// Initial update
updateBatteryStatus();
</script>

<style>
.accessible-meter {
  max-width: 400px;
  margin: 20px 0;
  padding: 20px;
  background: white;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
}

.accessible-meter h3 {
  margin-top: 0;
  color: #333;
  text-align: center;
}

.meter-group {
  margin-top: 16px;
}

.meter-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 8px;
  font-size: 0.9em;
  color: #666;
}

#batteryMeter {
  width: 100%;
  height: 24px;
  margin: 8px 0;
}

.meter-labels {
  display: flex;
  justify-content: space-between;
  margin-top: 4px;
  font-size: 0.8em;
  color: #999;
}

.status-message {
  margin-top: 12px;
  padding: 8px 12px;
  background: #f8f9fa;
  border-radius: 4px;
  font-weight: 500;
  text-align: center;
  transition: all 0.3s ease;
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

/* Custom meter styling for better visibility */
#batteryMeter::-webkit-meter-bar {
  background: #f0f0f0;
  border-radius: 12px;
  border: 1px solid #ddd;
}

#batteryMeter::-webkit-meter-optimum-value {
  background: linear-gradient(90deg, #27ae60, #2ecc71);
  border-radius: 12px;
}

#batteryMeter::-webkit-meter-suboptimum-value {
  background: linear-gradient(90deg, #f39c12, #f1c40f);
  border-radius: 12px;
}

#batteryMeter::-webkit-meter-even-less-good-value {
  background: linear-gradient(90deg, #e74c3c, #c0392b);
  border-radius: 12px;
}
</style>
```

**Survey results visualization:**
```html
<div class="survey-results">
  <h3>Customer Satisfaction Survey</h3>
  <p class="survey-description">How satisfied are you with our service?</p>
  
  <div class="result-item">
    <label>Very Satisfied:</label>
    <meter value="45" min="0" max="100" optimum="100">45%</meter>
    <span class="result-value">45%</span>
    <span class="result-count">(90 responses)</span>
  </div>
  
  <div class="result-item">
    <label>Satisfied:</label>
    <meter value="35" min="0" max="100" optimum="100">35%</meter>
    <span class="result-value">35%</span>
    <span class="result-count">(70 responses)</span>
  </div>
  
  <div class="result-item">
    <label>Neutral:</label>
    <meter value="12" min="0" max="100" optimum="100">12%</meter>
    <span class="result-value">12%</span>
    <span class="result-count">(24 responses)</span>
  </div>
  
  <div class="result-item">
    <label>Dissatisfied:</label>
    <meter value="5" min="0" max="100" optimum="100">5%</meter>
    <span class="result-value">5%</span>
    <span class="result-count">(10 responses)</span>
  </div>
  
  <div class="result-item">
    <label>Very Dissatisfied:</label>
    <meter value="3" min="0" max="100" optimum="100">3%</meter>
    <span class="result-value">3%</span>
    <span class="result-count">(6 responses)</span>
  </div>
  
  <div class="survey-summary">
    <strong>Total Responses: 200</strong>
    <span class="satisfaction-score">80% Positive</span>
  </div>
</div>

<style>
.survey-results {
  max-width: 600px;
  margin: 20px 0;
  padding: 24px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.survey-results h3 {
  margin-top: 0;
  color: #2c3e50;
  text-align: center;
  border-bottom: 2px solid #3498db;
  padding-bottom: 12px;
}

.survey-description {
  text-align: center;
  color: #666;
  margin-bottom: 24px;
  font-style: italic;
}

.result-item {
  display: grid;
  grid-template-columns: 120px 1fr 60px 100px;
  align-items: center;
  gap: 15px;
  margin-bottom: 12px;
  padding: 8px 0;
}

.result-item label {
  font-weight: 500;
  color: #555;
  text-align: right;
}

.result-item meter {
  height: 20px;
}

.result-value {
  font-weight: bold;
  color: #333;
  text-align: center;
}

.result-count {
  font-size: 0.8em;
  color: #999;
  text-align: right;
}

.survey-summary {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 20px;
  padding-top: 16px;
  border-top: 1px solid #e0e0e0;
  font-weight: 500;
}

.satisfaction-score {
  background: #27ae60;
  color: white;
  padding: 6px 12px;
  border-radius: 16px;
  font-size: 0.9em;
}

/* Color meters based on satisfaction level */
.result-item:nth-child(2) meter { /* Very Satisfied */
  color: #27ae60;
}

.result-item:nth-child(3) meter { /* Satisfied */
  color: #2ecc71;
}

.result-item:nth-child(4) meter { /* Neutral */
  color: #f39c12;
}

.result-item:nth-child(5) meter { /* Dissatisfied */
  color: #e67e22;
}

.result-item:nth-child(6) meter { /* Very Dissatisfied */
  color: #e74c3c;
}

@media (max-width: 600px) {
  .result-item {
    grid-template-columns: 1fr;
    gap: 8px;
    text-align: center;
  }
  
  .result-item label {
    text-align: center;
  }
}
</style>
```

---

## Notes

* **Browser support**: 
  - Well supported in modern browsers (Chrome, Firefox, Safari, Edge)
  - Some older browsers may not support the element
  - Fallback content is crucial for unsupported browsers
* **Accessibility considerations**:
  - Screen readers announce the value and range information
  - Use `aria-label` or `aria-labelledby` for additional context
  - Provide text alternatives for the visual representation
  - Ensure color contrast meets accessibility standards
* **Styling limitations**:
  - Limited CSS customization across browsers
  - Vendor prefixes required for WebKit/Blink browsers
  - Consider custom CSS implementations for complex designs
* **Common issues**:
  - Forgetting to set required `value` attribute
  - Confusing with `<progress>` element
  - Not providing meaningful fallback content
  - Incorrect range calculations
* **Best practices**:
  - Always include fallback text content
  - Use appropriate `min`, `max`, and `value` attributes
  - Set `low`, `high`, and `optimum` for contextual ranges
  - Provide labels and descriptions for clarity
  - Test across different browsers and devices
* **Performance**: 
  - Lightweight element with minimal performance impact
  - No inherent animation or interaction overhead
  - Suitable for real-time data updates
* **Mobile considerations**:
  - Ensure touch-friendly sizes for interactive meters
  - Consider responsive design for different screen sizes
  - Test color visibility in different lighting conditions
* **Semantic differences from `<progress>`**:
  - `<meter>`: Measurement within a known range (disk space, votes)
  - `<progress>`: Completion of a task (file upload, installation)
  - Choose based on whether you're measuring a value or tracking progress

---
