## Measurement Units

### Absolute Units

+ **`px` (pixels)** - This is the most common absolute unit. One pixel represents one dot on the screen. Pixels provide precise control but do not scale with user settings. For example: `width: 200px`.
+ **`pt` (points)**, **`cm` (centimeters)**, **`mm` (millimeters)**, **`in` (inches)** - These are physical measurement units primarily used for print styles. They are rarely used for screen design. One point equals 1/72 of an inch.

### Relative Units - Font-based

+ **`em`** - This unit is relative to the font size of the element itself. If an element has `font-size: 16px`, then `1em` equals 16 pixels. The value compounds when nested, which can cause unexpected sizing. For example: `padding: 1.5em`.
+ **`rem` (root em)** - This unit is relative to the root element's font size (usually the `<html>` element). Unlike `em`, it does not compound when nested, making it more predictable. For example: `margin: 2rem`.

### Relative Units - Viewport-based

+ **`vw` (viewport width)** - One `vw` equals 1% of the viewport's width. `100vw` is the full width of the browser window. This is useful for responsive designs.
+ **`vh` (viewport height)** - One `vh` equals 1% of the viewport's height. `100vh` is the full height of the browser window. This is commonly used for full-screen sections.
+ **`vmin`** - This equals 1% of the smaller dimension (width or height) of the viewport.
+ **`vmax`** - This equals 1% of the larger dimension (width or height) of the viewport.

### Percentage

+ **`%`** - Percentages are relative to the parent element's corresponding property. For example, `width: 50%` means half the width of the parent container. The reference property depends on what you are sizing (width refers to parent's width, but padding percentages refer to parent's width even for vertical padding).

### Special Values

+ **`auto`** - The browser calculates the value automatically based on context and available space.
+ **`0`** - Zero does not require a unit. You can write `margin: 0` instead of `margin: 0px`.

---
