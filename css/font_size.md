# Web Typography and Font Size Guidelines

## 1. Introduction

Font size on a web page is not a set of random numbers; it is a design decision that affects **readability, usability, accessibility, and visual hierarchy**. Proper font sizing helps users scan content, identify structure, and comfortably read text across devices and contexts.

This document explains practical font-size choices for different elements, when to apply them, and how to implement them consistently.

---

## 2. Why Font Size Matters

* **Readability:** Text must be large enough that users can read without strain. Smaller than ~16px forces squinting or zooming.
* **Accessibility:** Guidelines (e.g., WCAG) promote scalable text, relative units, and minimum sizes to support users with vision impairments.
* **Hierarchy:** Font size establishes visual hierarchy; larger sizes draw attention; smaller sizes indicate secondary information.
* **Responsive Design:** Sizes should adapt to screen size (desktop vs mobile) to maintain comfort and usability.

---

## 3. Base Font Sizes

### 3.1 Body Text (Main Content)

* **Recommended Minimum:** `16px` (the default browser font size); comfortable for most users.
* **Preferred Range:** `16px-18px` for content-heavy pages.
* **Avoid Smaller:** Text smaller than `14px` will strain users and may fail accessibility expectations.

**Rule:** Choose a base size that ensures long paragraphs are readable without zooming or strain.

---

## 4. Typography Scale (Hierarchy)

Use a consistent scale to differentiate headings and content types.

### 4.1 Headings

Example scale:

| Element | Size Range    | Notes                                                          |
| ------- | ------------- | -------------------------------------------------------------- |
| `h1`    | `32px – 48px` | Primary page title; strongest emphasis. |
| `h2`    | `24px – 32px` | Major section titles. |
| `h3`    | `20px – 28px` | Sub-headings. |
| `h4`    | `18px – 24px` | Lower sub-sections. |
| `h5`    | `14px – 20px` | Minor headings. |
| `h6`    | `12px – 18px` | Smallest headings, less emphasis. |

**Purpose:** Larger sizes establish clear reading order and improve scan-ability. ([Design.dev][2])

---

### 4.2 Secondary Text

| Element Type          | Size Recommendation                   |
| --------------------- | ------------------------------------- |
| Captions / Footnotes  | `12px – 14px` |
| Button / UI Labels    | `16px – 18px` |
| Metadata / Timestamps | `14px – 16px` |

**Note:** Avoid text smaller than `12px` unless purely decorative; smaller sizes harm legibility.

---

## 5. Unit Choices and Responsive Typography

### 5.1 Relative Units (Best Practice)

* **`rem`:** Relative to the root (`html`) font size. Best for consistency.
* **`em`:** Relative to the parent element. Useful inside components.
* **Percent / Viewport-based:** Supports fluid scaling (`vw`, `vh`) and flexible design.

**Recommendation:** Use `rem` for core typography so users and browsers can scale text easily.

---

### 5.2 Responsive Scaling Techniques

* **Media Queries:** Adjust root font size for different screen widths.
* **Clamp Function (CSS):** Automatically scale between minimum/maximum values.

```css
h1 {
  font-size: clamp(2rem, 5vw, 3rem);
}
```

This ensures typography scales with viewport size without manual breakpoints.

---

## 6. Accessibility Considerations

### 6.1 WCAG Compliance

* **Text must be resizable up to 200%** without loss of content or function. Use relative units to support this.
* **Minimum Font Size:** `16px` is widely recommended as the lower bound for body text on accessibility grounds.

### 6.2 Contrast & Readability

* Text contrast should follow WCAG ratios: **4.5:1** for normal text and **3:1** for large text.
* Adequate line height (`1.5x` the font size) improves readability.

**Effect:** Good contrast and spacing help users focus and comprehend content faster.

---

## 7. Practical Implementation Example (CSS)

```css
html {
  font-size: 100%; /* ~16px default */
}

body {
  font-size: 1rem; /* 16px */
  line-height: 1.6;
}

h1 { font-size: 2.5rem; }  /* ~40px */
h2 { font-size: 2rem; }    /* ~32px */
h3 { font-size: 1.5rem; }  /* ~24px */
p  { font-size: 1rem; }    /* ~16px */
button, .btn { font-size: 1rem; } /* ~16px */
.small-text { font-size: 0.875rem; } /* ~14px */
```

---
