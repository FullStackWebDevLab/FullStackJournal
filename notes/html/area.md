# `<area>`

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

The `<area>` element defines a clickable/hotspot region within an image map (`<map>` element). It specifies the shape, coordinates, and behavior of interactive areas over an image, allowing different parts of an image to have separate hyperlinks, JavaScript actions, or other interactive behaviors while maintaining the visual integrity of the base image.

---

## Syntax & Variants

+ **Standard syntax**: `<area>` (void element)
+ **Void element**: No closing tag required
+ **Self-closing variants**:
  - HTML5: `<area>`
  - XHTML: `<area />` or `<area></area>`
+ **Child element**: Always used within a `<map>` element
+ **No standalone use**: Must be contained within a `<map>`

---

## Attributes

+ **Core attributes**:
  - `shape` (optional): Shape of the area (`rect`, `circle`, `poly`, `default`)
  - `coords` (optional): Coordinates defining the area shape
  - `href` (optional): URL the area links to
  - `alt` (required if `href` present): Alternative text for the area
  - `target` (optional): Where to open linked resource
  - `download` (optional): Prompts to download linked resource
  - `rel` (optional): Relationship between current and linked document
  - `ping` (optional): URLs to notify when link is followed
+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **Deprecated attributes**:
  - `nohref` (use without `href` instead)

---

## Content Model

+ **Empty element**: Must not contain any content
+ **No children permitted**: Cannot contain text or other elements
+ **Void element category**: Defined as having no content model in HTML specification
+ **No fallback content**: Relies on parent `<map>` for structural context

---

## Context

+ **Required parent**: Must be a direct child of a `<map>` element
+ **Sibling relationships**: Multiple `<area>` elements can exist within one `<map>`
+ **Order significance**: For `shape="default"`, must be the last `<area>` in the `<map>`
+ **Referenced indirectly**: Connected to `<img>` via parent `<map>`'s `name` attribute

---

## Behavior and Semantics

+ **Default display**: No visual representation itself
+ **Interactive behavior**:
  - Creates invisible clickable region over associated image
  - Supports mouse clicks, touch events, and keyboard navigation
  - Can trigger hyperlinks, JavaScript actions, or other interactions
+ **Visual feedback**:
  - Browser shows link cursor (pointer) when hovering over area
  - No inherent visual styling; requires CSS for custom appearance
  - Status bar may show link URL in some browsers
+ **Semantic meaning**:
  - Defines an interactive region within an image map
  - Screen readers announce based on `alt` text and role
  - Provides context for image-based navigation
+ **Accessibility**: Critical to provide meaningful `alt` text for each interactive area

---

## Examples

**Basic rectangular areas in a navigation bar:**
```html
<img src="navbar.png" alt="Website navigation" usemap="#navmap">
<map name="navmap">
  <area shape="rect" coords="0,0,100,50" href="home.html" alt="Home page">
  <area shape="rect" coords="100,0,200,50" href="about.html" alt="About us">
  <area shape="rect" coords="200,0,300,50" href="contact.html" alt="Contact information">
</map>
```

**Geographic map with different shapes:**
```html
<img src="world-map.png" alt="World map" usemap="#world">
<map name="world">
  <area shape="circle" coords="250,150,30" href="europe.html" alt="Europe region">
  <area shape="poly" coords="100,200,150,250,200,200,150,150" href="north-america.html" alt="North America">
  <area shape="rect" coords="350,300,450,400" href="australia.html" alt="Australia">
  <area shape="default" href="other-regions.html" alt="Other regions not specified">
</map>
```

**Technical diagram with detailed coordinates:**
```html
<img src="computer-parts.png" alt="Computer components diagram" usemap="#components">
<map name="components">
  <area shape="rect" coords="50,50,150,100" href="#cpu" alt="Central Processing Unit - brain of the computer">
  <area shape="rect" coords="200,50,300,100" href="#ram" alt="Random Access Memory - temporary data storage">
  <area shape="circle" coords="400,200,25" href="#motherboard" alt="Motherboard - main circuit board">
  <area shape="poly" coords="100,150,150,200,200,150,150,100" href="#gpu" alt="Graphics Processing Unit - handles visual output">
</map>
```

