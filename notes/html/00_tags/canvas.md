# `<canvas>`

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

The `<canvas>` element provides a resolution-dependent bitmap canvas that can be used for rendering graphics, game visuals, data visualizations, image manipulation, and other dynamic visual content via JavaScript. It serves as a container for drawing graphics programmatically and does not have built-in drawing capabilities; all rendering must be done through the Canvas API using JavaScript.

---

## Syntax and Variants

+ **Standard syntax**: `<canvas>...</canvas>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain fallback content
+ **No self-closing variant**: Must have closing tag
+ **No alternative forms**: Standard syntax only

---

## Attributes

+ **Core attributes**:
  - `width` (optional): Width of the coordinate space in CSS pixels (default: 300)
  - `height` (optional): Height of the coordinate space in CSS pixels (default: 150)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, `lang`, `dir`, etc.

+ **Event handlers**: All global event attributes supported

---

## Content Model

+ **Permitted content**: Transparent content model, but typically contains fallback content
+ **Allowed content**:
  - Text and character references
  - Other HTML elements for fallback display
  - Images, paragraphs, or any content for non-supporting browsers
+ **Restricted content**: No specific restrictions beyond normal HTML validation
+ **Fallback content**: Displayed when canvas is not supported

---

## Context

+ **Valid parents**: Any element that accepts flow content
+ **Common locations**:
  - Within `<body>` for standalone graphics
  - Within `<article>`, `<section>`, or `<div>` for contextual graphics
  - Within interactive applications and games
  - In data visualization dashboards
+ **Nesting relationships**:
  - Can be contained within most block-level elements
  - Often wrapped in container divs for styling and positioning
  - Can be combined with other HTML elements for complex interfaces

---

## Behavior and Semantics

+ **Default display**: Inline-block element
+ **Default styling**:
  - `display: inline-block`
  - `width: 300px` (default coordinate space width)
  - `height: 150px` (default coordinate space height)
  - No inherent borders or background
  - Behaves like a replaced element
+ **Semantic meaning**:
  - Represents a bitmap drawing surface
  - Indicates dynamic, script-generated visual content
  - Provides no inherent semantic meaning for its visual content
+ **Accessibility role**:
  - Implicit ARIA role: `canvas` (generic container)
  - Screen readers treat as a generic container
  - Critical to provide fallback content and ARIA labels
+ **Rendering context**: Requires JavaScript to obtain 2D or WebGL rendering context

---

## Examples

**Basic canvas setup:**
```html
<canvas id="myCanvas" width="400" height="200">
  Your browser does not support the HTML canvas element.
  Here would be a beautiful drawing of a red rectangle.
</canvas>

<script>
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// Draw a red rectangle
ctx.fillStyle = 'red';
ctx.fillRect(10, 10, 150, 100);
</script>
```

**Canvas with responsive sizing:**
```html
<div class="canvas-container">
  <canvas id="responsiveCanvas">
    This canvas displays a responsive blue circle. 
    Please upgrade your browser to see it.
  </canvas>
</div>

<script>
function setupCanvas() {
  const canvas = document.getElementById('responsiveCanvas');
  const container = canvas.parentElement;
  
  // Set display size
  canvas.style.width = '100%';
  canvas.style.height = '400px';
  
  // Set actual size in memory (scaled for retina displays)
  const scale = window.devicePixelRatio || 1;
  canvas.width = container.offsetWidth * scale;
  canvas.height = 400 * scale;
  
  const ctx = canvas.getContext('2d');
  
  // Normalize coordinate system to use CSS pixels
  ctx.scale(scale, scale);
  
  // Draw a blue circle
  ctx.fillStyle = '#007bff';
  ctx.beginPath();
  ctx.arc(canvas.width / (2 * scale), 200, 80, 0, Math.PI * 2);
  ctx.fill();
}

window.addEventListener('load', setupCanvas);
window.addEventListener('resize', setupCanvas);
</script>

<style>
.canvas-container {
  max-width: 800px;
  margin: 0 auto;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 20px;
  background: #f8f9fa;
}
</style>
```

**Interactive drawing application:**
```html
<div class="drawing-app">
  <h3>Simple Drawing Canvas</h3>
  <canvas id="drawingCanvas" width="600" height="400">
    Your browser doesn't support interactive drawing.
    Please use a modern browser to experience this feature.
  </canvas>
  <div class="controls">
    <button onclick="clearCanvas()">Clear</button>
    <input type="color" id="colorPicker" value="#000000">
    <input type="range" id="brushSize" min="1" max="50" value="5">
    <span id="brushSizeValue">5px</span>
  </div>
