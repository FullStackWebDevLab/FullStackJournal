# `<svg>`

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

The `<svg>` element represents the root container for Scalable Vector Graphics (SVG) content. It defines a coordinate system and viewport for vector-based graphical content that can scale infinitely without loss of quality. SVG graphics are resolution-independent, accessible, and can be styled with CSS, making them ideal for icons, logos, diagrams, data visualizations, and complex illustrations that need to maintain crisp appearance across different devices and screen sizes.

---

## Syntax and Variants

+ **Standard syntax**: `<svg>...</svg>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Can contain other SVG elements and shapes
+ **Inline SVG**: Embedded directly in HTML documents
+ **External SVG**: Can be linked as separate `.svg` files
+ **Self-contained**: Can function as independent XML documents

---

## Attributes

+ **Core attributes**:
  - `width` and `height`: Define the viewport dimensions (CSS pixels)
  - `viewBox`: Defines the coordinate system and aspect ratio (`min-x min-y width height`)
  - `preserveAspectRatio`: Controls scaling behavior when aspect ratios don't match
  - `xmlns`: XML namespace declaration (required for standalone SVG)

+ **Presentation attributes**:
  - `fill`: Color for interior of shapes
  - `stroke`: Color for outlines
  - `stroke-width`: Thickness of outlines
  - `opacity`: Transparency level

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `role`, etc.

+ **HTML integration**: Supports most HTML global attributes when embedded in HTML

---

## Content Model

+ **Permitted content**: Any SVG elements and descriptive elements
+ **Graphic elements**:
  - Basic shapes: `<rect>`, `<circle>`, `<ellipse>`, `<line>`, `<polygon>`, `<polyline>`
  - Paths: `<path>` for complex shapes
  - Text: `<text>`, `<tspan>`
  - Images: `<image>`
  - Groups: `<g>`
+ **Structural elements**:
  - `<defs>` for reusable definitions
  - `<symbol>` for reusable symbols
  - `<use>` for reusing elements
+ **Interactive elements**: `<a>`, `<script>`
+ **Metadata**: `<title>`, `<desc>`, `<metadata>`

---

## Context

+ **Valid contexts**:
  - Embedded directly in HTML5 documents
  - As standalone `.svg` files
  - Within other SVG elements (nested SVGs)
  - As CSS background images
+ **Document embedding**: Can be inline in HTML or external via `<img>`, `<object>`, `<iframe>`
+ **Parent restrictions**: No specific restrictions in HTML5
+ **Nesting**: SVGs can contain other SVGs for complex compositions

---

## Behavior and Semantics

+ **Default display**: Inline-block element (`display: inline-block`)
+ **Coordinate system**: Uses Cartesian coordinate system with (0,0) at top-left
+ **Scaling behavior**: Infinitely scalable without quality loss
+ **Rendering**: Vector-based rendering through DOM
+ **Semantic meaning**:
  - Represents vector graphic content
  - Can be made accessible with proper ARIA attributes
  - Screen readers can interpret with proper labeling
+ **Interactivity**: Supports JavaScript events and CSS animations
+ **Performance**: Generally lightweight compared to raster images

---

## Examples

**Basic SVG with a circle:**
```html
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" fill="blue" />
</svg>
```

**SVG with viewBox for responsive scaling:**
```html
<svg width="200" height="200" viewBox="0 0 100 100">
  <rect x="10" y="10" width="80" height="80" fill="green" />
</svg>
```

**Accessible SVG with title and description:**
```html
<svg width="120" height="120" role="img" aria-labelledby="svg-title svg-desc">
  <title id="svg-title">Company Logo</title>
  <desc id="svg-desc">A circular logo with the company initials AC</desc>
  <circle cx="60" cy="60" r="50" fill="#3498db" />
  <text x="60" y="65" text-anchor="middle" fill="white" font-size="24">AC</text>
</svg>
```

**Styled SVG with CSS classes:**
```html
<svg width="150" height="150" class="icon-button">
  <circle class="button-background" cx="75" cy="75" r="70" />
  <polygon class="button-icon" points="55,55 95,75 55,95" />
</svg>

<style>
.icon-button {
  cursor: pointer;
  transition: transform 0.2s;
}

.icon-button:hover {
  transform: scale(1.1);
}

.button-background {
  fill: #e74c3c;
  stroke: #c0392b;
  stroke-width: 2;
}

