# Comprehensive CSS Properties Reference

This document presents a systematic enumeration of Cascading Style Sheets (CSS) properties, organized by functional category.

> Note to self. This document does not cover the properties as deeply as I would like. For each property you need more information on, document that property with all the information needed at the top of this file, under the heading "Expanded Property Notes". Arrange the properties in an alphabetical order. The property name should be a level 3 heading with sub-headings within the property's notes having lower levels (look at how `display` is documented).

## Expanded Property Notes

### `align-items`

The `align-items` property is a CSS property used in flexbox and grid layouts. It controls how items are positioned along the cross axis of their container. In flexbox, the cross axis is perpendicular to the main axis. In a horizontal layout, the cross axis is vertical (top to bottom).

#### Values

+ `stretch`: This is the default value. Items are stretched to fill the container's height (in horizontal layouts) or width (in vertical layouts). This only works if the items do not have a fixed size set.
+ `flex-start`: Items are placed at the start of the cross axis. In a horizontal layout, this means items align to the top of the container.
+ `flex-end`: Items are placed at the end of the cross axis. In a horizontal layout, items align to the bottom of the container.
+ `center`: Items are placed in the middle of the cross axis. This is commonly used to center items vertically within a container.
+ `baseline`: Items are aligned so that their text baselines line up. This is useful when you have items with different font sizes or padding and want their text to align properly.

---

### `border-bottom`

The `border-bottom` CSS property adds a border to the bottom edge of an element.

Basic syntax:
```css
border-bottom: width style color;
```

You can set all three values at once, or just one or two of them.

#### Examples

A simple bottom border:
```css
border-bottom: 1px solid black;
```

A thick blue dashed bottom border:
```css
border-bottom: 3px dashed blue;
```

Just setting the style:
```css
border-bottom: solid;
```

You can also control each part separately:

```css
border-bottom-width: 2px;
```

This sets how thick the bottom border is. You can use units like `px`, `em`, or keywords like `thin`, `medium`, `thick`.

```css
border-bottom-style: solid;
```

This sets the style of the bottom border. Common values include:
- `solid`
- `dashed`
- `dotted`
- `double`
- `none`

```css
border-bottom-color: red;
```

This sets the color of the bottom border.

---

### `box-shadow`

The `box-shadow` CSS property adds shadow effects around an element's frame.

The property takes several values in this order:

```css
box-shadow: horizontal vertical blur spread color;
```

+ **Horizontal offset** - This is the first value. It moves the shadow left or right. Positive numbers move it right. Negative numbers move it left.
+ **Vertical offset** - This is the second value. It moves the shadow up or down. Positive numbers move it down. Negative numbers move it up.
+ **Blur radius** - This is optional. It makes the shadow softer and more spread out. Larger numbers create more blur. The default is 0, which means sharp edges.
+ **Spread radius** - This is optional. It makes the shadow larger or smaller. Positive numbers make it bigger. Negative numbers make it smaller.
+ **Color** - This sets the shadow's color. You can use any valid CSS color.

#### Examples

A simple shadow below and to the right:
```css
box-shadow: 5px 5px 10px gray;
```

A shadow above and to the left:
```css
box-shadow: -5px -5px 10px black;
```

A large, soft shadow:
```css
box-shadow: 0 0 20px 5px rgba(0, 0, 0, 0.3);
```

#### Multiple Shadows

You can add multiple shadows by separating them with commas:
```css
box-shadow: 3px 3px 5px gray, -3px -3px 5px lightblue;
```

#### Inset Shadows

Adding the word `inset` at the start creates a shadow inside the element:
```css
box-shadow: inset 0 0 10px black;
```

---

### `box-sizing`

This property controls how the total width and height of an element are calculated.

#### Values

**1. `box-sizing: content-box` (the default)**

This means that `width` and `height` only apply to the content area of the element. Padding and borders are added on top of the width you set.

For example, if you set:
```css
width: 200px;
padding: 10px;
border: 5px;
```

The total width will be 230px (200px content + 10px padding on each side + 5px border on each side).

**2. `box-sizing: border-box`**

This means that `width` and `height` include the content, padding, and border. The browser calculates the content area by subtracting padding and border from the total width you set.

Using the same example:
```css
width: 200px;
padding: 10px;
border: 5px;
box-sizing: border-box;
```

The total width will be exactly 200px. The browser will make the content area smaller (170px) to fit the padding and border inside the 200px total.

---

### `display`

Determines the rendering behavior of elements within a document.

#### Values

+ `block`: An element with this value starts on a new line and takes up the full width available in its container. Block elements include `div`, `p`, etc.
+ `inline`: An element with this value flows within the text and does not start on a new line. It only takes up as much width as it needs. You cannot set width or height on inline elements. Examples include `<span>`, `<a>`, and `<strong>`.
+ `inline-block`: This value combines features of both inline and block. The element flows with the text but you can set its width, height, padding, and margin. This is useful for creating horizontal layouts.
+ `none`: An element with this value is removed completely from the page. It takes up no space. This is different from `visibility: hidden`, which hides the element but keeps its space.
+ `flex`: This value turns the element into a flex container. This allows you to arrange its child elements in flexible ways, making it useful for responsive layouts.
+ `grid`: This value turns the element into a grid container. You can define rows and columns to create organized two-dimensional layouts.
+ `inline-flex` and `inline-grid`: These work like flex and grid, but the container itself flows within the text like an inline element.

There are additional values such as `table`, `table-row`, and `table-cell` for creating table-like layouts, `list-item` for list formatting, and `contents` for removing the element's box while keeping its children visible.

---

### `flex`

The `flex` CSS property is a shorthand that sets how a flex item grows, shrinks, and sizes itself.

Basic Syntax:
```css
flex: grow shrink basis;
```

This combines three properties:
- `flex-grow` - How much the item grows
- `flex-shrink` - How much the item shrinks
- `flex-basis` - The initial size of the item

#### Common Values

Single Number:
```css
flex: 1;
```