</div>

<script>
const canvas = document.getElementById('drawingCanvas');
const ctx = canvas.getContext('2d');
const colorPicker = document.getElementById('colorPicker');
const brushSize = document.getElementById('brushSize');
const brushSizeValue = document.getElementById('brushSizeValue');

let isDrawing = false;
let lastX = 0;
let lastY = 0;

// Set initial styles
ctx.strokeStyle = colorPicker.value;
ctx.lineWidth = brushSize.value;
ctx.lineCap = 'round';
ctx.lineJoin = 'round';

// Drawing functions
function startDrawing(e) {
  isDrawing = true;
  [lastX, lastY] = [e.offsetX, e.offsetY];
}

function draw(e) {
  if (!isDrawing) return;
  
  ctx.beginPath();
  ctx.moveTo(lastX, lastY);
  ctx.lineTo(e.offsetX, e.offsetY);
  ctx.stroke();
  
  [lastX, lastY] = [e.offsetX, e.offsetY];
}

function stopDrawing() {
  isDrawing = false;
}

function clearCanvas() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
}

// Event listeners
canvas.addEventListener('mousedown', startDrawing);
canvas.addEventListener('mousemove', draw);
canvas.addEventListener('mouseup', stopDrawing);
canvas.addEventListener('mouseout', stopDrawing);

colorPicker.addEventListener('input', (e) => {
  ctx.strokeStyle = e.target.value;
});

brushSize.addEventListener('input', (e) => {
  ctx.lineWidth = e.target.value;
  brushSizeValue.textContent = e.target.value + 'px';
});
</script>

<style>
.drawing-app {
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.drawing-app h3 {
  margin-top: 0;
  color: #333;
}

#drawingCanvas {
  border: 2px solid #ddd;
  border-radius: 4px;
  cursor: crosshair;
  display: block;
  margin: 0 auto;
}

.controls {
  margin-top: 15px;
  display: flex;
  gap: 15px;
  align-items: center;
  justify-content: center;
}

.controls button {
  padding: 8px 16px;
  background: #dc3545;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.controls button:hover {
  background: #c82333;
}
</style>
```

**Data visualization chart:**
```html
<div class="chart-container">
  <h3>Monthly Sales Data</h3>
  <canvas id="salesChart" width="600" height="300">
    Alternative text-based sales data:
    January: $12,000
    February: $19,000
    March: $15,000
    April: $22,000
    May: $18,000
    June: $25,000
  </canvas>
</div>

<script>
function drawChart() {
  const canvas = document.getElementById('salesChart');
  const ctx = canvas.getContext('2d');
  
  const data = [12000, 19000, 15000, 22000, 18000, 25000];
  const labels = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'];
  const maxValue = Math.max(...data);
  
  const padding = 40;
  const chartWidth = canvas.width - padding * 2;
  const chartHeight = canvas.height - padding * 2;
  const barWidth = chartWidth / data.length * 0.8;
  const barSpacing = chartWidth / data.length * 0.2;
  
  // Clear canvas
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  
  // Draw grid lines
  ctx.strokeStyle = '#e0e0e0';
  ctx.lineWidth = 1;
  
  for (let i = 0; i <= 5; i++) {
    const y = padding + (chartHeight / 5) * i;
    ctx.beginPath();
    ctx.moveTo(padding, y);
    ctx.lineTo(canvas.width - padding, y);
    ctx.stroke();
    
    // Y-axis labels
    ctx.fillStyle = '#666';
    ctx.font = '12px Arial';
    ctx.textAlign = 'right';
    ctx.fillText('$' + (maxValue - (maxValue / 5) * i).toLocaleString(), padding - 5, y + 4);
  }
  
  // Draw bars
  data.forEach((value, index) => {
    const x = padding + (chartWidth / data.length) * index + barSpacing / 2;
    const barHeight = (value / maxValue) * chartHeight;
    const y = canvas.height - padding - barHeight;
    
    // Bar gradient
    const gradient = ctx.createLinearGradient(x, y, x, y + barHeight);
    gradient.addColorStop(0, '#4a90e2');
    gradient.addColorStop(1, '#2c5aa0');
    
    ctx.fillStyle = gradient;
    ctx.fillRect(x, y, barWidth, barHeight);
    
    // Value labels
    ctx.fillStyle = '#333';
    ctx.font = '12px Arial';
    ctx.textAlign = 'center';
    ctx.fillText('$' + value.toLocaleString(), x + barWidth / 2, y - 8);
    
    // X-axis labels
    ctx.fillStyle = '#666';
    ctx.fillText(labels[index], x + barWidth / 2, canvas.height - padding + 20);
  });
  
  // Draw axes
  ctx.strokeStyle = '#333';
  ctx.lineWidth = 2;
  
  // Y-axis
  ctx.beginPath();
  ctx.moveTo(padding, padding);
  ctx.lineTo(padding, canvas.height - padding);
  ctx.stroke();
  
  // X-axis
  ctx.beginPath();
  ctx.moveTo(padding, canvas.height - padding);
  ctx.lineTo(canvas.width - padding, canvas.height - padding);
  ctx.stroke();
}

