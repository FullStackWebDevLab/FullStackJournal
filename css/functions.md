# CSS Functions Complete Reference

## Introduction

CSS functions are built-in statements that perform specific data processing or calculations and return a value for use in CSS properties. Functions follow the syntax `function-name(arguments)` where arguments are separated by commas or spaces depending on the function.

---

## Transform Functions

Transform functions modify the appearance and position of elements. They are used with the `transform` property.

### Translation Functions

**`translateX()`** - Moves an element horizontally along the x-axis.
```css
transform: translateX(50px);
```

**`translateY()`** - Moves an element vertically along the y-axis.
```css
transform: translateY(100px);
```

**`translateZ()`** - Moves an element along the z-axis in 3D space.
```css
transform: translateZ(20px);
```

**`translate()`** - Moves an element on the 2D plane using x and y coordinates.
```css
transform: translate(50px, 100px);
```

**`translate3d()`** - Moves an element in 3D space using x, y, and z coordinates.
```css
transform: translate3d(50px, 100px, 20px);
```

### Rotation Functions

**`rotateX()`** - Rotates an element around the horizontal x-axis.
```css
transform: rotateX(45deg);
```

**`rotateY()`** - Rotates an element around the vertical y-axis.
```css
transform: rotateY(45deg);
```

**`rotateZ()`** - Rotates an element around the z-axis.
```css
transform: rotateZ(45deg);
```

**`rotate()`** - Rotates an element around a fixed point on the 2D plane.
```css
transform: rotate(45deg);
```

**`rotate3d()`** - Rotates an element around a fixed axis in 3D space.
```css
transform: rotate3d(1, 1, 0, 45deg);
```

### Scaling Functions

**`scaleX()`** - Changes the width of an element.
```css
transform: scaleX(1.5);
```

**`scaleY()`** - Changes the height of an element.
```css
transform: scaleY(1.5);
```

**`scaleZ()`** - Changes the depth of an element along the z-axis.
```css
transform: scaleZ(2);
```

**`scale()`** - Changes the size of an element on the 2D plane.
```css
transform: scale(1.5, 2);
```

**`scale3d()`** - Changes the size of an element in 3D space.
```css
transform: scale3d(1.5, 2, 1);
```

### Skew Functions

**`skewX()`** - Tilts an element horizontally.
```css
transform: skewX(20deg);
```

**`skewY()`** - Tilts an element vertically.
```css
transform: skewY(20deg);
```

**`skew()`** - Tilts an element on the 2D plane.
```css
transform: skew(20deg, 10deg);
```

### Matrix Functions

**`matrix()`** - Describes a 2D transformation using a transformation matrix.
```css
transform: matrix(1, 0, 0, 1, 0, 0);
```

**`matrix3d()`** - Describes a 3D transformation using a 4×4 transformation matrix.
```css
transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1);
```

### Perspective Function

**`perspective()`** - Sets the distance between the viewer and the z=0 plane.
```css
transform: perspective(500px);
```

---

## Math Functions

Math functions perform calculations on numeric values.

### Basic Arithmetic

**`calc()`** - Performs mathematical calculations on numeric values.
```css
width: calc(100% - 50px);
```

**`calc-size()`** - Performs calculations on intrinsic size values like `auto`, `fit-content`, and `max-content`.
```css
width: calc-size(auto, size + 20px);
```

### Comparison Functions

**`min()`** - Returns the smallest value from a list of values.
```css
width: min(50%, 400px);
```

**`max()`** - Returns the largest value from a list of values.
```css
width: max(200px, 50%);
```

**`clamp()`** - Returns a value between a minimum and maximum range.
```css
font-size: clamp(1rem, 2vw, 2rem);
```

### Stepped Value Functions

**`round()`** - Calculates a rounded number based on a rounding strategy.
```css
width: round(nearest, 100px, 10px);
```

**`mod()`** - Calculates a modulus with the same sign as the divisor.
```css
width: mod(18px, 5px);
```

**`rem()`** - Calculates a remainder with the same sign as the dividend.
```css
width: rem(18px, 5px);
```

**`progress()`** - Calculates the position of a value between a start and end value as a number between 0 and 1.
```css
opacity: progress(var(--scroll), 0%, 100%);
```

### Trigonometric Functions

**`sin()`** - Calculates the trigonometric sine of a number.
```css
transform: rotate(sin(45deg));
```

**`cos()`** - Calculates the trigonometric cosine of a number.
```css
transform: rotate(cos(45deg));
```

**`tan()`** - Calculates the trigonometric tangent of a number.
```css
transform: rotate(tan(45deg));
```

**`asin()`** - Calculates the inverse sine of a number.
```css
transform: rotate(asin(0.5));
```

**`acos()`** - Calculates the inverse cosine of a number.
```css
transform: rotate(acos(0.5));
```

**`atan()`** - Calculates the inverse tangent of a number.
```css
transform: rotate(atan(1));
```

**`atan2()`** - Calculates the inverse tangent of two numbers in a plane.
```css
transform: rotate(atan2(1, 1));
```

### Exponential Functions

**`pow()`** - Raises a base to a power.
```css
width: calc(pow(2, 3) * 10px);
```