.button-icon {
  fill: white;
}
</style>
```

**Complex logo with multiple shapes:**
```html
<svg width="200" height="100" viewBox="0 0 200 100">
  <defs>
    <linearGradient id="logoGradient" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#667eea" />
      <stop offset="100%" stop-color="#764ba2" />
    </linearGradient>
  </defs>
  
  <rect x="10" y="10" width="180" height="80" fill="url(#logoGradient)" rx="10" />
  <text x="100" y="60" text-anchor="middle" fill="white" font-family="Arial" font-size="24" font-weight="bold">
    LOGO
  </text>
</svg>
```

**Interactive SVG with JavaScript:**
```html
<svg width="300" height="200" id="interactive-svg">
  <rect id="clickable-rect" x="50" y="50" width="200" height="100" fill="#3498db" />
  <text x="150" y="110" text-anchor="middle" fill="white" font-size="16">Click Me!</text>
</svg>

<script>
document.getElementById('clickable-rect').addEventListener('click', function() {
  this.setAttribute('fill', '#e74c3c');
  alert('SVG element clicked!');
});
</script>
```

**Data visualization chart:**
```html
<svg width="400" height="300" viewBox="0 0 400 300" class="bar-chart">
  <title>Monthly Sales Data</title>
  
  <!-- Axes -->
  <line x1="50" y1="250" x2="350" y2="250" stroke="#333" stroke-width="2" />
  <line x1="50" y1="250" x2="50" y2="50" stroke="#333" stroke-width="2" />
  
  <!-- Bars -->
  <rect x="70" y="150" width="40" height="100" fill="#3498db">
    <title>January: $10,000</title>
  </rect>
  <rect x="130" y="100" width="40" height="150" fill="#2ecc71">
    <title>February: $15,000</title>
  </rect>
  <rect x="190" y="80" width="40" height="170" fill="#e74c3c">
    <title>March: $17,000</title>
  </rect>
  <rect x="250" y="120" width="40" height="130" fill="#f39c12">
    <title>April: $13,000</title>
  </rect>
  <rect x="310" y="180" width="40" height="70" fill="#9b59b6">
    <title>May: $7,000</title>
  </rect>
  
  <!-- Labels -->
  <text x="90" y="270" text-anchor="middle" font-size="12">Jan</text>
  <text x="150" y="270" text-anchor="middle" font-size="12">Feb</text>
  <text x="210" y="270" text-anchor="middle" font-size="12">Mar</text>
  <text x="270" y="270" text-anchor="middle" font-size="12">Apr</text>
  <text x="330" y="270" text-anchor="middle" font-size="12">May</text>
</svg>
```

**Animated SVG with CSS:**
```html
<svg width="200" height="200" class="loading-spinner">
  <circle class="spinner-track" cx="100" cy="100" r="80" />
  <circle class="spinner-fill" cx="100" cy="100" r="80" />
</svg>

<style>
.loading-spinner {
  animation: rotate 2s linear infinite;
}

.spinner-track {
  fill: none;
  stroke: #f0f0f0;
  stroke-width: 8;
}

.spinner-fill {
  fill: none;
  stroke: #3498db;
  stroke-width: 8;
  stroke-dasharray: 200;
  stroke-dashoffset: 200;
  animation: dash 1.5s ease-in-out infinite;
}

@keyframes rotate {
  100% { transform: rotate(360deg); }
}

@keyframes dash {
  0% { stroke-dashoffset: 200; }
  50% { stroke-dashoffset: 50; }
  100% { stroke-dashoffset: 200; }
}
</style>
```

**SVG icon system with symbols:**
```html
<svg style="display: none;">
  <defs>
    <symbol id="home-icon" viewBox="0 0 24 24">
      <path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/>
    </symbol>
    
    <symbol id="user-icon" viewBox="0 0 24 24">
      <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
    </symbol>
    
    <symbol id="settings-icon" viewBox="0 0 24 24">
      <path d="M19.14 12.94c.04-.3.06-.61.06-.94 0-.32-.02-.64-.07-.94l2.03-1.58c.18-.14.23-.41.12-.61l-1.92-3.32c-.12-.22-.37-.29-.59-.22l-2.39.96c-.5-.38-1.03-.7-1.62-.94l-.36-2.54c-.04-.24-.24-.41-.48-.41h-3.84c-.24 0-.43.17-.47.41l-.36 2.54c-.59.24-1.13.57-1.62.94l-2.39-.96c-.22-.08-.47 0-.59.22L2.74 8.87c-.12.21-.08.47.12.61l2.03 1.58c-.05.3-.09.63-.09.94s.02.64.07.94l-2.03 1.58c-.18.14-.23.41-.12.61l1.92 3.32c.12.22.37.29.59.22l2.39-.96c.5.38 1.03.7 1.62.94l.36 2.54c.05.24.24.41.48.41h3.84c.24 0 .44-.17.47-.41l.36-2.54c.59-.24 1.13-.56 1.62-.94l2.39.96c.22.08.47 0 .59-.22l1.92-3.32c.12-.22.07-.47-.12-.61l-2.01-1.58zM12 15.6c-1.98 0-3.6-1.62-3.6-3.6s1.62-3.6 3.6-3.6 3.6 1.62 3.6 3.6-1.62 3.6-3.6 3.6z"/>
    </symbol>
  </defs>