**Area with JavaScript action instead of link:**
```html
<img src="control-panel.png" alt="Interactive control panel" usemap="#controls">
<map name="controls">
  <area shape="circle" coords="100,100,20" alt="Play button" onclick="playAudio()">
  <area shape="circle" coords="150,100,20" alt="Pause button" onclick="pauseAudio()">
  <area shape="circle" coords="200,100,20" alt="Stop button" onclick="stopAudio()">
</map>
```

**Accessible image map with comprehensive attributes:**
```html
<img src="org-chart.png" alt="Company organizational chart" usemap="#orgchart">
<map name="orgchart">
  <area shape="rect" coords="200,50,300,100" 
        href="ceo-profile.html" 
        alt="CEO: Sarah Johnson - Chief Executive Officer"
        title="View CEO profile and responsibilities"
        target="_blank"
        rel="noopener"
        data-department="executive">
  
  <area shape="rect" coords="100,120,200,170" 
        href="cto-profile.html" 
        alt="CTO: Michael Chen - Chief Technology Officer"
        title="View CTO profile and technology roadmap"
        target="_blank"
        rel="noopener"
        data-department="technology">
  
  <area shape="rect" coords="300,120,400,170" 
        href="cfo-profile.html" 
        alt="CFO: Maria Garcia - Chief Financial Officer" 
        title="View CFO profile and financial reports"
        target="_blank"
        rel="noopener"
        data-department="finance">
</map>
```

**Responsive-friendly area with percentage coordinates:**
```html
<img src="product-diagram.png" alt="Product features diagram" usemap="#productmap" class="responsive-image">
<map name="productmap">
  <area shape="rect" coords="0%,0%,25%,100%" href="#feature1" alt="Primary feature set">
  <area shape="rect" coords="25%,0%,50%,100%" href="#feature2" alt="Secondary features">
  <area shape="rect" coords="50%,0%,75%,100%" href="#feature3" alt="Advanced capabilities">
  <area shape="rect" coords="75%,0%,100%,100%" href="#feature4" alt="Support and maintenance">
</map>
```

**Area with download attribute and multiple actions:**
```html
<img src="document-icons.png" alt="Document download options" usemap="#documents">
<map name="documents">
  <area shape="rect" coords="0,0,100,50" 
        href="report.pdf" 
        download="annual-report.pdf"
        alt="Download PDF version of annual report">
  
  <area shape="rect" coords="100,0,200,50" 
        href="report.docx" 
        download="annual-report.docx"
        alt="Download Word document version">
  
  <area shape="rect" coords="200,0,300,50" 
        href="report.html" 
        alt="View report in browser">
</map>
```

**Complex polygon area for irregular shapes:**
```html
<img src="floor-plan.png" alt="Office floor plan" usemap="#floorplan">
<map name="floorplan">
  <area shape="poly" 
        coords="50,75,100,50,150,75,150,125,100,150,50,125" 
        href="conference-room.html" 
        alt="Hexagonal conference room with 6-person capacity">
  
  <area shape="poly" 
        coords="200,100,250,75,300,100,300,150,250,175,200,150" 
        href="break-room.html" 
        alt="Break room with kitchen facilities and seating">
</map>
```

---

## Notes

* **Coordinate systems**:
  - `rect`: x1,y1,x2,y2 (top-left to bottom-right corners)
  - `circle`: center-x,center-y,radius
  - `poly`: x1,y1,x2,y2,x3,y3,... (minimum 3 points for triangle)
  - Coordinates are image-relative, with (0,0) at top-left
* **Shape default**: If `shape` omitted, defaults to `rect`
* **Accessibility requirements**:
  - `alt` attribute required when `href` is present
  - Provide meaningful descriptions, not just "click here"
  - Ensure adequate target size (minimum 44×44px for touch)
  - Consider text alternatives for complex image maps
* **Browser support**: Well-supported but with some behavioral variations
* **Common pitfalls**:
  - Missing `alt` text for linked areas
  - Incorrect coordinate values
  - Overlapping areas causing unpredictable behavior
  - Areas too small for reliable interaction
  - Not testing with keyboard navigation
* **Responsive challenges**:
  - Fixed coordinates don't scale with responsive images
  - JavaScript solutions needed for dynamic coordinate adjustment
  - Consider SVG as a more responsive alternative
* **SEO considerations**: Search engines can follow links in image maps
* **Performance**: Lightweight, but complex polygons with many points may impact rendering
* **Mobile usability**: Touch targets should be appropriately sized and spaced
* **Deprecated patterns**: Avoid `nohref`; use without `href` attribute instead for non-linked areas

---
