# `<map>`

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

The `<map>` element defines an image map; a clickable region on an image that contains one or more areas defined by `<area>` elements. It creates interactive hotspots over images, allowing different parts of an image to link to different destinations or trigger different actions, effectively turning a static image into a navigational interface.

---

## Syntax & Variants

+ **Standard syntax**: `<map>...</map>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps one or more `<area>` elements
+ **No self-closing variant**: Must contain `<area>` elements
+ **HTML association**: Connected to `<img>` via `usemap` attribute

---

## Attributes

+ **Core attributes**:
  - `name` (required): Unique name identifier for the map, referenced by `<img>` elements
  - `id` (recommended): Should match `name` for compatibility and accessibility
+ **Global attributes**: `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No optional core attributes**: Only `name` is required for functionality

---

## Content Model

+ **Permitted content**:
  - Zero or more `<area>` elements (typically one or more)
  - Transparent content model (can contain flow content)
  - Any phrasing content or flow content as fallback
+ **Area elements**: Define the clickable regions within the image
+ **Fallback content**: Displayed if image map is not supported (rare in modern browsers)

---

## Context

+ **Valid parents**: Any element that accepts phrasing content or flow content
+ **Common locations**:
  - Within `<body>` as a direct child or within containers
  - Near the `<img>` elements that reference it
  - In technical documentation, geographic maps, or interactive diagrams
+ **Referenced by**: `<img>` elements via `usemap` attribute
+ **No nesting**: Cannot nest `<map>` elements

---

## Behavior and Semantics

+ **Default display**: No visual representation itself
+ **Interactive behavior**:
  - Creates invisible clickable regions over associated images
  - Areas respond to mouse clicks, touches, and keyboard navigation
  - Hover states can be styled with CSS
+ **Semantic meaning**:
  - Defines an image map structure
  - Screen readers may announce the presence of image maps
  - Provides context for complex image interactions
+ **Accessibility**: Can be challenging; requires careful area labeling and alternatives

---

## Examples

**Basic image map with rectangular areas:**
```html
<img src="office-map.jpg" alt="Office floor plan" usemap="#officemap">
<map name="officemap" id="officemap">
  <area shape="rect" coords="34,44,270,350" href="reception.html" alt="Reception Area">
  <area shape="rect" coords="290,172,333,250" href="kitchen.html" alt="Kitchen">
  <area shape="rect" coords="350,44,600,350" href="conference.html" alt="Conference Room">
</map>
```

**Geographic map with different shapes:**
```html
<img src="world-map.png" alt="World map with clickable regions" usemap="#worldmap">
<map name="worldmap" id="worldmap">
  <area shape="circle" coords="250,150,30" href="europe.html" alt="Europe region">
  <area shape="poly" coords="100,200,150,250,200,200,150,150" href="north-america.html" alt="North America">
  <area shape="rect" coords="350,300,450,400" href="australia.html" alt="Australia">
  <area shape="default" href="other-regions.html" alt="Other regions">
</map>
```

**Technical diagram with multiple areas:**
```html
<figure>
  <img src="computer-diagram.png" alt="Computer components diagram" usemap="#components">
  <figcaption>Figure 1: Computer system components - click areas for details</figcaption>
</figure>
<map name="components" id="components">
  <area shape="rect" coords="50,50,150,100" href="#cpu" alt="Central Processing Unit (CPU)">
  <area shape="rect" coords="200,50,300,100" href="#ram" alt="Random Access Memory (RAM)">
  <area shape="rect" coords="350,50,450,100" href="#storage" alt="Storage Devices">
  <area shape="circle" coords="400,200,25" href="#motherboard" alt="Motherboard">
  <area shape="poly" coords="100,150,150,200,200,150,150,100" href="#gpu" alt="Graphics Processing Unit">
</map>
```

**Interactive menu using image map:**
```html
<img src="restaurant-menu.png" alt="Restaurant menu with clickable items" usemap="#menu">
<map name="menu" id="menu">
  <area shape="rect" coords="0,0,200,50" href="#appetizers" alt="Appetizers section">
  <area shape="rect" coords="0,60,200,110" href="#entrees" alt="Main courses">
  <area shape="rect" coords="0,120,200,170" href="#desserts" alt="Desserts">
  <area shape="rect" coords="0,180,200,230" href="#beverages" alt="Beverages">
</map>
```