**`sqrt()`** - Calculates the square root of a number.
```css
width: calc(sqrt(144) * 1px);
```

**`hypot()`** - Calculates the square root of the sum of squares of its arguments.
```css
width: hypot(3px, 4px);
```

**`log()`** - Calculates the logarithm of a number.
```css
opacity: log(10);
```

**`exp()`** - Calculates e raised to a power.
```css
opacity: exp(1);
```

### Sign-Related Functions

**`abs()`** - Returns the absolute value of a number.
```css
margin: abs(-20px);
```

**`sign()`** - Returns the sign of a number (positive or negative).
```css
transform: scale(sign(-1));
```

---

## Filter Functions

Filter functions apply visual effects to elements. They are used with the `filter` and `backdrop-filter` properties.

**`blur()`** - Applies a Gaussian blur effect.
```css
filter: blur(5px);
```

**`brightness()`** - Adjusts the brightness of an element.
```css
filter: brightness(150%);
```

**`contrast()`** - Adjusts the contrast of an element.
```css
filter: contrast(200%);
```

**`drop-shadow()`** - Applies a drop shadow effect.
```css
filter: drop-shadow(2px 2px 4px rgba(0, 0, 0, 0.5));
```

**`grayscale()`** - Converts an element to grayscale.
```css
filter: grayscale(100%);
```

**`hue-rotate()`** - Rotates the hue of colors in an element.
```css
filter: hue-rotate(90deg);
```

**`invert()`** - Inverts the colors of an element.
```css
filter: invert(100%);
```

**`opacity()`** - Sets the transparency level of an element.
```css
filter: opacity(50%);
```

**`saturate()`** - Adjusts the color saturation of an element.
```css
filter: saturate(200%);
```

**`sepia()`** - Applies a sepia tone effect to an element.
```css
filter: sepia(100%);
```

---

## Color Functions

Color functions define color values using various color models.

**`rgb()`** - Defines a color using red, green, and blue values.
```css
color: rgb(255, 0, 0);
```

**`hsl()`** - Defines a color using hue, saturation, and lightness.
```css
color: hsl(120, 100%, 50%);
```

**`hwb()`** - Defines a color using hue, whiteness, and blackness.
```css
color: hwb(120 30% 20%);
```

**`lab()`** - Defines a color in the Lab color space.
```css
color: lab(50% 40 60);
```

**`lch()`** - Defines a color using lightness, chroma, and hue.
```css
color: lch(50% 50 120);
```

**`oklab()`** - Defines a color in the Oklab color space.
```css
color: oklab(59% 0.1 0.1);
```

**`oklch()`** - Defines a color using lightness, chroma, and hue in the Oklch color space.
```css
color: oklch(59% 0.15 120);
```

**`color()`** - Specifies a color in a specific color space.
```css
color: color(display-p3 1 0.5 0);
```

**`color-mix()`** - Mixes two colors in a specified color space.
```css
background: color-mix(in srgb, red 50%, blue);
```

**`contrast-color()`** - Returns a color with maximum contrast for a given color.
```css
color: contrast-color(white);
```

**`device-cmyk()`** - Defines CMYK colors in a device-dependent way.
```css
color: device-cmyk(0 81% 81% 30%);
```

**`light-dark()`** - Returns one of two colors based on the current color scheme.
```css
color: light-dark(black, white);
```

**`dynamic-range-limit-mix()`** - Creates a custom maximum luminance limit by mixing different dynamic range limit keywords.
```css
color: dynamic-range-limit-mix(standard 50%, high 50%);
```

---

## Image Functions

Image functions create or manipulate images used as backgrounds or content.

### Gradient Functions

**`linear-gradient()`** - Creates a gradient that transitions colors along a straight line.
```css
background: linear-gradient(to right, red, blue);
```

**`radial-gradient()`** - Creates a gradient that radiates from a center point.
```css
background: radial-gradient(circle, red, blue);
```

**`conic-gradient()`** - Creates a gradient that rotates around a center point.
```css
background: conic-gradient(from 90deg, red, blue);
```

**`repeating-linear-gradient()`** - Creates a repeating linear gradient.
```css
background: repeating-linear-gradient(45deg, red, blue 20px);
```

**`repeating-radial-gradient()`** - Creates a repeating radial gradient.
```css
background: repeating-radial-gradient(circle, red, blue 20px);
```

**`repeating-conic-gradient()`** - Creates a repeating conic gradient.
```css
background: repeating-conic-gradient(red 0deg 10deg, blue 10deg 20deg);
```

### Other Image Functions

**`image()`** - Defines an image with added functionality including directionality and fallback images.
```css
background: image('photo.jpg', blue);
```

**`image-set()`** - Selects the most appropriate image from a set based on device capabilities.
```css
background: image-set('photo.jpg' 1x, 'photo-2x.jpg' 2x);
```

**`cross-fade()`** - Blends two or more images at specified transparency levels.
```css
background: cross-fade(url(image1.jpg), url(image2.jpg), 50%);
```

**`element()`** - Generates an image from an arbitrary HTML element.
```css
background: element(#myElement);
```