This is shorthand for `flex: 1 1 0%`. The item can grow and shrink, starting from zero size.

Two Numbers:
```css
flex: 2 1;
```

This sets `flex-grow: 2` and `flex-shrink: 1`. The `flex-basis` defaults to `0%`.

Number and Size:
```css
flex: 1 200px;
```

This sets `flex-grow: 1` and `flex-basis: 200px`. The `flex-shrink` defaults to `1`.

Three Values:
```css
flex: 2 1 300px;
```

This sets `flex-grow: 2`, `flex-shrink: 1`, and `flex-basis: 300px`.

#### Common Keywords

Auto:
```css
flex: auto;
```

This is shorthand for `flex: 1 1 auto`. The item can grow and shrink, starting from its natural content size.

None:
```css
flex: none;
```

This is shorthand for `flex: 0 0 auto`. The item cannot grow or shrink. It stays at its natural size.

Initial:
```css
flex: initial;
```

This is shorthand for `flex: 0 1 auto`. The item can shrink but not grow.

If you do not set `flex`, the default is:

```css
flex: 0 1 auto;
```

This means items do not grow, but they can shrink, and they start at their natural size.

---

### `flex-shrink`

The `flex-shrink` CSS property controls how much a flex item shrinks when there is not enough space in the flex container. When flex items are too large to fit in their container, `flex-shrink` determines how much each item shrinks relative to the others.

Basic Syntax:
```css
flex-shrink: 1;
```

This is applied to individual flex items, not to the flex container.

**Default value:** `1` - Items can shrink if needed.

**Value of `0`:** The item will not shrink at all.

**Higher values:** The item shrinks more than items with lower values.

The value is a number (without units). It can be:
- Zero or positive numbers
- Decimals like `0.5`

Negative values are not allowed.

#### Examples

Preventing an Item from Shrinking:
```css
.item {
  flex-shrink: 0;
}
```

This item will keep its original size and will not shrink, even if there is not enough space.

Making an Item Shrink More:
```css
.item1 {
  flex-shrink: 1;
}

.item2 {
  flex-shrink: 2;
}
```

When space is tight, `item2` will shrink twice as much as `item1`.

#### Practical Use Case

Keeping a sidebar at a fixed width while allowing the main content to shrink:

```css
.container {
  display: flex;
}

.sidebar {
  width: 200px;
  flex-shrink: 0; /* Does not shrink */
}

.main-content {
  flex-shrink: 1; /* Can shrink if needed */
}
```

`flex-shrink` is often used with:
- `flex-grow` - Controls how items grow
- `flex-basis` - Sets the initial size before growing or shrinking

---

### `font-weight`

The `font-weight` CSS property sets how thick or thin the characters in text appear.

Basic Syntax:
```css
font-weight: bold;
```

Or:

```css
font-weight: 700;
```

#### Common Values

The default `font-weight` is `normal` (which equals 400).

**normal** - Regular weight (same as 400):
```css
font-weight: normal;
```

**bold** - Bold weight (same as 700):
```css
font-weight: bold;
```

**bolder** - One weight heavier than the parent element:
```css
font-weight: bolder;
```

**lighter** - One weight lighter than the parent element:
```css
font-weight: lighter;
```

You can use numbers from 100 to 900 in increments of 100:

```css
font-weight: 100; /* Thin */
font-weight: 200; /* Extra Light */
font-weight: 300; /* Light */
font-weight: 400; /* Normal (default) */
font-weight: 500; /* Medium */
font-weight: 600; /* Semi Bold */
font-weight: 700; /* Bold */
font-weight: 800; /* Extra Bold */
font-weight: 900; /* Black */
```

The exact appearance depends on which weights the font family supports.

Not all fonts support all weight values. If you request a weight that the font does not have, the browser will use the closest available weight.

For example, if a font only has weights 400 and 700:
- `font-weight: 300` will display as 400
- `font-weight: 600` will display as 700

Modern variable fonts can support any weight value between their minimum and maximum, not just increments of 100:

```css
font-weight: 450;
font-weight: 650;
```

This only works if the font is a variable font.

#### Inheritance

`font-weight` is inherited from parent elements. Child elements will use the same weight unless you specify otherwise.

```css
.parent {
  font-weight: 300;
}

.child {
  /* Inherits 300 from parent */
}
```

---

### `gap`

The `gap` CSS property sets the space between items in a flex container or grid container.

Basic Syntax:
```css
gap: 20px;
```

This adds 20 pixels of space between all items.

The `gap` property works with:
- **Flexbox** - Elements with `display: flex`
- **Grid** - Elements with `display: grid`

It does not work with normal block or inline elements.

Same Gap for All Directions:
```css
gap: 10px;
```

Different Gaps for Rows and Columns:
```css
gap: 20px 10px;
```

The first value is the row gap (vertical space). The second value is the column gap (horizontal space).

You can set row and column gaps separately:
```css
row-gap: 20px;
column-gap: 10px;
```

#### Value Types

**Pixels:**
```css
gap: 15px;
```

**Percentages:**
```css
gap: 5%;
```

**Em or rem units:**
```css
gap: 1rem;
```

**Zero** (no gap):
```css
gap: 0;
```

Note: Gap cannot have negative values.

---

### `justify-content`

This property controls how items are positioned along the main axis of their container. It is used in flexbox and grid layouts. In flexbox, the main axis is usually horizontal (left to right) but can be vertical if you change the flex direction.

#### Values

+ `flex-start`: This is the default value. Items are placed at the beginning of the container. In a horizontal layout, this means items align to the left.
+ `flex-end`: Items are placed at the end of the container. In a horizontal layout, items align to the right.
+ `center`: Items are placed in the middle of the container. This is useful for centering content horizontally.
+ `space-between`: Items are spread out evenly across the container. The first item is at the start, the last item is at the end, and remaining space is distributed equally between items.
+ `space-around`: Items are spread out with equal space around each item. This means the space between items is twice as large as the space at the edges.
+ `space-evenly`: Items are spread out with exactly equal space between them and at the edges. All gaps are the same size.