**Accessible image map with detailed descriptions:**
```html
<img src="organizational-chart.png" 
     alt="Company organizational chart showing management structure" 
     usemap="#orgchart">
<map name="orgchart" id="orgchart">
  <area shape="rect" coords="200,50,300,100" 
        href="ceo-profile.html" 
        alt="CEO: John Smith - Chief Executive Officer"
        title="View CEO profile and responsibilities">
  <area shape="rect" coords="100,120,200,170" 
        href="cto-profile.html" 
        alt="CTO: Maria Garcia - Chief Technology Officer"
        title="View CTO profile and technology initiatives">
  <area shape="rect" coords="300,120,400,170" 
        href="cfo-profile.html" 
        alt="CFO: David Chen - Chief Financial Officer"
        title="View CFO profile and financial reports">
</map>
```

**Image map with JavaScript interactions:**
```html
<img src="interactive-diagram.png" alt="Interactive product diagram" usemap="#productmap">
<map name="productmap" id="productmap">
  <area shape="circle" coords="100,100,20" href="#feature1" alt="Primary feature" 
        onmouseover="showTooltip('Wireless charging capability')" 
        onmouseout="hideTooltip()">
  <area shape="rect" coords="150,80,250,120" href="#feature2" alt="Secondary feature"
        onmouseover="showTooltip('High-resolution display with touch support')" 
        onmouseout="hideTooltip()">
  <area shape="poly" coords="300,100,350,150,400,100,350,50" href="#feature3" alt="Tertiary feature"
        onmouseover="showTooltip('Advanced camera system with optical zoom')" 
        onmouseout="hideTooltip()">
</map>

<div id="tooltip" style="display: none; position: absolute; background: #fff; border: 1px solid #ccc; padding: 5px;"></div>

<script>
function showTooltip(text) {
  const tooltip = document.getElementById('tooltip');
  tooltip.textContent = text;
  tooltip.style.display = 'block';
}

function hideTooltip() {
  document.getElementById('tooltip').style.display = 'none';
}
</script>
```

**Responsive image map with CSS styling:**
```html
<div class="image-map-container">
  <img src="responsive-diagram.svg" alt="Responsive technical diagram" usemap="#responsiveMap">
  <map name="responsiveMap" id="responsiveMap">
    <area shape="rect" coords="0,0,100,50" href="#section1" alt="Section 1" class="map-area">
    <area shape="rect" coords="110,0,210,50" href="#section2" alt="Section 2" class="map-area">
    <area shape="rect" coords="220,0,320,50" href="#section3" alt="Section 3" class="map-area">
  </map>
</div>

<style>
.image-map-container {
  position: relative;
  max-width: 100%;
}

.image-map-container img {
  width: 100%;
  height: auto;
}

/* Style the hover states of areas */
area.map-area:hover {
  cursor: pointer;
}
</style>
```

---

## Notes

* **Coordinate system**: Coordinates are relative to the image, with (0,0) at top-left corner
* **Shape types**:
  - `rect`: Rectangle defined by x1,y1,x2,y2 (top-left and bottom-right corners)
  - `circle`: Circle defined by center-x,center-y,radius
  - `poly`: Polygon defined by x1,y1,x2,y2,...,xn,yn (three or more points)
  - `default`: Entire image (must be last area if used)
* **Accessibility challenges**:
  - Image maps can be difficult for screen reader users
  - Always provide meaningful `alt` text for each area
  - Consider providing a text-based alternative navigation
  - Ensure adequate color contrast and target size
* **Responsive limitations**: 
  - Fixed coordinates don't scale with responsive images
  - JavaScript solutions needed for responsive image maps
  - Consider SVG as a modern alternative
* **Browser support**: Well-supported in all modern browsers
* **Common pitfalls**:
  - Forgetting to match `name` and `id` attributes
  - Using incorrect coordinate values
  - Not providing adequate fallback for non-visual users
  - Creating areas that are too small for touch devices
  - Overlapping areas causing unpredictable behavior
* **Modern alternatives**:
  - SVG with `<a>` elements for clickable regions
  - CSS image sprites with positioned links
  - JavaScript-based interactive images
  - HTML/CSS grid layouts over images
* **SEO considerations**: Search engines can follow links in image maps, but text alternatives are important
* **Mobile usability**: Ensure touch targets are at least 44×44 pixels for mobile accessibility

---
