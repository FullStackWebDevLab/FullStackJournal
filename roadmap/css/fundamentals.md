## CSS Fundamentals — Topics Checklist

### 1. Introduction & Overview

* What CSS is (Cascading Style Sheets)
* Role of CSS in the HTML / web stack
* How CSS is applied / interpreted by browsers
* Default (user agent) stylesheet concept

### 2. CSS Syntax & Structure

* Rule / ruleset: selector + declaration block
* Declarations: property : value
* Declaration block delimiters `{ … }` and semicolons `;`
* Comments in CSS (`/* comment */`)
* Shorthand vs longhand properties

### 3. How to Include CSS in HTML

* Inline styles (`style` attribute)
* Internal styles (within `<style>` tag in HTML)
* External stylesheets (`<link rel="stylesheet" href="…">`)
* Media types / media attributes (e.g. `media="print"`)
* Order of CSS files / cascade impact

### 4. Selectors & Targeting Elements

* Type / element selectors (e.g. `h1`, `p`)
* Class selectors (`.classname`)
* ID selectors (`#idname`)
* Descendant combinator (space)
* Child combinator (`>`)
* Adjacent sibling (`+`) and general sibling (`~`)
* Grouping selectors (comma)
* Attribute selectors (e.g. `[attr]`, `[attr=value]`, `[attr^=value]`)
* Pseudo-classes (`:hover`, `:focus`, `:nth-child`, `:first-child`, `:not`, etc.)
* Pseudo-elements (`::before`, `::after`, `::first-line`, `::first-letter`)

### 5. Specificity, Inheritance & Cascade

* The cascade: how multiple rules compete
* Source order precedence
* Specificity calculation (IDs > classes > elements)
* `!important` usage and drawbacks
* CSS inheritance: which properties inherit by default, and how to override

### 6. The Box Model & Element Sizing

* Content, padding, border, margin layers
* How total size is computed (content + padding + border + margin)
* `box-sizing` property: `content-box` vs `border-box`
* Width / height properties, `min-` / `max-`
* Margin collapsing rules
* Overflow (`overflow: visible | hidden | scroll | auto`)

### 7. Units, Values & Types

* Length units: `px`, `em`, `rem`, `%`, `vw`, `vh`, `vmin`, `vmax`
* Relative vs absolute units
* Zero / `auto` / `inherit` / `initial` / `unset` keywords
* Functions in CSS: `calc()`, `var()` (custom properties)
* Numeric values, unitless values, percentages
* Color value types: named colors, hex, `rgb()` / `rgba()`, `hsl()` / `hsla()`

### 8. Display & Visibility

* `display` property: `block`, `inline`, `inline-block`, `none`, `inline-flex`, etc.
* How each display type behaves (flow, width, height)
* `visibility` property
* Replacing / overriding display behavior

### 9. Positioning & Layout in the Flow

* Position property: `static`, `relative`, `absolute`, `fixed`, `sticky`
* Offsets: `top`, `right`, `bottom`, `left`
* How positioned elements affect (or don’t) normal document flow
* `z-index` and stacking contexts
* Centering techniques (horizontal, vertical)

### 10. Backgrounds, Borders & Styling Decorations

* Background properties: `background-color`, `background-image`
* Background positioning, repeating, size, attachment
* Shorthand `background`
* Border properties: width, style, color, shorthand
* `border-radius` for rounded corners
* Box shadows (`box-shadow`) and text shadows (`text-shadow`)

### 11. Styling Basic Elements & Forms

* Default styling of HTML elements (headings, paragraphs, list elements, links)
* Reset / normalize CSS (to counter browser defaults)
* Styling lists (bullets, nested lists)
* Table basics: borders, spacing, cell padding, captions
* Basic form control styling: input, textarea, select, button
* Using `appearance: none` to override native styling where possible

### 12. Overflow & Clipping

* How content that overflows its container is handled
* `overflow-x` / `overflow-y`
* `clip-path` (basic use)
* `white-space` (wrapping, no wrap)

### 13. Debugging & Tools

* Browser Developer Tools: inspect styles, live editing, toggling rules
* Inspecting computed styles, box model view
* Using “toggle off” or disabling rules to find conflicting styles
* CSS validator / syntax checking
* Experiments by editing CSS live to see effect

---