window.addEventListener('load', drawChart);
</script>

<style>
.chart-container {
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.chart-container h3 {
  margin-top: 0;
  text-align: center;
  color: #333;
}

#salesChart {
  display: block;
  margin: 0 auto;
}
</style>
```

**Game animation with requestAnimationFrame:**
```html
<div class="game-container">
  <h3>Bouncing Ball Animation</h3>
  <canvas id="gameCanvas" width="400" height="300">
    An animated bouncing ball would appear here if your browser supported canvas.
    Consider upgrading to a modern browser for the full experience.
  </canvas>
  <div class="game-controls">
    <button onclick="toggleAnimation()" id="toggleBtn">Pause</button>
    <button onclick="resetAnimation()">Reset</button>
  </div>
</div>

<script>
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

let ball = {
  x: 50,
  y: 50,
  radius: 20,
  dx: 4,
  dy: 3,
  color: '#e74c3c'
};

let animationId = null;
let isAnimating = true;

function drawBall() {
  ctx.beginPath();
  ctx.arc(ball.x, ball.y, ball.radius, 0, Math.PI * 2);
  ctx.fillStyle = ball.color;
  ctx.fill();
  ctx.closePath();
}

function update() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  
  // Update ball position
  ball.x += ball.dx;
  ball.y += ball.dy;
  
  // Wall collision detection
  if (ball.x + ball.radius > canvas.width || ball.x - ball.radius < 0) {
    ball.dx = -ball.dx;
    ball.color = getRandomColor();
  }
  
  if (ball.y + ball.radius > canvas.height || ball.y - ball.radius < 0) {
    ball.dy = -ball.dy;
    ball.color = getRandomColor();
  }
  
  drawBall();
}

function animate() {
  update();
  if (isAnimating) {
    animationId = requestAnimationFrame(animate);
  }
}

function toggleAnimation() {
  isAnimating = !isAnimating;
  document.getElementById('toggleBtn').textContent = isAnimating ? 'Pause' : 'Play';
  
  if (isAnimating) {
    animate();
  } else {
    cancelAnimationFrame(animationId);
  }
}

function resetAnimation() {
  ball.x = 50;
  ball.y = 50;
  ball.dx = 4;
  ball.dy = 3;
  ball.color = '#e74c3c';
}

function getRandomColor() {
  const colors = ['#e74c3c', '#3498db', '#2ecc71', '#f39c12', '#9b59b6', '#1abc9c'];
  return colors[Math.floor(Math.random() * colors.length)];
}

// Start animation
animate();
</script>

<style>
.game-container {
  max-width: 400px;
  margin: 20px auto;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  text-align: center;
}

.game-container h3 {
  margin-top: 0;
  color: #333;
}

#gameCanvas {
  border: 2px solid #333;
  border-radius: 4px;
  background: #f8f9fa;
  display: block;
  margin: 0 auto 15px;
}

.game-controls {
  display: flex;
  gap: 10px;
  justify-content: center;
}

