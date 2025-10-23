# Fundamentals

## 1. What is CSS?

Covered [here](../../notes/css/01_fundamentals/01_introduction.md)

* The role of CSS in web development (separation of content and presentation)
* CSS syntax: selector + declaration block (property: value)
* The cascade, inheritance, and how CSS rules “win” (specificity, order, importance)

---

## 2. How to include CSS in HTML

Covered [here](../../notes/css/01_fundamentals/02_including_css.md)

* Inline styles  
* Internal styles (in a `<style>` tag)  
* External stylesheets (`<link rel="stylesheet" href="…">`)  
* Media attributes in `<link>` (e.g. `media="print"`)  

---

## 3. Selectors and Specificity

Covered [here](../../notes/css/01_fundamentals/03_selectors_and_specificity.md)

* Basic selectors: element, class, ID  
* Combinators: descendant (` `), child (`>`), adjacent sibling (`+`), general sibling (`~`)  
* Attribute selectors (e.g. `[attr=value]`, `[attr^=value]`)  
* Pseudo-classes (e.g. `:hover`, `:focus`, `:nth-child`, `:not`)  
* Pseudo-elements (e.g. `::before`, `::after`, `::first-line`)  
* Specificity rules & tie-breakers  
* `!important` (when to use, when to avoid)  
* Inheritance: which properties inherit and which don’t  

---

## 4. The Box Model

Covered [here](../../notes/css/01_fundamentals/04_box_model.md)

* Content, padding, border, margin  
* `width`, `height`, `min-width`, `max-width`, `min-height`, `max-height`  
* `box-sizing` (content-box vs border-box)  
* `overflow` and handling overflow (scroll, hidden, auto)  
* Margin collapse rules  

---

## 5. Units, Values, and Colors

Covered [here](../../notes/css/01_fundamentals/05_units_values_colors.md)

* Absolute units: `px`, `pt`, `cm`, etc.  
* Relative units: `em`, `rem`, `%`, `vw`, `vh`, `vmin`, `vmax`  
* `auto`, `inherit`, `initial`, `unset`  
* `calc()` function  
* Color formats: named colors, hex, `rgb()` / `rgba()`, `hsl()` / `hsla()`  

---