</svg>

<div class="icon-grid">
  <svg class="icon" aria-label="Home">
    <use href="#home-icon" />
  </svg>
  
  <svg class="icon" aria-label="User Profile">
    <use href="#user-icon" />
  </svg>
  
  <svg class="icon" aria-label="Settings">
    <use href="#settings-icon" />
  </svg>
</div>

<style>
.icon-grid {
  display: flex;
  gap: 20px;
  padding: 20px;
}

.icon {
  width: 48px;
  height: 48px;
  fill: #666;
  transition: fill 0.3s;
}

.icon:hover {
  fill: #3498db;
}
</style>
```

**Responsive SVG that scales with container:**
```html
<div class="responsive-container">
  <svg viewBox="0 0 100 50" preserveAspectRatio="xMidYMid meet">
    <rect x="10" y="10" width="80" height="30" fill="#3498db" rx="5" />
    <text x="50" y="30" text-anchor="middle" fill="white" font-size="8">Responsive SVG</text>
  </svg>
</div>

<style>
.responsive-container {
  width: 100%;
  max-width: 600px;
  border: 1px solid #ddd;
  padding: 20px;
}

.responsive-container svg {
  width: 100%;
  height: auto;
}
</style>
```

**SVG with filters and effects:**
```html
<svg width="300" height="200">
  <defs>
    <filter id="shadow" x="-20%" y="-20%" width="140%" height="140%">
      <feDropShadow dx="2" dy="2" stdDeviation="3" flood-color="rgba(0,0,0,0.5)"/>
    </filter>
    
    <linearGradient id="gradient" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#ff6b6b" />
      <stop offset="100%" stop-color="#4ecdc4" />
    </linearGradient>
  </defs>
  
  <rect x="50" y="50" width="200" height="100" rx="10" 
        fill="url(#gradient)" filter="url(#shadow)" />
  
  <text x="150" y="110" text-anchor="middle" fill="white" 
        font-family="Arial" font-size="20" font-weight="bold">
    Styled Box
  </text>
</svg>
```

**SVG map with interactive regions:**
```html
<svg width="400" height="300" viewBox="0 0 400 300" class="interactive-map">
  <title>Office Floor Plan</title>
  
  <!-- Conference Room -->
  <rect id="conference-room" x="50" y="50" width="120" height="80" 
        fill="#3498db" stroke="#2980b9" stroke-width="2" />
  <text x="110" y="95" text-anchor="middle" fill="white" font-size="12">
    Conference
  </text>
  
  <!-- Kitchen -->
  <rect id="kitchen" x="200" y="50" width="80" height="60" 
        fill="#2ecc71" stroke="#27ae60" stroke-width="2" />
  <text x="240" y="85" text-anchor="middle" fill="white" font-size="12">
    Kitchen
  </text>
  
  <!-- Office Area -->
  <rect id="office-area" x="50" y="150" width="230" height="100" 
        fill="#e74c3c" stroke="#c0392b" stroke-width="2" />
  <text x="165" y="205" text-anchor="middle" fill="white" font-size="12">
    Office Space
  </text>
</svg>

<script>
// Add interactivity to map areas
const areas = document.querySelectorAll('.interactive-map rect');
areas.forEach(area => {
  area.addEventListener('mouseenter', function() {
    this.style.fill = '#f1c40f';
  });
  
  area.addEventListener('mouseleave', function() {
    const colors = {
      'conference-room': '#3498db',
      'kitchen': '#2ecc71', 
      'office-area': '#e74c3c'
    };
    this.style.fill = colors[this.id];
  });
  
  area.addEventListener('click', function() {
    alert(`You clicked the ${this.id.replace('-', ' ')}`);
  });
});
</script>
```

**SVG with text on a path:**
```html
<svg width="400" height="200">
  <defs>
    <path id="text-path" d="M 50,150 C 100,50 300,50 350,150" 
          fill="none" stroke="none" />
  </defs>
  
  <!-- Background path for reference -->
  <path d="M 50,150 C 100,50 300,50 350,150" 
        fill="none" stroke="#ddd" stroke-width="2" />
  
  <!-- Text following the path -->
  <text fill="#3498db" font-family="Arial" font-size="20" font-weight="bold">
    <textPath href="#text-path" startOffset="50%" text-anchor="middle">
      Curved Text in SVG
    </textPath>
  </text>