.game-controls button {
  padding: 8px 16px;
  background: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.game-controls button:hover {
  background: #0056b3;
}
</style>
```

**Image manipulation and filters:**
```html
<div class="image-editor">
  <h3>Canvas Image Editor</h3>
  <div class="editor-container">
    <canvas id="imageCanvas" width="500" height="300">
      Image editing features not available. 
      Please use a browser that supports canvas for image manipulation.
    </canvas>
    <div class="controls">
      <input type="file" id="imageUpload" accept="image/*">
      <button onclick="applyGrayscale()">Grayscale</button>
      <button onclick="applySepia()">Sepia</button>
      <button onclick="applyInvert()">Invert</button>
      <button onclick="resetImage()">Reset</button>
    </div>
  </div>
</div>

<script>
const canvas = document.getElementById('imageCanvas');
const ctx = canvas.getContext('2d');
const imageUpload = document.getElementById('imageUpload');

let originalImageData = null;

imageUpload.addEventListener('change', function(e) {
  const file = e.target.files[0];
  if (!file) return;
  
  const reader = new FileReader();
  reader.onload = function(event) {
    const img = new Image();
    img.onload = function() {
      // Scale image to fit canvas while maintaining aspect ratio
      const scale = Math.min(canvas.width / img.width, canvas.height / img.height);
      const width = img.width * scale;
      const height = img.height * scale;
      const x = (canvas.width - width) / 2;
      const y = (canvas.height - height) / 2;
      
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.drawImage(img, x, y, width, height);
      
      // Store original image data
      originalImageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
    };
    img.src = event.target.result;
  };
  reader.readAsDataURL(file);
});

function applyGrayscale() {
  if (!originalImageData) return;
  
  const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
  const data = imageData.data;
  
  for (let i = 0; i < data.length; i += 4) {
    const gray = data[i] * 0.299 + data[i + 1] * 0.587 + data[i + 2] * 0.114;
    data[i] = gray;     // red
    data[i + 1] = gray; // green
    data[i + 2] = gray; // blue
  }
  
  ctx.putImageData(imageData, 0, 0);
}

function applySepia() {
  if (!originalImageData) return;
  
  const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
  const data = imageData.data;
  
  for (let i = 0; i < data.length; i += 4) {
    const r = data[i];
    const g = data[i + 1];
    const b = data[i + 2];
    
    data[i] = Math.min(255, (r * 0.393) + (g * 0.769) + (b * 0.189));
    data[i + 1] = Math.min(255, (r * 0.349) + (g * 0.686) + (b * 0.168));
    data[i + 2] = Math.min(255, (r * 0.272) + (g * 0.534) + (b * 0.131));
  }
  
  ctx.putImageData(imageData, 0, 0);
}

function applyInvert() {
  if (!originalImageData) return;
  
  const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
  const data = imageData.data;
  
  for (let i = 0; i < data.length; i += 4) {
    data[i] = 255 - data[i];     // red
    data[i + 1] = 255 - data[i + 1]; // green
    data[i + 2] = 255 - data[i + 2]; // blue
  }
  
  ctx.putImageData(imageData, 0, 0);
}

function resetImage() {
  if (originalImageData) {
    ctx.putImageData(originalImageData, 0, 0);
  }
}
</script>

<style>
.image-editor {
  max-width: 500px;
  margin: 20px auto;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.image-editor h3 {
  margin-top: 0;
  text-align: center;
  color: #333;
}

#imageCanvas {
  border: 2px solid #ddd;
  border-radius: 4px;
  background: #f8f9fa;
  display: block;
  margin: 0 auto 15px;
}

.controls {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  justify-content: center;
}

.controls button {
  padding: 8px 16px;
  background: #6c757d;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.controls button:hover {
  background: #545b62;
}
</style>
```

**Accessible canvas with ARIA:**
```html
<div class="accessible-canvas">
  <h3 id="canvas-title">Interactive Bar Chart: Quarterly Revenue</h3>
  
  <canvas 
    id="accessibleChart" 
    width="600" height="300"
    aria-labelledby="canvas-title"
    aria-describedby="chart-description"
    role="img">
    This chart shows quarterly revenue data for 2024:
    Q1: $150,000 | Q2: $180,000 | Q3: $220,000 | Q4: $190,000
  </canvas>
  
  <div id="chart-description" class="sr-only">
    A bar chart displaying quarterly revenue for 2024. 
    The x-axis shows quarters and the y-axis shows revenue in thousands of dollars. 
    Q1: $150,000, Q2: $180,000, Q3: $220,000, Q4: $190,000.
  </div>
  
  <div class="data-table" aria-hidden="true">
    <table>
      <caption>Quarterly Revenue Data</caption>
      <thead>
        <tr>
          <th>Quarter</th>
          <th>Revenue</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>Q1</td><td>$150,000</td></tr>
        <tr><td>Q2</td><td>$180,000</td></tr>
        <tr><td>Q3</td><td>$220,000</td></tr>
        <tr><td>Q4</td><td>$190,000</td></tr>
      </tbody>
    </table>
  </div>
</div>

<script>
function drawAccessibleChart() {
  const canvas = document.getElementById('accessibleChart');
  const ctx = canvas.getContext('2d');
  
  const data = [150000, 180000, 220000, 190000];
  const labels = ['Q1', 'Q2', 'Q3', 'Q4'];
  const maxValue = Math.max(...data);
  
  const padding = 50;
  const chartWidth = canvas.width - padding * 2;
  const chartHeight = canvas.height - padding * 2;
  const barWidth = chartWidth / data.length * 0.6;
  const barSpacing = chartWidth / data.length * 0.4;
  
  // Clear and setup
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  
  // Draw bars
  data.forEach((value, index) => {
    const x = padding + (chartWidth / data.length) * index + barSpacing / 2;
    const barHeight = (value / maxValue) * chartHeight;
    const y = canvas.height - padding - barHeight;
    
    const gradient = ctx.createLinearGradient(x, y, x, y + barHeight);
    gradient.addColorStop(0, '#2ecc71');
    gradient.addColorStop(1, '#27ae60');
    
    ctx.fillStyle = gradient;
    ctx.fillRect(x, y, barWidth, barHeight);
    
    // Value labels
    ctx.fillStyle = '#2c3e50';
    ctx.font = 'bold 12px Arial';
    ctx.textAlign = 'center';
    ctx.fillText('$' + (value / 1000).toFixed(0) + 'K', x + barWidth / 2, y - 10);
    
    // Quarter labels
    ctx.fillStyle = '#7f8c8d';
    ctx.font = '14px Arial';
    ctx.fillText(labels[index], x + barWidth / 2, canvas.height - padding + 20);
  });
  
  // Draw axes
  ctx.strokeStyle = '#34495e';
  ctx.lineWidth = 2;
  
  // Y-axis
  ctx.beginPath();
  ctx.moveTo(padding, padding);
  ctx.lineTo(padding, canvas.height - padding);
  ctx.stroke();
  
  // X-axis
  ctx.beginPath();
  ctx.moveTo(padding, canvas.height - padding);
  ctx.lineTo(canvas.width - padding, canvas.height - padding);
  ctx.stroke();
}

window.addEventListener('load', drawAccessibleChart);
</script>

<style>
.accessible-canvas {
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
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

#accessibleChart {
  border: 1px solid #bdc3c7;
  border-radius: 4px;
  display: block;
  margin: 0 auto 20px;
}

.data-table {
  margin-top: 20px;
}

.data-table table {
  width: 100%;
  border-collapse: collapse;
}

.data-table th,
.data-table td {
  padding: 10px;
  text-align: left;
  border-bottom: 1px solid #ecf0f1;
}

.data-table th {
  background: #34495e;
  color: white;
}

.data-table caption {
  font-weight: bold;
  margin-bottom: 10px;
  color: #2c3e50;
}
</style>
```

**Multiple canvas contexts (2D and WebGL):**
```html
<div class="multi-context-demo">
  <h3>Canvas Rendering Contexts</h3>
  
  <div class="context-comparison">
    <div class="context-item">
      <h4>2D Context</h4>
      <canvas id="canvas2d" width="300" height="200">
        2D graphics not supported. This would show 2D shapes and text.
      </canvas>
    </div>
    
    <div class="context-item">
      <h4>WebGL Context</h4>
      <canvas id="canvasWebGL" width="300" height="200">
        WebGL not supported. This would show 3D graphics if available.
      </canvas>
    </div>
  </div>
</div>

<script>
// 2D Context Example
const canvas2d = document.getElementById('canvas2d');
const ctx2d = canvas2d.getContext('2d');

// Draw 2D shapes
ctx2d.fillStyle = '#3498db';
ctx2d.fillRect(50, 50, 100, 80);

ctx2d.fillStyle = '#e74c3c';
ctx2d.beginPath();
ctx2d.arc(200, 100, 40, 0, Math.PI * 2);
ctx2d.fill();

ctx2d.fillStyle = '#2c3e50';
ctx2d.font = '14px Arial';
ctx2d.fillText('2D Graphics', 100, 180);

// WebGL Context Example
const canvasWebGL = document.getElementById('canvasWebGL');
const gl = canvasWebGL.getContext('webgl') || canvasWebGL.getContext('experimental-webgl');

if (gl) {
  // Set clear color to dark blue
  gl.clearColor(0.1, 0.2, 0.4, 1.0);
  gl.clear(gl.COLOR_BUFFER_BIT);
  
  // Simple vertex shader
  const vsSource = `
    attribute vec4 aPosition;
    void main() {
      gl_Position = aPosition;
      gl_PointSize = 10.0;
    }
  `;
  
  // Simple fragment shader
  const fsSource = `
    void main() {
      gl_FragColor = vec4(1.0, 0.5, 0.0, 1.0);
    }
  `;
  
  // Compile shader
  function compileShader(source, type) {
    const shader = gl.createShader(type);
    gl.shaderSource(shader, source);
    gl.compileShader(shader);
    
    if (!gl.getShaderParameter(shader, gl.COMPILE_STATUS)) {
      console.error('Shader compilation error:', gl.getShaderInfoLog(shader));
      gl.deleteShader(shader);
      return null;
    }
    return shader;
  }
  
  const vertexShader = compileShader(vsSource, gl.VERTEX_SHADER);
  const fragmentShader = compileShader(fsSource, gl.FRAGMENT_SHADER);
  
  // Create program
  const program = gl.createProgram();
  gl.attachShader(program, vertexShader);
  gl.attachShader(program, fragmentShader);
  gl.linkProgram(program);
  
  if (!gl.getProgramParameter(program, gl.LINK_STATUS)) {
    console.error('Program linking error:', gl.getProgramInfoLog(program));
  }
  
  gl.useProgram(program);
  
  // Draw some points
  const positions = [
    0.0, 0.0,
    -0.5, 0.5,
    0.5, 0.5,
    -0.5, -0.5,
    0.5, -0.5
  ];
  
  const positionBuffer = gl.createBuffer();
  gl.bindBuffer(gl.ARRAY_BUFFER, positionBuffer);
  gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(positions), gl.STATIC_DRAW);
  
  const positionAttributeLocation = gl.getAttribLocation(program, "aPosition");
  gl.enableVertexAttribArray(positionAttributeLocation);
  gl.vertexAttribPointer(positionAttributeLocation, 2, gl.FLOAT, false, 0, 0);
  
  gl.drawArrays(gl.POINTS, 0, positions.length / 2);
} else {
  // WebGL not supported - show fallback
  const ctx = canvasWebGL.getContext('2d');
  ctx.fillStyle = '#95a5a6';
  ctx.font = '12px Arial';
  ctx.textAlign = 'center';
  ctx.fillText('WebGL not supported', 150, 100);
}
</script>

