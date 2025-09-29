# Browser Rendering Process

When you load a web page, the browser doesn’t immediately show pixels. There is a pipeline of parsing, style computations, layout, painting, compositing, JS execution, etc. Understanding this pipeline is critical for performance and for designing front‐end systems.

## Key Topics

+ [Key Definitions](#key-definitions)
+ [Stages of the Rendering Pipeline](#stages-of-the-rendering-pipeline)
    + [Reflow vs Repaint and Performance Implications](#reflow-vs-repaint-and-performance-implications)
+ [Critical Rendering Path and Render-Blocking Resources](#critical-rendering-path-and-render-blocking-resources)
+ [JavaScript Execution and Event Loop](#javascript-execution-and-event-loop)
+ [Rendering Strategies](#rendering-strategies)
+ [Best Practices](#best-practices)

---

## Key Definitions

* **DOM (Document Object Model):** A tree structure representing the HTML document’s elements, attributes, text, etc. Built by parsing HTML.
* **CSSOM (CSS Object Model):** A tree (or set of data structures) representing all the CSS rules, selectors, and computed style information. Built by parsing CSS.
* **Render Tree:** What you get when you combine the DOM & CSSOM, but only those nodes that will be visible. It ties together content + style.
* **Layout (aka Reflow):** The phase where the browser computes the exact size and position of every visible element (node) in the render tree.
* **Painting / Rasterization:** Filling in pixels for each node: drawing text, colors, backgrounds, borders, shadows, images, etc.
* **Compositing:** When parts of the page are broken into layers (often for performance, e.g. for animations, overlapping elements, GPU‐accelerated layers), compositing is the process of merging these layers into the final image displayed on screen.
* **Reflow vs. Repaint:**

  * *Reflow* means layout is recalculated; size or position has changed affecting geometry.
  * *Repaint* means something visual changed but geometry/layout doesn’t need recalculation (e.g. changing `color`, `background-color`).
* **Critical Rendering Path:** The minimal sequence of steps and essential resources that the browser must fetch / compute before it can render content to the screen. Optimizing this path improves perceived performance.
* **Event Loop & JS Execution:** How JavaScript is parsed, compiled, run; how async tasks, events, callbacks are queued and executed. JS execution can affect the DOM and CSSOM, hence affect rendering.

---

## Stages of the Rendering Pipeline

Below is a sequence of what happens, roughly, from when you request a page to when it appears to the user (for the initial load).

1. **Request & Load Resources**

   * Browser makes HTTP(s) requests for the HTML document.
   * As HTML is parsed, references to external resources (CSS, JS, images, fonts) are discovered. Some are critical, some can be deferred.

2. **HTML Parsing → DOM Construction**

   * The browser tokenizer and parser read HTML, produce tokens, build nodes. Build the DOM tree incrementally.
   * If HTML is malformed, browsers use error‐handling rules to still produce a usable DOM.

3. **CSS Parsing → CSSOM Construction**

   * CSS (inline, `<style>` tags, or external stylesheets) is downloaded and parsed.
   * CSS rules are resolved: cascading, specificity, inheritance, etc.
   * CSSOM built.

4. **JavaScript Processing / Execution (Interleaved)**

   * Scripts may modify the DOM or CSSOM.
   * If a script is synchronous and placed such that it blocks parsing (i.e., not `defer` or `async`), then parsing HTML / CSS may stop until JS loads & executes.
   * JS execution may force style recalculations, layout changes, etc.

5. **Render Tree Construction**

   * Combine DOM + CSSOM: traverse DOM, include only visible nodes.
   * For each visible node, compute final computed styles.
   * Build render tree (visibility + styles + hierarchy).

6. **Layout (Reflow)**

   * Given the render tree, determine the geometry: width, height, position of each node in relation to viewport and its parent/children.
   * This is influenced by box model, display properties, position, floats, margins/padding etc.

7. **Painting / Rasterization**

   * Actual drawing of visual parts: backgrounds, borders, text, shadows, images.
   * This may happen in layers.

8. **Compositing**

   * If layers exist (due to certain CSS properties: transforms, opacity, animations, `will-change`, fixed position elements, etc.), then browser composes (merges) the layers into a final image. Some parts may be drawn on GPU.

9. **Display / Re‐rendering (as needed)**

   * Once painted/composited, the user sees the result.
   * Afterwards, any changes (due to user interaction, script, network; e.g. lazy loading images) may trigger part of this pipeline to re‐run (style recalculation, reflow, repaint, compositing).


### Reflow vs Repaint and Performance Implications

* **Reflow** is more expensive than repaint. Because layout calculation has to traverse through parts of the tree, compute sizes & positions. If many elements or complex layout, cost increases.
* **Repaint** happens when visual style changes without affecting layout (e.g. changing color). Still expensive over large areas.
* Frequent reflows (e.g. in JS loops or with forced synchronous layout queries) are a common performance killer.

---

## Critical Rendering Path and Render-Blocking Resources

* **Critical resources** are those that block the rendering of content on the page.

  * CSS in `<head>` is render‐blocking.
  * JavaScript can be render‐blocking if it must be executed before the page can render (e.g. modifies DOM or CSSOM).
* The **Critical Rendering Path** is about minimizing the time between the request and the first meaningful paint. You want to reduce what the browser must wait for to show something useful.
* Strategies to optimize:

  * Minimize and defer non‐critical CSS / JS.
  * Use `async` or `defer` for scripts so they don’t block HTML parsing unnecessarily.
  * Inline small CSS needed for above‐the‐fold content.
  * Preload or prefetch critical resources.

---

## JavaScript Execution and Event Loop

* JavaScript runs on (usually) a single main thread in the browser responsible also for rendering tasks. If JS execution blocks this thread, rendering, layout, etc., are delayed, leading to “jank”.
* **Event loop**: JS has a mechanism of handling synchronous code, microtasks (Promises, mutation observers), macrotasks (setTimeout, I/O events, etc.). The event loop queues tasks and processes them; rendering tasks (style/reflow/paint/composite) happen in between or after suitable tasks.
* If JS code repeatedly manipulates DOM/CSSOM (especially layout affecting properties) without batching, this can force multiple layouts/repaints, hurting performance.

---

## Rendering Strategies

Different rendering strategies determine *where* and *when* the HTML for a page is produced, and each comes with unique trade-offs.

* **Static Site Generation (SSG):**
  The HTML is generated ahead of time during a build process, before any user request. This approach produces fast and cache-friendly sites, excellent for SEO and distribution through CDNs. However, it is less suitable for highly dynamic data unless combined with revalidation or client-side fetching.

* **Server-Side Rendering (SSR):**
  The server generates the HTML at the moment of each request. This ensures that content is always fresh and indexable by search engines, and users see meaningful content quickly. The drawbacks are increased server load and potentially higher latency, especially under heavy traffic.

* **Client-Side Rendering (CSR):**
  The browser initially receives a minimal HTML shell and then relies on JavaScript to build and update the DOM. This method allows highly interactive applications and smooth transitions once the application is loaded, but it can lead to slower first paint and potential SEO challenges without additional measures.

* **Hybrid Approaches (e.g., SSG + Hydration):**
  Modern frameworks often combine static generation with client-side hydration. In this model, static HTML is delivered first for performance and SEO, and then JavaScript attaches interactivity on the client side. This provides a balance between fast initial rendering and rich interactivity, though it adds implementation complexity and still requires careful bundle optimization.

---

## Best Practices

* Write CSS & JS to minimize layout changes. For animations, prefer CSS transforms / opacity rather than e.g. top/left or width changes which trigger reflow.
* Avoid querying layout properties in JS (like `offsetWidth`, `clientHeight`) over and over, especially inside loops; they can cause forced synchronous layout.
* Use `async` / `defer` for JS when possible to avoid blocking DOM parsing.
* Minimize render‐blocking CSS by inlining minimal critical CSS, splitting CSS into above‐the‐fold vs rest.
* Be aware of how images/fonts without dimensions cause layout shifts; provide width/height or aspect‐ratio.
* For SEO & performance of initial load, consider SSR or SSG where feasible. CSR is fine for highly interactive apps but you pay the cost on initial load.

---
