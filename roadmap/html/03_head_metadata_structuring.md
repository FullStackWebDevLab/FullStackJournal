# Structuring Metadata in `<head>`

## Tags

+ [`<title>`](../../notes/html/00_tags/title.md)
+ [`<meta>`](../../notes/html/00_tags/meta.md)
+ [`<base>`](../../notes/html/00_tags/base.md)
+ [`<link>`](../../notes/html/00_tags/link.md)
+ [`<style>`](../../notes/html/00_tags/style.md)
+ [`<script>`](../../notes/html/00_tags/script.md)
+ `<noscript>`
+ `<template>`

---

## Additional Content

### Essential Declaration Order

+ Character encoding `<meta charset>` must come first for proper parsing.
+ Viewport meta tag early for mobile rendering.
+ Document `<title>` as required core identity.
+ Required vs optional meta tags.

### Resource Loading Sequence

+ CSS before JavaScript for proper rendering.
+ Preload critical resources vs defer non-essential.
+ External stylesheets vs inline critical CSS.
+ Impact on render blocking and performance.

### Document Relationships

+ Linking to stylesheets, icons, and manifests.
+ Canonical URLs and alternate language versions.
+ Preconnects and DNS-prefetches for external domains.
+ Logical grouping: identification, rendering, SEO, social.

### Organization Principles

+ Order-dependent parsing and execution.
+ Minimizing render-blocking resources.
+ Relationship between title, description, and Open Graph tags.
+ Strategic placement of all head elements for optimal performance.

### Advanced Functionality Tags

+ Fallback content when scripts are disabled.
+ Client-side template storage and usage.
+ Conditional rendering strategies.

---