<style>
.multi-context-demo {
  max-width: 650px;
  margin: 20px auto;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.multi-context-demo h3 {
  text-align: center;
  margin-top: 0;
  color: #333;
}

.context-comparison {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-top: 20px;
}

.context-item {
  text-align: center;
}

.context-item h4 {
  margin-bottom: 10px;
  color: #555;
}

.context-item canvas {
  border: 2px solid #bdc3c7;
  border-radius: 4px;
  background: #ecf0f1;
}

@media (max-width: 650px) {
  .context-comparison {
    grid-template-columns: 1fr;
  }
}
</style>
```

---

## Notes

* **Rendering contexts**: 
  - `getContext('2d')` for 2D graphics
  - `getContext('webgl')` for 3D graphics (WebGL 1)
  - `getContext('webgl2')` for WebGL 2
  - `getContext('bitmaprenderer')` for ImageBitmap rendering
* **Accessibility considerations**:
  - Canvas content is not accessible by default
  - Provide meaningful fallback content
  - Use ARIA attributes (`aria-label`, `role`, etc.)
  - Consider providing alternative text-based representations
* **Performance optimization**:
  - Use `requestAnimationFrame` for smooth animations
  - Avoid frequent canvas state changes
  - Use offscreen canvases for complex operations
  - Consider Web Workers for heavy computations
* **Browser support**: 
  - Basic canvas: All modern browsers
  - WebGL: Most modern browsers (check compatibility)
  - Some advanced features may have limited support
* **Common issues**:
  - Forgetting to call `getContext()` before drawing
  - Mixing CSS dimensions with canvas coordinate space
  - Not handling high-DPI (retina) displays properly
  - Memory leaks from not clearing animations
* **Best practices**:
  - Always provide fallback content
  - Handle responsive sizing properly
  - Clean up animation frames when not needed
  - Use appropriate rendering contexts for different tasks
  - Test performance on target devices
* **Security considerations**:
  - Canvas content is subject to same-origin policy
  - `getImageData()` may throw for cross-origin images
  - Tainted canvases have restricted functionality
* **Mobile considerations**:
  - Touch events instead of mouse events
  - Performance limitations on older devices
  - High-DPI display handling
* **File formats**: Can export to PNG, JPEG, or WebP via `toDataURL()` or `toBlob()`

---