**`paint()`** - Generates an image using a CSS Paint API worklet.
```css
background: paint(myPainter);
```

---

## Counter Functions

Counter functions are used with the `content` property to display counter values.

**`counter()`** - Returns a string representing the current value of a named counter.
```css
content: counter(section);
```

**`counters()`** - Returns concatenated values of named counters for nested counters.
```css
content: counters(section, ".");
```

**`symbols()`** - Defines counter styles inline as a property value.
```css
list-style-type: symbols(cyclic "*" "†" "‡");
```

---

## Shape Functions

Shape functions define geometric shapes for clipping and positioning.

**`circle()`** - Defines a circular shape.
```css
clip-path: circle(50% at 50% 50%);
```

**`ellipse()`** - Defines an elliptical shape.
```css
clip-path: ellipse(50% 30% at 50% 50%);
```

**`inset()`** - Defines an inset rectangle shape.
```css
clip-path: inset(10px 20px);
```

**`rect()`** - Defines a rectangle using distances from the top and left edges.
```css
clip-path: rect(10px 200px 150px 10px);
```

**`xywh()`** - Defines a rectangle using x, y coordinates and width, height.
```css
clip-path: xywh(10px 10px 100px 100px);
```

**`polygon()`** - Defines a polygon shape using a series of coordinates.
```css
clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);
```

**`path()`** - Defines a shape using an SVG path string.
```css
clip-path: path('M 0 0 L 100 0 L 100 100 Z');
```

**`shape()`** - Defines a shape using a list of commands.
```css
offset-path: shape(from 0 0, line to 100px 100px);
```

**`ray()`** - Defines a line segment for animated element paths.
```css
offset-path: ray(45deg closest-side);
```

**`superellipse()`** - Defines the curvature of an ellipse for rounded corners.
```css
corner-shape: superellipse(2);
```

---

## Reference Functions

Reference functions retrieve values from other sources.

**`attr()`** - Retrieves the value of an HTML element attribute.
```css
content: attr(data-tooltip);
```

**`env()`** - Retrieves user-agent defined environment variables.
```css
padding-top: env(safe-area-inset-top);
```

**`if()`** - Conditionally sets a property value based on query results.
```css
color: if(style(--dark-mode: true), white, black);
```

**`url()`** - References a file from a specified URL.
```css
background-image: url('image.jpg');
```

**`var()`** - Retrieves the value of a CSS custom property.
```css
color: var(--primary-color);
```

---

## Grid Functions

Grid functions are used in CSS Grid layout.

**`fit-content()`** - Clamps a size to an available size.
```css
grid-template-columns: fit-content(200px);
```

**`minmax()`** - Defines a size range with minimum and maximum values.
```css
grid-template-columns: minmax(100px, 1fr);
```

**`repeat()`** - Repeats track definitions in grid layouts.
```css
grid-template-columns: repeat(3, 1fr);
```

---

## Font Functions

Font functions control alternate glyphs with the `font-variant-alternates` property.

**`stylistic()`** - Enables stylistic alternates for individual characters.
```css
font-variant-alternates: stylistic(flowing);
```

**`styleset()`** - Enables stylistic alternatives for sets of characters.
```css
font-variant-alternates: styleset(alt-g);
```

**`character-variant()`** - Enables specific stylistic alternatives for characters.
```css
font-variant-alternates: character-variant(cv02);
```

**`swash()`** - Enables swash glyphs.
```css
font-variant-alternates: swash(flowing);
```

**`ornaments()`** - Enables ornamental glyphs like fleurons.
```css
font-variant-alternates: ornaments(fleurons);
```

**`annotation()`** - Enables annotations like circled digits.
```css
font-variant-alternates: annotation(circled);
```

---

## Easing Functions

Easing functions define animation timing curves.

**`linear()`** - Creates a linear easing function that interpolates between points.
```css
animation-timing-function: linear(0, 0.5, 1);
```

**`cubic-bezier()`** - Defines a cubic Bézier curve for easing.
```css
animation-timing-function: cubic-bezier(0.42, 0, 0.58, 1);
```

**`steps()`** - Divides an animation into equal steps.
```css
animation-timing-function: steps(4, end);
```

---

## Animation Functions

Animation functions define animation timelines.

**`scroll()`** - Sets an animation timeline to a scroll progress timeline.
```css
animation-timeline: scroll(block nearest);
```

**`view()`** - Sets an animation timeline to a view progress timeline.
```css
animation-timeline: view(block);
```

---

## Anchor Positioning Functions

Anchor positioning functions position elements relative to anchor elements.

**`anchor()`** - Returns a length relative to the position of anchor element edges.
```css
top: anchor(bottom);
```

**`anchor-size()`** - Returns a length relative to the size of the anchor element.
```css
width: anchor-size(width);
```

---

## Tree Counting Functions

Tree counting functions return integer values based on the DOM tree structure.

**`sibling-index()`** - Returns the position of the selected element among its siblings.
```css
counter-reset: item sibling-index();
```

**`sibling-count()`** - Returns the total number of siblings including the selected element.
```css
counter-reset: total sibling-count();
```

---