---

### `margin`

The `margin` CSS property creates space around the outside of an element.

Basic syntax:
```css
margin: 20px;
```

This adds 20 pixels of space around all sides of the element.

Margin creates transparent space between an element and other elements around it. Unlike padding (which creates space inside an element), margin pushes other elements away.

#### Examples

All Sides the Same:
```css
margin: 10px;
```

Different Values for Each Side:
**Two values** - Top/bottom, then left/right:
```css
margin: 10px 20px;
```

**Three values** - Top, left/right, then bottom:
```css
margin: 10px 20px 30px;
```

**Four values** - Top, right, bottom, left (clockwise):
```css
margin: 10px 20px 30px 40px;
```

You can set each side separately:

```css
margin-top: 10px;
margin-right: 20px;
margin-bottom: 10px;
margin-left: 20px;
```

#### Value Types

**Pixels:**
```css
margin: 20px;
```

**Percentages** (relative to the parent element's width):
```css
margin: 5%;
```

**Em or rem units:**
```css
margin: 1.5em;
```

**Auto** (for centering):
```css
margin: 0 auto;
```

This centers a block element horizontally.

**Zero** (no margin):
```css
margin: 0;
```

**Negative values** (pulls elements closer or creates overlap):
```css
margin-top: -10px;
```

#### Margin Collapse

When two vertical margins touch, they collapse into one margin. The larger margin wins.

Example:
```css
.box1 { margin-bottom: 20px; }
.box2 { margin-top: 30px; }
```

The space between these boxes will be 30px (not 50px), because the margins collapse and the larger one (30px) is used.

Horizontal margins do not collapse.

#### Negative Margins

Negative margins pull elements in the opposite direction:

```css
margin-left: -10px;
```

This moves the element 10 pixels to the left, potentially overlapping with other elements.

---

### `min-height`

This property sets the minimum height an element can have. The element can grow taller than this value if its content requires more space, but it will never be shorter than the specified minimum.

#### Values

+ Length values: You can use units like `px` (pixels), `em`, `rem`, `vh` (viewport height), or `%` (percentage of the parent's height). For example: `min-height: 200px` or `min-height: 50vh`.
+ `0`: This is the default value. The element has no minimum height and will only be as tall as its content requires.
+ `auto`: The browser calculates the minimum height automatically based on the content.

The `min-height` property works alongside `height` and `max-height`. If both `height` and `min-height` are set, and `min-height` is larger, then `min-height` takes priority. The element will be at least as tall as `min-height` specifies.

---

### `outline`

The `outline` CSS property draws a line around the outside of an element, beyond its border.

Basic Syntax:
```css
outline: width style color;
```

You can set all three values at once, or just one or two of them.

This sets how thick the outline is:
```css
outline-width: 2px;
```

You can use units like `px`, `em`, or keywords like `thin`, `medium`, `thick`.

Style is required for the outline to show. Common styles include:

- `solid` - A single solid line
- `dashed` - A dashed line
- `dotted` - A dotted line
- `double` - Two solid lines
- `groove` - A 3D grooved outline
- `ridge` - A 3D ridged outline
- `inset` - A 3D inset outline
- `outset` - A 3D outset outline
- `none` - No outline (default)

```css
outline-style: solid;
```

This sets the outline's color:
```css
outline-color: blue;
```

To remove an outline:
```css
outline: none;
/*
Or:
*/
outline: 0;
```

**Accessibility Warning**: Do not remove focus outlines without providing an alternative. Focus indicators help keyboard users know which element is active. Removing them makes websites harder to use for people who navigate without a mouse.

You can control each part separately:
```css
outline-width: 3px;
outline-style: dashed;
outline-color: green;
```

---

### `padding`

The `padding` CSS property creates space inside an element, between the element's content and its border.

Basic Syntax:
```css
padding: 20px;
```

This adds 20 pixels of space inside all sides of the element.

Padding creates space inside an element. Unlike margin (which creates space outside an element), padding pushes the content away from the element's edges. Padding uses the element's background color.

#### Examples

All Sides the Same:
```css
padding: 10px;
```

**Two values** - Top/bottom, then left/right:
```css
padding: 10px 20px;
```

**Three values** - Top, left/right, then bottom:
```css
padding: 10px 20px 30px;
```

**Four values** - Top, right, bottom, left (clockwise):
```css
padding: 10px 20px 30px 40px;
```

You can set each side separately:
```css
padding-top: 10px;
padding-right: 20px;
padding-bottom: 10px;
padding-left: 20px;
```

#### Padding and Box Size

By default, padding increases the total size of an element. If you set `width: 200px` and `padding: 20px`, the total width becomes 240px (200px + 20px left + 20px right).

You can change this behavior with `box-sizing`:

```css
.box {
  box-sizing: border-box;
  width: 200px;
  padding: 20px;
}
```

With `box-sizing: border-box`, the total width stays 200px, and the padding is included inside that width.

---

### `position`

The `position` CSS property sets how an element is positioned in the document.

#### Values

There are five main position values:

##### 1. Static

```css
position: static;
```

This is the default value. Elements appear in the normal document flow. The properties `top`, `right`, `bottom`, `left`, and `z-index` have no effect.

##### 2. Relative

```css
position: relative;
```

The element is positioned relative to its normal position. You can move it using `top`, `right`, `bottom`, and `left`, but its original space remains reserved in the layout.

Example:
```css
.box {
  position: relative;
  top: 20px;
  left: 30px;
}
```

This moves the box 20 pixels down and 30 pixels right from where it would normally be.

##### 3. Absolute

```css
position: absolute;
```

The element is removed from the normal document flow. It is positioned relative to its nearest positioned ancestor (an ancestor with `position` other than `static`). If no positioned ancestor exists, it positions relative to the document body.

Example:
```css
.child {
  position: absolute;
  top: 10px;
  right: 10px;
}
```

##### 4. Fixed

```css
position: fixed;
```

The element is removed from the normal flow and positioned relative to the browser window. It stays in the same place even when the page is scrolled.

Example:
```css
.header {
  position: fixed;
  top: 0;
  width: 100%;
}
```

This creates a header that stays at the top while scrolling.

##### 5. Sticky

```css
position: sticky;
```

The element acts like `relative` until it reaches a specified scroll position, then it acts like `fixed`. You must specify at least one of `top`, `right`, `bottom`, or `left`.

Example:
```css
.sidebar {
  position: sticky;
  top: 20px;
}
```

#### Positioning Properties

Once you set a position value (except `static`), you can use these properties:

- `top` - Distance from the top
- `right` - Distance from the right
- `bottom` - Distance from the bottom
- `left` - Distance from the left

These properties accept values like pixels, percentages, or other CSS units.

---

### `text-align`

`text-align` is a CSS property that controls the horizontal alignment of text and inline content within an element.

#### Values

**1. `text-align: left` (the default for left-to-right languages)**

This aligns the text to the left edge of the container.

```css
text-align: left;
```

**2. `text-align: right`**

This aligns the text to the right edge of the container.

```css
text-align: right;
```

**3. `text-align: center`**

This centers the text horizontally within the container.

```css
text-align: center;
```

**4. `text-align: justify`**

This stretches the text so that each line has equal width. The browser adds extra space between words to make both the left and right edges align. The last line is usually left-aligned.

```css
text-align: justify;
```

**Important notes:**

- `text-align` only works on **block-level elements** (like `<div>`, `<p>`, `<h1>`) or elements with `display: block`
- It affects the text and inline elements (like `<span>`, `<img>`, `<a>`) inside the element, not the element itself
- To center a block element itself (not its text), you need to use different techniques, like `margin: 0 auto` with a set width

**Example:**
```css
p {
  text-align: center; /* Centers the text inside the paragraph */
}
```

---

### `transition`

The `transition` CSS property creates smooth animations when CSS properties change from one value to another.

Basic Syntax:
```css
transition: property duration timing-function delay;
```

You can set all four values at once, or just one or two of them.

#### Property

Which CSS property to animate.

```css
transition: background-color 0.3s;
```

You can use `all` to animate all properties:

```css
transition: all 0.3s;
```

#### Duration

How long the transition takes.

```css
transition: color 2s;
```

Use seconds (`s`) or milliseconds (`ms`). For example, `0.3s` or `300ms`.

#### Timing Function (Optional)

How the transition progresses over time.

Common values:
- `ease` - Starts slow, speeds up, then slows down (default)
- `linear` - Constant speed throughout
- `ease-in` - Starts slow, then speeds up
- `ease-out` - Starts fast, then slows down
- `ease-in-out` - Similar to ease but more pronounced

```css
transition: width 1s ease-in-out;
```

#### Delay (Optional)

How long to wait before starting the transition.

```css
transition: opacity 0.5s ease 0.2s;
```

This waits 0.2 seconds before starting the opacity transition.

#### Examples

##### Simple Hover Effect

```css
button {
  background-color: blue;
  transition: background-color 0.3s;
}

button:hover {
  background-color: red;
}
```

The background color smoothly changes from blue to red over 0.3 seconds.

##### Multiple Properties

You can animate multiple properties by separating them with commas:

```css
.box {
  width: 100px;
  height: 100px;
  background-color: blue;
  transition: width 0.5s, height 0.5s, background-color 0.3s;
}

.box:hover {
  width: 200px;
  height: 200px;
  background-color: red;
}
```

#### Animating All Properties

```css
.card {
  opacity: 1;
  transform: scale(1);
  transition: all 0.3s ease;
}

.card:hover {
  opacity: 0.8;
  transform: scale(1.05);
}
```

#### Individual Properties

You can set each part separately:

```css
transition-property: background-color;
transition-duration: 0.5s;
transition-timing-function: ease-in-out;
transition-delay: 0.1s;
```

#### Properties That Can Be Transitioned

Most numeric and color properties can be transitioned, including:
- `opacity`
- `color`, `background-color`, `border-color`
- `width`, `height`
- `margin`, `padding`
- `transform` (scale, rotate, translate)
- `box-shadow`
- `border-width`

Properties like `display` and `visibility` cannot be smoothly transitioned (though `visibility` can be delayed).

For smooth animations, prefer transitioning these properties:
- `opacity`
- `transform` (translate, scale, rotate)

These perform better than transitioning properties like `width`, `height`, or `top`/`left`.

#### Removing Transitions

To remove a transition:
```css
transition: none;
```

---

### `z-index`

The `z-index` CSS property controls the stacking order of elements on a webpage.

When elements overlap, `z-index` determines which element appears on top. Elements with higher `z-index` values appear in front of elements with lower values.

Basic usage:
```css
z-index: 10;
```

The value is a number. It can be positive, negative, or zero.

+ **Higher numbers are on top** - An element with `z-index: 10` will appear above an element with `z-index: 5`.
+ **Default value** - Elements start with `z-index: auto`, which behaves like `z-index: 0`.
+ **Negative values** - You can use negative numbers like `z-index: -1` to push elements behind others.

**Note**: The `z-index` property only works on positioned elements. This means the element must have a `position` value of:
- `relative`
- `absolute`
- `fixed`
- `sticky`

It does not work on elements with `position: static` (the default).

#### Examples

Creating a popup that appears above other content:
```css
.popup {
  position: fixed;
  z-index: 100;
}
```

Layering three overlapping boxes:
```css
.box1 { position: relative; z-index: 1; }
.box2 { position: relative; z-index: 2; }
.box3 { position: relative; z-index: 3; }
```

#### Stacking Context

Elements create separate stacking groups called stacking contexts. A child element cannot appear above elements outside its parent's stacking context, no matter how high its `z-index` is. This means `z-index` values only compete within the same stacking context.

---

## Typography and Text Properties

### Font Properties

+ `font`: Shorthand property for comprehensive font specification
+ `font-family`: Specifies typeface for text rendering
+ `font-size`: Determines text scale and dimensions
+ `font-style`: Controls italic and oblique text presentation
+ `font-variant`: Manages small-caps and variant typography
+ `font-weight`: Adjusts text boldness and thickness
+ `font-stretch`: Controls horizontal condensation or expansion
+ `font-kerning`: Manages spacing between character pairs
+ `font-feature-settings`: Enables OpenType font features
+ `font-variant-caps`: Controls capital letter variants
+ `font-variant-ligatures`: Manages ligature rendering
+ `font-variant-numeric`: Controls numeric character variants
+ `font-variant-east-asian`: Manages East Asian character variants
+ `font-variant-alternates`: Specifies alternate glyph usage
+ `font-variant-position`: Controls subscript and superscript
+ `font-optical-sizing`: Manages optical size variation
+ `font-synthesis`: Controls browser synthesis of font styles
+ `font-synthesis-weight`: Controls weight synthesis
+ `font-synthesis-style`: Controls style synthesis
+ `font-synthesis-small-caps`: Controls small-caps synthesis
+ `font-synthesis-position`: Controls position synthesis
+ `font-language-override`: Overrides language-specific rendering
+ `font-palette`: Selects color font palette
+ `font-size-adjust`: Preserves legibility across font changes
+ `font-variation-settings`: Controls variable font axes

### Text Properties

+ `color`: Specifies foreground text color
+ `text-align`: Controls horizontal text alignment
+ `text-align-last`: Aligns final line of text block
+ `text-decoration`: Applies decorative lines to text
+ `text-decoration-line`: Specifies decoration line type
+ `text-decoration-color`: Defines decoration line color
+ `text-decoration-style`: Determines decoration line style
+ `text-decoration-thickness`: Controls decoration line thickness
+ `text-decoration-skip-ink`: Manages decoration interaction with descenders
+ `text-indent`: Specifies first-line indentation
+ `text-justify`: Controls text justification algorithm
+ `text-overflow`: Manages overflow text truncation
+ `text-shadow`: Applies shadow effects to text
+ `text-transform`: Controls capitalization transformation
+ `text-underline-offset`: Adjusts underline vertical position
+ `text-underline-position`: Controls underline placement
+ `text-emphasis`: Applies emphasis marks to text
+ `text-emphasis-color`: Specifies emphasis mark color
+ `text-emphasis-position`: Determines emphasis mark placement
+ `text-emphasis-style`: Defines emphasis mark appearance
+ `text-orientation`: Controls glyph orientation in vertical text
+ `text-combine-upright`: Manages character combination in vertical text
+ `text-wrap`: Controls text wrapping behavior
+ `text-wrap-mode`: Specifies wrapping mode
+ `text-wrap-style`: Determines wrapping style characteristics
+ `text-rendering`: Optimizes text rendering
+ `text-spacing-trim`: Controls spacing at text boundaries
+ `text-autospace`: Manages automatic spacing rules

### Line and Letter Spacing

+ `line-height`: Controls vertical spacing between text lines
+ `line-height-step`: Quantizes line height to specified step
+ `letter-spacing`: Adjusts spacing between characters
+ `word-spacing`: Controls spacing between words
+ `word-break`: Specifies word breaking behavior
+ `overflow-wrap`: Controls word breaking at overflow
+ `white-space`: Manages whitespace handling
+ `white-space-collapse`: Controls whitespace collapsing
+ `hyphens`: Controls hyphenation behavior
+ `hyphenate-character`: Specifies hyphenation character
+ `hyphenate-limit-chars`: Sets minimum characters for hyphenation
+ `tab-size`: Specifies tab character width
+ `hanging-punctuation`: Controls punctuation placement

## Box Model Properties

### Dimensions

+ `width`: Specifies element width
+ `height`: Specifies element height
+ `min-width`: Establishes minimum width constraint
+ `max-width`: Establishes maximum width constraint
+ `min-height`: Establishes minimum height constraint
+ `max-height`: Establishes maximum height constraint
+ `inline-size`: Specifies size in inline direction
+ `block-size`: Specifies size in block direction
+ `min-inline-size`: Establishes minimum inline size
+ `max-inline-size`: Establishes maximum inline size
+ `min-block-size`: Establishes minimum block size
+ `max-block-size`: Establishes maximum block size

### Padding

+ `padding`: Shorthand for internal spacing
+ `padding-top`: Specifies top internal spacing
+ `padding-right`: Specifies right internal spacing
+ `padding-bottom`: Specifies bottom internal spacing
+ `padding-left`: Specifies left internal spacing
+ `padding-block`: Shorthand for block-axis padding
+ `padding-block-start`: Specifies block-start padding
+ `padding-block-end`: Specifies block-end padding
+ `padding-inline`: Shorthand for inline-axis padding
+ `padding-inline-start`: Specifies inline-start padding
+ `padding-inline-end`: Specifies inline-end padding

### Margin

+ `margin`: Shorthand for external spacing
+ `margin-top`: Specifies top external spacing
+ `margin-right`: Specifies right external spacing
+ `margin-bottom`: Specifies bottom external spacing
+ `margin-left`: Specifies left external spacing
+ `margin-block`: Shorthand for block-axis margin
+ `margin-block-start`: Specifies block-start margin
+ `margin-block-end`: Specifies block-end margin
+ `margin-inline`: Shorthand for inline-axis margin
+ `margin-inline-start`: Specifies inline-start margin
+ `margin-inline-end`: Specifies inline-end margin
+ `margin-trim`: Removes margins at container edges

### Border

+ `border`: Shorthand for border specification
+ `border-width`: Specifies border thickness
+ `border-style`: Defines border visual style
+ `border-color`: Specifies border color
+ `border-top`: Shorthand for top border
+ `border-top-width`: Specifies top border thickness
+ `border-top-style`: Defines top border style
+ `border-top-color`: Specifies top border color
+ `border-right`: Shorthand for right border
+ `border-right-width`: Specifies right border thickness
+ `border-right-style`: Defines right border style
+ `border-right-color`: Specifies right border color
+ `border-bottom`: Shorthand for bottom border
+ `border-bottom-width`: Specifies bottom border thickness
+ `border-bottom-style`: Defines bottom border style
+ `border-bottom-color`: Specifies bottom border color
+ `border-left`: Shorthand for left border
+ `border-left-width`: Specifies left border thickness
+ `border-left-style`: Defines left border style
+ `border-left-color`: Specifies left border color
+ `border-block`: Shorthand for block-axis borders
+ `border-block-width`: Specifies block-axis border thickness
+ `border-block-style`: Defines block-axis border style
+ `border-block-color`: Specifies block-axis border color
+ `border-block-start`: Shorthand for block-start border
+ `border-block-start-width`: Specifies block-start border thickness
+ `border-block-start-style`: Defines block-start border style
+ `border-block-start-color`: Specifies block-start border color
+ `border-block-end`: Shorthand for block-end border
+ `border-block-end-width`: Specifies block-end border thickness
+ `border-block-end-style`: Defines block-end border style
+ `border-block-end-color`: Specifies block-end border color
+ `border-inline`: Shorthand for inline-axis borders
+ `border-inline-width`: Specifies inline-axis border thickness
+ `border-inline-style`: Defines inline-axis border style
+ `border-inline-color`: Specifies inline-axis border color
+ `border-inline-start`: Shorthand for inline-start border
+ `border-inline-start-width`: Specifies inline-start border thickness
+ `border-inline-start-style`: Defines inline-start border style
+ `border-inline-start-color`: Specifies inline-start border color
+ `border-inline-end`: Shorthand for inline-end border
+ `border-inline-end-width`: Specifies inline-end border thickness
+ `border-inline-end-style`: Defines inline-end border style
+ `border-inline-end-color`: Specifies inline-end border color
+ `border-radius`: Specifies corner curvature
+ `border-top-left-radius`: Defines top-left corner radius
+ `border-top-right-radius`: Defines top-right corner radius
+ `border-bottom-right-radius`: Defines bottom-right corner radius
+ `border-bottom-left-radius`: Defines bottom-left corner radius
+ `border-start-start-radius`: Defines start-start corner radius
+ `border-start-end-radius`: Defines start-end corner radius
+ `border-end-start-radius`: Defines end-start corner radius
+ `border-end-end-radius`: Defines end-end corner radius
+ `border-image`: Shorthand for border image specification
+ `border-image-source`: Specifies border image source
+ `border-image-slice`: Defines border image slicing
+ `border-image-width`: Specifies border image width
+ `border-image-outset`: Extends border image beyond border box
+ `border-image-repeat`: Controls border image repetition
+ `border-collapse`: Controls table border rendering model
+ `border-spacing`: Specifies spacing between table borders

### Outline

+ `outline`: Shorthand for outline specification
+ `outline-width`: Specifies outline thickness
+ `outline-style`: Defines outline visual style
+ `outline-color`: Specifies outline color
+ `outline-offset`: Controls distance between outline and border edge

## Layout and Positioning

### Display

+ `display`: Establishes element rendering behavior
+ `visibility`: Controls element visibility
+ `opacity`: Specifies element transparency

### Position

+ `position`: Defines positioning scheme
+ `top`: Specifies vertical offset from containing block top
+ `right`: Specifies horizontal offset from containing block right
+ `bottom`: Specifies vertical offset from containing block bottom
+ `left`: Specifies horizontal offset from containing block left
+ `inset`: Shorthand for top, right, bottom, left
+ `inset-block`: Shorthand for block-axis insets
+ `inset-block-start`: Specifies block-start inset
+ `inset-block-end`: Specifies block-end inset
+ `inset-inline`: Shorthand for inline-axis insets
+ `inset-inline-start`: Specifies inline-start inset
+ `inset-inline-end`: Specifies inline-end inset
+ `z-index`: Controls stacking order in positioned elements

### Float and Clear

+ `float`: Positions element outside normal flow
+ `clear`: Prevents floating element adjacency

### Flexbox Layout

+ `flex`: Shorthand for flexible box properties
+ `flex-direction`: Establishes flex container main axis
+ `flex-wrap`: Controls flex item wrapping behavior
+ `flex-flow`: Shorthand for direction and wrap
+ `flex-grow`: Specifies flex item growth factor
+ `flex-shrink`: Specifies flex item shrink factor
+ `flex-basis`: Establishes flex item initial size
+ `justify-content`: Aligns items along main axis
+ `align-items`: Aligns items along cross axis
+ `align-self`: Overrides align-items for individual items
+ `align-content`: Aligns flex lines within container
+ `place-content`: Shorthand for align-content and justify-content
+ `place-items`: Shorthand for align-items and justify-items
+ `place-self`: Shorthand for align-self and justify-self
+ `order`: Controls flex item ordering
+ `gap`: Specifies spacing between flex items
+ `row-gap`: Specifies vertical spacing between rows
+ `column-gap`: Specifies horizontal spacing between columns

### Grid Layout

+ `grid`: Shorthand for grid container properties
+ `grid-template`: Shorthand for template rows, columns, areas
+ `grid-template-rows`: Defines grid row track sizes
+ `grid-template-columns`: Defines grid column track sizes
+ `grid-template-areas`: Establishes named grid areas
+ `grid-auto-rows`: Specifies implicit row track sizes
+ `grid-auto-columns`: Specifies implicit column track sizes
+ `grid-auto-flow`: Controls auto-placement algorithm
+ `grid-row`: Shorthand for row placement
+ `grid-row-start`: Specifies row start position
+ `grid-row-end`: Specifies row end position
+ `grid-column`: Shorthand for column placement
+ `grid-column-start`: Specifies column start position
+ `grid-column-end`: Specifies column end position
+ `grid-area`: Shorthand for row and column placement
+ `justify-items`: Aligns grid items along inline axis
+ `justify-self`: Controls individual item inline alignment

### Multi+column Layout

+ `columns`: Shorthand for column properties
+ `column-count`: Specifies number of columns
+ `column-width`: Defines optimal column width
+ `column-gap`: Specifies spacing between columns
+ `column-rule`: Shorthand for column divider specification
+ `column-rule-width`: Specifies column divider thickness
+ `column-rule-style`: Defines column divider style
+ `column-rule-color`: Specifies column divider color
+ `column-span`: Controls element spanning across columns
+ `column-fill`: Controls content distribution across columns
+ `break-before`: Controls page/column break before element
+ `break-after`: Controls page/column break after element
+ `break-inside`: Controls page/column break within element

### Box Sizing and Overflow

+ `box-sizing`: Controls box model calculation method
+ `overflow`: Shorthand for overflow behavior
+ `overflow-x`: Controls horizontal overflow behavior
+ `overflow-y`: Controls vertical overflow behavior
+ `overflow-block`: Controls block-axis overflow
+ `overflow-inline`: Controls inline-axis overflow
+ `overflow-wrap`: Controls word breaking at line end
+ `overflow-clip-margin`: Extends overflow clip boundary
+ `overflow-anchor`: Controls scroll anchoring behavior
+ `overscroll-behavior`: Shorthand for overscroll behavior
+ `overscroll-behavior-x`: Controls horizontal overscroll
+ `overscroll-behavior-y`: Controls vertical overscroll
+ `overscroll-behavior-block`: Controls block-axis overscroll
+ `overscroll-behavior-inline`: Controls inline-axis overscroll

## Visual Effects

### Background

+ `background`: Shorthand for background properties
+ `background-color`: Specifies background fill color
+ `background-image`: Defines background image
+ `background-position`: Specifies background image position
+ `background-position-x`: Controls horizontal background position
+ `background-position-y`: Controls vertical background position
+ `background-size`: Defines background image dimensions
+ `background-repeat`: Controls background image repetition
+ `background-attachment`: Specifies background scrolling behavior
+ `background-origin`: Determines background positioning area
+ `background-clip`: Defines background painting area
+ `background-blend-mode`: Specifies background layer blending

### Shadows and Filters

+ `box-shadow`: Applies shadow effects to element box
+ `filter`: Applies graphical effects to element
+ `backdrop-filter`: Applies effects to area behind element

### Transformations

+ `transform`: Applies geometric transformations
+ `transform-origin`: Establishes transformation reference point
+ `transform-style`: Preserves 3D transformation context
+ `transform-box`: Defines transformation coordinate space
+ `rotate`: Specifies rotation transformation
+ `scale`: Specifies scaling transformation
+ `translate`: Specifies translation transformation
+ `perspective`: Establishes 3D perspective viewing distance
+ `perspective-origin`: Defines 3D perspective vanishing point

### Transitions and Animations

+ `transition`: Shorthand for transition properties
+ `transition-property`: Specifies properties to transition
+ `transition-duration`: Defines transition duration
+ `transition-timing-function`: Controls transition acceleration curve
+ `transition-delay`: Specifies transition start delay
+ `transition-behavior`: Controls transition behavior for discrete properties

### Blending and Masking

+ `mix-blend-mode`: Specifies element blending with backdrop
+ `isolation`: Creates new stacking context for blending
+ `mask`: Shorthand for masking properties
+ `mask-image`: Defines mask image source
+ `mask-mode`: Specifies mask application mode
+ `mask-position`: Controls mask position
+ `mask-size`: Defines mask dimensions
+ `mask-repeat`: Controls mask repetition
+ `mask-origin`: Determines mask positioning area
+ `mask-clip`: Defines mask painting area
+ `mask-composite`: Specifies mask compositing operation
+ `mask-border`: Shorthand for mask border properties
+ `mask-border-source`: Specifies mask border image
+ `mask-border-slice`: Defines mask border slicing
+ `mask-border-width`: Specifies mask border width
+ `mask-border-outset`: Extends mask border beyond element
+ `mask-border-repeat`: Controls mask border repetition
+ `mask-border-mode`: Defines mask border application mode
+ `mask-type`: Specifies SVG mask type
+ `clip-path`: Defines visible element region
+ `clip-rule`: Determines clipping region fill algorithm

### Color and Appearance

+ `color-scheme`: Indicates color scheme preference
+ `forced-color-adjust`: Controls forced color mode behavior
+ `appearance`: Controls native widget appearance
+ `accent-color`: Specifies user interface accent color
+ `caret-color`: Defines text input caret color
+ `caret`: Shorthand for caret properties
+ `caret-shape`: Controls caret visual shape

## Scrolling and Interaction

### Scroll Behavior

+ `scroll-behavior`: Controls scrolling animation behavior
+ `scroll-margin`: Shorthand for scroll margin
+ `scroll-margin-top`: Specifies top scroll margin
+ `scroll-margin-right`: Specifies right scroll margin
+ `scroll-margin-bottom`: Specifies bottom scroll margin
+ `scroll-margin-left`: Specifies left scroll margin
+ `scroll-margin-block`: Shorthand for block-axis scroll margin
+ `scroll-margin-block-start`: Specifies block-start scroll margin
+ `scroll-margin-block-end`: Specifies block-end scroll margin
+ `scroll-margin-inline`: Shorthand for inline-axis scroll margin
+ `scroll-margin-inline-start`: Specifies inline-start scroll margin
+ `scroll-margin-inline-end`: Specifies inline-end scroll margin
+ `scroll-padding`: Shorthand for scroll padding
+ `scroll-padding-top`: Specifies top scroll padding
+ `scroll-padding-right`: Specifies right scroll padding
+ `scroll-padding-bottom`: Specifies bottom scroll padding
+ `scroll-padding-left`: Specifies left scroll padding
+ `scroll-padding-block`: Shorthand for block-axis scroll padding
+ `scroll-padding-block-start`: Specifies block-start scroll padding
+ `scroll-padding-block-end`: Specifies block-end scroll padding
+ `scroll-padding-inline`: Shorthand for inline-axis scroll padding
+ `scroll-padding-inline-start`: Specifies inline-start scroll padding
+ `scroll-padding-inline-end`: Specifies inline-end scroll padding
+ `scroll-snap-type`: Defines scroll snap container characteristics
+ `scroll-snap-align`: Specifies snap alignment position
+ `scroll-snap-stop`: Controls snap point bypassing behavior
+ `scroll-timeline`: Defines scroll-driven animation timeline
+ `scroll-timeline-name`: Specifies scroll timeline identifier
+ `scroll-timeline-axis`: Defines scroll timeline axis

### Scrollbar Styling

+ `scrollbar-color`: Specifies scrollbar color scheme
+ `scrollbar-width`: Controls scrollbar thickness
+ `scrollbar-gutter`: Reserves space for scrollbar

### User Interaction

+ `pointer-events`: Controls pointer event processing
+ `touch-action`: Determines touch gesture handling
+ `user-select`: Controls text selection capability
+ `resize`: Enables user-initiated element resizing
+ `cursor`: Specifies pointer cursor appearance

## List Styling

+ `list-style`: Shorthand for list properties
+ `list-style-type`: Defines list item marker type
+ `list-style-position`: Controls marker positioning
+ `list-style-image`: Specifies custom marker image

## Table Properties

+ `table-layout`: Controls table layout algorithm
+ `caption-side`: Specifies table caption position
+ `empty-cells`: Controls empty cell border rendering

## Content and Generated Content

+ `content`: Generates content in pseudo-elements
+ `quotes`: Defines quotation mark characters
+ `counter-reset`: Creates or resets counters
+ `counter-increment`: Increments counter values
+ `counter-set`: Sets counter to specific value

## Printing and Paged Media

+ `page`: Specifies named page for element
+ `page-break-before`: Controls page break before element
+ `page-break-after`: Controls page break after element
+ `page-break-inside`: Controls page break within element
+ `orphans`: Specifies minimum lines at page bottom
+ `widows`: Specifies minimum lines at page top

## Writing Modes and Direction

+ `writing-mode`: Establishes block flow direction
+ `direction`: Specifies inline base direction
+ `text-orientation`: Controls glyph orientation
+ `unicode-bidi`: Controls bidirectional text handling

## SVG+specific Properties

+ `fill`: Specifies fill color for SVG shapes
+ `fill-opacity`: Controls fill transparency
+ `fill-rule`: Determines fill region algorithm
+ `stroke`: Specifies stroke color for SVG shapes
+ `stroke-width`: Controls stroke thickness
+ `stroke-opacity`: Controls stroke transparency
+ `stroke-linecap`: Defines stroke end cap style
+ `stroke-linejoin`: Specifies stroke corner style
+ `stroke-dasharray`: Creates dashed stroke pattern
+ `stroke-dashoffset`: Offsets dash pattern start position
+ `stroke-miterlimit`: Limits miter length at sharp corners
+ `marker`: Shorthand for shape markers
+ `marker-start`: Specifies marker at path start
+ `marker-mid`: Specifies marker at path vertices
+ `marker-end`: Specifies marker at path end
+ `paint-order`: Controls painting order of fill, stroke, markers
+ `vector-effect`: Controls coordinate space for stroke
+ `shape-rendering`: Optimizes shape rendering quality
+ `color-interpolation-filters`: Controls filter color space
+ `flood-color`: Specifies flood color for filters
+ `flood-opacity`: Controls flood opacity
+ `lighting-color`: Specifies lighting color for filters
+ `stop-color`: Defines gradient stop color
+ `stop-opacity`: Controls gradient stop opacity

## Container Queries

+ `container`: Shorthand for container properties
+ `container-type`: Defines container query type
+ `container-name`: Specifies container identifier

## Containment

+ `contain`: Enables layout containment optimizations
+ `content-visibility`: Controls element rendering behavior
+ `contain-intrinsic-size`: Shorthand for intrinsic size specification
+ `contain-intrinsic-width`: Specifies intrinsic width placeholder
+ `contain-intrinsic-height`: Specifies intrinsic height placeholder
+ `contain-intrinsic-block-size`: Specifies intrinsic block size
+ `contain-intrinsic-inline-size`: Specifies intrinsic inline size

## Anchor Positioning

+ `anchor-name`: Defines anchor element identifier
+ `position-anchor`: Associates element with anchor
+ `position-area`: Specifies positioning area relative to anchor

## View Transitions

+ `view-transition-name`: Defines view transition participant identifier
+ `view-transition-class`: Assigns class to view transition element

## Mathematical Layout

+ `math-style`: Controls mathematical notation style
+ `math-depth`: Manages mathematical expression nesting
+ `math-shift`: Controls superscript/subscript positioning

## Ruby Annotations

+ `ruby-position`: Specifies ruby annotation position
+ `ruby-align`: Controls ruby content alignment

## Image Rendering

+ `image-rendering`: Optimizes image scaling algorithm
+ `image-orientation`: Controls image orientation
+ `image-resolution`: Specifies image intrinsic resolution
+ `object-fit`: Controls replaced element content fitting
+ `object-position`: Specifies replaced element content position
+ `object-view-box`: Defines viewable region of replaced content

## Motion Path

+ `offset`: Shorthand for motion path properties
+ `offset-path`: Defines motion path
+ `offset-distance`: Specifies position along path
+ `offset-rotate`: Controls orientation along path
+ `offset-anchor`: Defines element anchor point for path
+ `offset-position`: Specifies initial position reference

## Miscellaneous Properties

+ `all`: Resets all properties except direction and unicode-bidi
+ `aspect-ratio`: Specifies preferred width-to-height ratio
+ `box-decoration-break`: Controls fragmented box decoration
+ `field-sizing`: Controls form field sizing behavior
+ `initial-letter`: Creates drop cap effect
+ `interpolate-size`: Enables size interpolation for animations
+ `line-clamp`: Limits text to specified line count
+ `overlay`: Controls overlay painting order
+ `print-color-adjust`: Controls color adjustment in print
+ `will-change`: Hints at upcoming property changes for optimization
+ `zoom`: Scales element and its contents