</svg>
```

**SVG clip-path example:**
```html
<svg width="300" height="300">
  <defs>
    <clipPath id="circle-clip">
      <circle cx="150" cy="150" r="100" />
    </clipPath>
  </defs>
  
  <!-- Background image clipped to circle -->
  <image href="https://picsum.photos/300/300" width="300" height="300" 
         clip-path="url(#circle-clip)" />
  
  <!-- Border around clipped area -->
  <circle cx="150" cy="150" r="100" fill="none" stroke="#333" stroke-width="3" />
</svg>
```

**SVG with masking:**
```html
<svg width="400" height="200">
  <defs>
    <mask id="gradient-mask">
      <linearGradient id="mask-gradient" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" stop-color="white" stop-opacity="1" />
        <stop offset="100%" stop-color="white" stop-opacity="0" />
      </linearGradient>
      <rect x="0" y="0" width="400" height="200" fill="url(#mask-gradient)" />
    </mask>
  </defs>
  
  <rect x="0" y="0" width="400" height="200" 
        fill="url(#gradient)" mask="url(#gradient-mask)" />
  
  <defs>
    <linearGradient id="gradient">
      <stop offset="0%" stop-color="#667eea" />
      <stop offset="100%" stop-color="#764ba2" />
    </linearGradient>
  </defs>
</svg>
```

**SVG animation with SMIL (deprecated but shown for reference):**
```html
<svg width="200" height="200">
  <circle cx="100" cy="100" r="50" fill="#3498db">
    <animate attributeName="r" from="10" to="50" dur="2s" repeatCount="indefinite" />
    <animate attributeName="fill" values="#3498db;#e74c3c;#2ecc71;#3498db" 
             dur="3s" repeatCount="indefinite" />
  </circle>
</svg>
```

**Modern SVG animation with CSS:**
```html
<svg width="200" height="200" class="pulsing-circle">
  <circle cx="100" cy="100" r="40" class="circle-element" />
</svg>

<style>
.pulsing-circle .circle-element {
  fill: #3498db;
  animation: pulse 2s ease-in-out infinite;
  transform-origin: center;
}

@keyframes pulse {
  0% {
    transform: scale(1);
    fill: #3498db;
  }
  50% {
    transform: scale(1.2);
    fill: #e74c3c;
  }
  100% {
    transform: scale(1);
    fill: #3498db;
  }
}
</style>
```

---

## Notes

* **Accessibility considerations**:
  - Always include `<title>` and `<desc>` elements for complex graphics
  - Use `aria-label` or `aria-labelledby` for simple graphics
  - Ensure proper color contrast for text within SVGs
  - Provide text alternatives for informational graphics
  - Use `role="img"` for decorative SVGs

* **Browser support**: Excellent support in all modern browsers
* **Common mistakes**:
  - Forgetting `xmlns` attribute in standalone SVG files
  - Not providing accessible labels for meaningful graphics
  - Using raster images within SVG when vector alternatives exist
  - Overlooking viewBox for responsive behavior
  - Creating overly complex SVGs that impact performance

* **Performance considerations**:
  - Complex paths with many points can impact rendering performance
  - Filters and effects can be computationally expensive
  - Consider simplifying complex illustrations
  - Use CSS transforms for animations when possible

* **Best practices**:
  - Use meaningful IDs for reusable elements
  - Optimize SVG files by removing unnecessary metadata
  - Use CSS for styling when possible for maintainability
  - Provide fallbacks for older browsers when using advanced features
  - Test across different screen sizes and resolutions

* **SEO implications**:
  - Text within SVG is indexable by search engines
  - Properly labeled SVGs can contribute to accessibility scores
  - Consider using structured data for complex diagrams

* **Export optimization**:
  - Use tools like SVGO to optimize file size
  - Remove editor metadata and comments
  - Simplify paths when possible
  - Consider gzipping for web delivery

* **Security considerations**:
  - Be cautious with external resources in SVGs
  - Sanitize user-generated SVG content
  - Consider Content Security Policy for inline SVGs

* **Progressive enhancement**:
  - Provide PNG fallbacks for critical images
  - Use feature detection for advanced SVG features
  - Consider loading complex SVGs lazily

* **Animation approaches**:
  - CSS animations: Good for simple transformations
  - SMIL: Native SVG animation (deprecated in some browsers)
  - JavaScript: Most flexible for complex interactions
  - Web Animations API: Modern standard for complex animations

---
