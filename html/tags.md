# Comprehensive HTML Tags Reference

## Document Structure

### `<html>`
**Description:** The root element that encompasses all content within an HTML document. All other elements must be descendants of this element.

**Example:**
```html
<html lang="en">
  <head>...</head>
  <body>...</body>
</html>
```

### `<head>`
**Description:** Contains metadata and machine-readable information about the document, including title, scripts, and stylesheets. This content is not displayed on the page itself.

**Example:**
```html
<head>
  <meta charset="UTF-8">
  <title>Document Title</title>
</head>
```

### `<body>`
**Description:** Represents the content section of an HTML document. Only one body element may exist per document, and it contains all visible content.

**Example:**
```html
<body>
  <h1>Welcome</h1>
  <p>This is the main content.</p>
</body>
```

### `<title>`
**Description:** Defines the document's title as displayed in browser tabs and search engine results. This element must reside within the head element and contains only text.

**Example:**
```html
<title>My Website - Home Page</title>
```

## Metadata Elements

### `<meta>`
**Description:** Provides metadata that cannot be represented by other meta-related elements. Common uses include character encoding, viewport settings, and page descriptions.

**Example:**
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="A comprehensive guide">
```

### `<link>`
**Description:** Specifies relationships between the current document and external resources. Most commonly used for linking stylesheets, but also for favicons and other resources.

**Example:**
```html
<link rel="stylesheet" href="styles.css">
<link rel="icon" type="image/png" href="favicon.png">
```

### `<style>`
**Description:** Contains CSS styling information that applies to the document or specific portions thereof. The styles are embedded directly within the HTML.

**Example:**
```html
<style>
  body { font-family: Arial, sans-serif; }
  h1 { color: navy; }
</style>
```

### `<base>`
**Description:** Specifies the base URL for all relative URLs within a document. Only one base element is permitted per document.

**Example:**
```html
<base href="https://www.example.com/" target="_blank">
```

## Content Sectioning

### `<header>`
**Description:** Represents introductory content, typically containing navigational aids, logos, search forms, or heading elements.

**Example:**
```html
<header>
  <h1>Site Title</h1>
  <nav>...</nav>
</header>
```

### `<nav>`
**Description:** Defines a section containing navigation links, either within the current document or to external pages. Common examples include menus and tables of contents.

**Example:**
```html
<nav>
  <ul>
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
  </ul>
</nav>
```

### `<main>`
**Description:** Represents the dominant content of the document body. This content should be unique to the document and directly related to its central topic.

**Example:**
```html
<main>
  <article>
    <h1>Article Title</h1>
    <p>Main content...</p>
  </article>
</main>
```

### `<section>`
**Description:** Represents a generic standalone section of a document. Sections should typically contain a heading, with few exceptions.

**Example:**
```html
<section>
  <h2>Chapter 1</h2>
  <p>Content of the first chapter...</p>
</section>
```

### `<article>`
**Description:** Represents self-contained composition intended for independent distribution or reuse, such as blog posts, forum posts, or news articles.

**Example:**
```html
<article>
  <h2>Blog Post Title</h2>
  <p>Published on January 1, 2024</p>
  <p>Article content...</p>
</article>
```

### `<aside>`
**Description:** Represents content indirectly related to the main content, frequently presented as sidebars or call-out boxes.

**Example:**
```html
<aside>
  <h3>Related Links</h3>
  <ul>
    <li><a href="#">Resource 1</a></li>
  </ul>
</aside>
```

### `<footer>`
**Description:** Represents a footer for its nearest sectioning content or sectioning root, typically containing author information, copyright data, or related links.

**Example:**
```html
<footer>
  <p>&copy; 2024 Company Name. All rights reserved.</p>
</footer>
```

### `<address>`
**Description:** Indicates that the enclosed content provides contact information for a person, people, or organization.

**Example:**
```html
<address>
  Contact us at: <a href="mailto:info@example.com">info@example.com</a>
</address>
```

### `<h1>` through `<h6>`
**Description:** Represent six hierarchical levels of section headings, with h1 being the highest and h6 the lowest.

**Example:**
```html
<h1>Main Title</h1>
<h2>Subtitle</h2>
<h3>Section Heading</h3>
```

### `<hgroup>`
**Description:** Represents a heading grouped with secondary content such as subheadings, alternative titles, or taglines.

**Example:**
```html
<hgroup>
  <h1>Main Heading</h1>
  <p>A descriptive subtitle</p>
</hgroup>
```

### `<search>`
**Description:** Represents a component containing form controls or content related to performing search or filtering operations.

**Example:**
```html
<search>
  <form role="search">
    <input type="search" placeholder="Search...">
    <button type="submit">Search</button>
  </form>
</search>
```

## Text Content

### `<p>`
**Description:** Represents a paragraph. In visual media, paragraphs are typically rendered as text blocks separated by blank lines or first-line indentation.

**Example:**
```html
<p>This is a paragraph of text containing multiple sentences. It represents a discrete unit of content.</p>
```

### `<div>`
**Description:** A generic container for flow content with no inherent semantic meaning. Primarily used for styling purposes or grouping elements.

**Example:**
```html
<div class="container">
  <p>Content inside a div</p>
</div>
```

### `<span>`
**Description:** A generic inline container for phrasing content without inherent representation. Used for styling or grouping inline elements.

**Example:**
```html
<p>This is <span class="highlight">highlighted text</span> within a paragraph.</p>
```

### `<br>`
**Description:** Produces a line break in text. Useful for content where line division is significant, such as addresses or poems.

**Example:**
```html
<p>123 Main Street<br>
Anytown, ST 12345</p>
```

### `<hr>`
**Description:** Represents a thematic break between paragraph-level elements, such as a scene change in a story or topic shift within a section.

**Example:**
```html
<p>First section content...</p>
<hr>
<p>Second section content...</p>
```

### `<pre>`
**Description:** Represents preformatted text to be presented exactly as written in the HTML file, typically using a monospaced font. Whitespace is preserved.

**Example:**
```html
<pre>
function example() {
    return true;
}
</pre>
```

### `<blockquote>`
**Description:** Indicates that the enclosed text is an extended quotation, typically rendered with indentation. May include a cite attribute for the source URL.

**Example:**
```html
<blockquote cite="https://www.example.com">
  <p>This is a quotation from another source.</p>
</blockquote>
```

## Lists

### `<ul>`
**Description:** Represents an unordered list of items, typically rendered with bullet points.

**Example:**
```html
<ul>
  <li>First item</li>
  <li>Second item</li>
  <li>Third item</li>
</ul>
```

### `<ol>`
**Description:** Represents an ordered list of items, typically rendered with sequential numbers or letters.

**Example:**
```html
<ol>
  <li>First step</li>
  <li>Second step</li>
  <li>Third step</li>
</ol>
```

### `<li>`
**Description:** Represents an individual item within an ordered list, unordered list, or menu element.

**Example:**
```html
<ul>
  <li>List item content</li>
</ul>
```

### `<dl>`
**Description:** Represents a description list, enclosing groups of terms and their corresponding descriptions. Commonly used for glossaries or metadata.

**Example:**
```html
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language</dd>
  <dt>CSS</dt>
  <dd>Cascading Style Sheets</dd>
</dl>
```

### `<dt>`
**Description:** Specifies a term in a description list, used inside a dl element and typically followed by one or more dd elements.

**Example:**
```html
<dl>
  <dt>Term</dt>
  <dd>Definition of the term</dd>
</dl>
```

### `<dd>`
**Description:** Provides the description, definition, or value for the preceding term in a description list.

**Example:**
```html
<dl>
  <dt>Browser</dt>
  <dd>A software application for accessing the World Wide Web</dd>
</dl>
```

### `<menu>`
**Description:** A semantic alternative to ul, representing an unordered list of items. Browsers treat it identically to ul.

**Example:**
```html
<menu>
  <li>Menu item 1</li>
  <li>Menu item 2</li>
</menu>
```

## Inline Text Semantics

### `<a>`
**Description:** Creates a hyperlink to web pages, files, email addresses, or locations within the current page using its href attribute.

**Example:**
```html
<a href="https://www.example.com">Visit Example</a>
<a href="#section2">Jump to Section 2</a>
```

### `<strong>`
**Description:** Indicates that its contents have strong importance, seriousness, or urgency. Typically rendered in bold.

**Example:**
```html
<p>This is <strong>very important</strong> information.</p>
```

### `<em>`
**Description:** Marks text with stress emphasis. Nested em elements indicate greater degrees of emphasis. Typically rendered in italics.

**Example:**
```html
<p>I <em>really</em> need to finish this project.</p>
```

### `<b>`
**Description:** Draws attention to text without conveying additional importance. Historically rendered in boldface, but semantic elements like strong are preferred for importance.

**Example:**
```html
<p>The <b>product name</b> is clearly visible on the packaging.</p>
```

### `<i>`
**Description:** Represents text set off from normal text for some reason, such as idiomatic text, technical terms, or taxonomical designations. Traditionally rendered in italics.

**Example:**
```html
<p>The term <i>lorem ipsum</i> is commonly used in design.</p>
```

### `<mark>`
**Description:** Represents text marked or highlighted for reference purposes due to its relevance in the enclosing context.

**Example:**
```html
<p>The search found <mark>three results</mark> in the document.</p>
```

### `<small>`
**Description:** Represents side-comments and small print, such as copyright and legal text. Renders text one font size smaller by default.

**Example:**
```html
<p><small>Copyright 2024. All rights reserved.</small></p>
```

### `<del>`
**Description:** Represents text that has been deleted from a document. Useful for displaying track changes or diff information.

**Example:**
```html
<p>The price is <del>$50</del> $40.</p>
```

### `<ins>`
**Description:** Represents text that has been added to a document. Can be used alongside del to show modifications.

**Example:**
```html
<p>The meeting is <del>Tuesday</del> <ins>Wednesday</ins>.</p>
```

### `<sub>`
**Description:** Specifies inline text to be displayed as subscript for typographical reasons, rendered with a lowered baseline.

**Example:**
```html
<p>H<sub>2</sub>O is the chemical formula for water.</p>
```

### `<sup>`
**Description:** Specifies inline text to be displayed as superscript for typographical reasons, rendered with a raised baseline.

**Example:**
```html
<p>E = mc<sup>2</sup> is Einstein's famous equation.</p>
```

### `<code>`
**Description:** Displays contents as a short fragment of computer code, typically using a monospace font.

**Example:**
```html
<p>Use the <code>console.log()</code> function to output values.</p>
```

### `<kbd>`
**Description:** Represents textual user input from a keyboard, voice input, or other text entry device. Typically rendered in monospace font.

**Example:**
```html
<p>Press <kbd>Ctrl</kbd> + <kbd>C</kbd> to copy.</p>
```

### `<samp>`
**Description:** Encloses inline text representing sample output from a computer program, typically rendered in monospace font.

**Example:**
```html
<p>The program output: <samp>Hello, World!</samp></p>
```

### `<var>`
**Description:** Represents the name of a variable in a mathematical expression or programming context, typically rendered in italics.

**Example:**
```html
<p>The value of <var>x</var> must be greater than zero.</p>
```

### `<abbr>`
**Description:** Represents an abbreviation or acronym. The title attribute may provide the full expansion.

**Example:**
```html
<p><abbr title="World Wide Web">WWW</abbr> was invented by Tim Berners-Lee.</p>
```

### `<cite>`
**Description:** Marks the title of a creative work. May be in abbreviated form according to context-appropriate conventions.

**Example:**
```html
<p>As stated in <cite>The Art of Computer Programming</cite>...</p>
```

### `<dfn>`
**Description:** Indicates the term being defined within a definition phrase or sentence. The ancestor element provides the definition context.

**Example:**
```html
<p><dfn>HTML</dfn> is the standard markup language for web pages.</p>
```

### `<q>`
**Description:** Indicates that the enclosed text is a short inline quotation. Modern browsers typically surround it with quotation marks.

**Example:**
```html
<p>She said <q>Hello, world!</q> and smiled.</p>
```

### `<s>`
**Description:** Renders text with a strikethrough to represent things no longer relevant or accurate. Not appropriate for document edits; use del and ins instead.

**Example:**
```html
<p>The offer is <s>$100</s> now only $75!</p>
```

### `<u>`
**Description:** Represents inline text with a non-textual annotation, rendered by default as a simple underline. Useful for indicating spelling errors.

**Example:**
```html
<p>This word is <u class="spelling-error">mispeled</u>.</p>
```

### `<time>`
**Description:** Represents a specific period in time. May include a datetime attribute for machine-readable format.

**Example:**
```html
<p>The event starts at <time datetime="2024-01-15T19:00">7:00 PM on January 15</time>.</p>
```

### `<data>`
**Description:** Links content with a machine-readable translation using the value attribute. For time-related content, use time instead.

**Example:**
```html
<data value="398">Three hundred ninety-eight</data>
```

### `<bdi>`
**Description:** Isolates text from its surrounding content for bidirectional text algorithm purposes, useful when inserting text of unknown directionality.

**Example:**
```html
<p>User <bdi>إيان</bdi> commented on your post.</p>
```

### `<bdo>`
**Description:** Overrides the current text directionality, forcing text to render in a specified direction.

**Example:**
```html
<p><bdo dir="rtl">This text will display right-to-left</bdo></p>
```

### `<wbr>`
**Description:** Represents a word break opportunity where the browser may optionally break a line, though rules would not otherwise create a break.

**Example:**
```html
<p>Supercalifragilistic<wbr>expialidocious</p>
```

### `<ruby>`
**Description:** Represents small annotations rendered above, below, or next to base text, typically for pronunciation of East Asian characters.

**Example:**
```html
<ruby>
  漢 <rt>かん</rt>
  字 <rt>じ</rt>
</ruby>
```

### `<rt>`
**Description:** Specifies the ruby text component providing pronunciation or translation information within a ruby element.

**Example:**
```html
<ruby>東京<rt>とうきょう</rt></ruby>
```

### `<rp>`
**Description:** Provides fallback parentheses for browsers not supporting ruby annotations, wrapping the rt element.

**Example:**
```html
<ruby>
  漢字 <rp>(</rp><rt>かんじ</rt><rp>)</rp>
</ruby>
```

## Images and Multimedia

### `<img>`
**Description:** Embeds an image into the document using the src attribute. The alt attribute provides alternative text for accessibility.

**Example:**
```html
<img src="photo.jpg" alt="A scenic mountain landscape">
```

### `<figure>`
**Description:** Represents self-contained content with an optional caption, referenced as a single unit. Often used with images, illustrations, or code listings.

**Example:**
```html
<figure>
  <img src="diagram.png" alt="Process diagram">
  <figcaption>Figure 1: System Architecture</figcaption>
</figure>
```

### `<figcaption>`
**Description:** Represents a caption or legend describing the contents of its parent figure element.

**Example:**
```html
<figure>
  <img src="chart.png" alt="Sales data">
  <figcaption>Annual sales for 2024</figcaption>
</figure>
```

### `<picture>`
**Description:** Contains zero or more source elements and one img element to offer alternative image versions for different display scenarios.

**Example:**
```html
<picture>
  <source media="(min-width: 800px)" srcset="large.jpg">
  <source media="(min-width: 400px)" srcset="medium.jpg">
  <img src="small.jpg" alt="Responsive image">
</picture>
```

### `<audio>`
**Description:** Embeds sound content into documents. May contain multiple audio sources or serve as destination for streamed media.

**Example:**
```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
  Your browser does not support the audio element.
</audio>
```

### `<video>`
**Description:** Embeds a media player supporting video playback. Can also be used for audio content, though audio element may be more appropriate.

**Example:**
```html
<video width="640" height="360" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.webm" type="video/webm">
  Your browser does not support the video tag.
</video>
```

### `<source>`
**Description:** Specifies multiple media resources for picture, audio, or video elements, providing format alternatives for browser compatibility.

**Example:**
```html
<video controls>
  <source src="video.webm" type="video/webm">
  <source src="video.mp4" type="video/mp4">
</video>
```

### `<track>`
**Description:** Specifies timed text tracks for audio and video elements, formatted in WebVTT format for subtitles or captions.

**Example:**
```html
<video controls>
  <source src="movie.mp4">
  <track kind="subtitles" src="subtitles_en.vtt" srclang="en" label="English">
</video>
```

### `<map>`
**Description:** Used with area elements to define an image map, creating clickable regions on an image.

**Example:**
```html
<img src="workplace.jpg" alt="Workplace" usemap="#workmap">
<map name="workmap">
  <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
</map>
```

### `<area>`
**Description:** Defines a clickable area within an image map with predefined coordinates and hyperlink destinations.

**Example:**
```html
<map name="planetmap">
  <area shape="circle" coords="90,58,3" alt="Mercury" href="mercury.htm">
</map>
```

## Embedded Content

### `<iframe>`
**Description:** Represents a nested browsing context, embedding another HTML page into the current document.

**Example:**
```html
<iframe src="https://www.example.com" width="600" height="400" title="External content">
</iframe>
```

### `<embed>`
**Description:** Embeds external content at a specified point, provided by external applications or interactive content sources.

**Example:**
```html
<embed src="animation.swf" width="400" height="300" type="application/x-shockwave-flash">
```

### `<object>`
**Description:** Represents an external resource treated as an image, nested browsing context, or plugin-handled resource.

**Example:**
```html
<object data="document.pdf" type="application/pdf" width="600" height="800">
  <p>Alternative content if PDF cannot be displayed</p>
</object>
```

### `<canvas>`
**Description:** Container element for rendering graphics and animations dynamically using JavaScript, via Canvas API or WebGL API.

**Example:**
```html
<canvas id="myCanvas" width="400" height="200">
  Your browser does not support the canvas element.
</canvas>
```

### `<svg>`
**Description:** Container defining a new coordinate system and viewport for Scalable Vector Graphics, used as the outermost SVG element.

**Example:**
```html
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" fill="blue" />
</svg>
```

### `<math>`
**Description:** The top-level element in MathML for representing mathematical notation and capturing both structure and content.

**Example:**
```html
<math>
  <mrow>
    <mi>x</mi>
    <mo>=</mo>
    <mfrac>
      <mn>1</mn>
      <mn>2</mn>
    </mfrac>
  </mrow>
</math>
```

## Tables

### `<table>`
**Description:** Represents tabular data in a two-dimensional structure comprising rows and columns of cells.

**Example:**
```html
<table>
  <tr>
    <th>Header 1</th>
    <th>Header 2</th>
  </tr>
  <tr>
    <td>Data 1</td>
    <td>Data 2</td>
  </tr>
</table>
```

### `<caption>`
**Description:** Specifies the caption or title of a table, appearing immediately after the opening table tag.

**Example:**
```html
<table>
  <caption>Monthly Sales Report</caption>
  <tr><th>Month</th><th>Sales</th></tr>
</table>
```

### `<thead>`
**Description:** Encapsulates table rows comprising the head of a table, containing column header information.

**Example:**
```html
<table>
  <thead>
    <tr><th>Product</th><th>Price</th></tr>
  </thead>
  <tbody>...</tbody>
</table>
```

### `<tbody>`
**Description:** Encapsulates table rows comprising the main data body of the table.

**Example:**
```html
<table>
  <tbody>
    <tr><td>Item 1</td><td>$10</td></tr>
    <tr><td>Item 2</td><td>$20</td></tr>
  </tbody>
</table>
```

### `<tfoot>`
**Description:** Encapsulates table rows comprising the footer of a table, typically containing column summaries.

**Example:**
```html
<table>
  <tfoot>
    <tr><td>Total</td><td>$100</td></tr>
  </tfoot>
</table>
```

### `<tr>`
**Description:** Defines a row of cells within a table, containing td (data cells) and th (header cells) elements.

**Example:**
```html
<tr>
  <td>Cell 1</td>
  <td>Cell 2</td>
  <td>Cell 3</td>
</tr>
```

### `<th>`
**Description:** Defines a cell as a header for a group of table cells. The scope and headers attributes define the relationship.

**Example:**
```html
<tr>
  <th scope="col">Name</th>
  <th scope="col">Age</th>
</tr>
```

### `<td>`
**Description:** Defines a cell within a table containing data, as a child of a tr element.

**Example:**
```html
<tr>
  <td>John Doe</td>
  <td>30</td>
</tr>
```

### `<colgroup>`
**Description:** Defines a group of columns within a table for applying common styling or attributes.

**Example:**
```html
<table>
  <colgroup>
    <col span="2" style="background-color: yellow">
  </colgroup>
  <tr><td>Data</td><td>Data</td></tr>
</table>
```

### `<col>`
**Description:** Defines one or more columns within a colgroup element. Valid only as a child of colgroup without a span attribute.

**Example:**
```html
<colgroup>
  <col style="width: 50%">
  <col style="width: 50%">
</colgroup>
```

## Forms

### `<form>`
**Description:** Represents a document section containing interactive controls for submitting information to a server.

**Example:**
```html
<form action="/submit" method="post">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name">
  <button type="submit">Submit</button>
</form>
```

### `<input>`
**Description:** Creates interactive controls for web-based forms accepting user data. Behavior varies significantly based on the type attribute.

**Example:**
```html
<input type="text" name="username" placeholder="Enter username">
<input type="email" name="email" required>
<input type="checkbox" name="subscribe" value="newsletter">
```

### `<label>`
**Description:** Represents a caption for a user interface item, associating with form controls via the for attribute.

**Example:**
```html
<label for="email">Email Address:</label>
<input type="email" id="email" name="email">
```

### `<button>`
**Description:** An interactive element activated by users to perform actions such as form submission or dialog opening.

**Example:**
```html
<button type="submit">Send Form</button>
<button type="button" onclick="alert('Clicked')">Click Me</button>
```

### `<textarea>`
**Description:** Represents a multi-line plain-text editing control for free-form text input such as comments or feedback.

**Example:**
```html
<label for="message">Message:</label>
<textarea id="message" name="message" rows="4" cols="50">
Default text content
</textarea>
```

### `<select>`
**Description:** Represents a control providing a menu of options from which users may choose.

**Example:**
```html
<label for="country">Country:</label>
<select id="country" name="country">
  <option value="us">United States</option>
  <option value="uk">United Kingdom</option>
  <option value="ca">Canada</option>
</select>
```

### `<option>`
**Description:** Defines an item within a select, optgroup, or datalist element, representing menu choices.

**Example:**
```html
<select>
  <option value="1">Option 1</option>
  <option value="2" selected>Option 2</option>
</select>
```

### `<optgroup>`
**Description:** Creates a grouping of options within a select element for better organization.

**Example:**
```html
<select>
  <optgroup label="Fruits">
    <option>Apple</option>
    <option>Banana</option>
  </optgroup>
  <optgroup label="Vegetables">
    <option>Carrot</option>
  </optgroup>
</select>
```

### `<datalist>`
**Description:** Contains a set of option elements representing suggested values for other controls, typically used with input elements.

**Example:**
```html
<input list="browsers" name="browser">
<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Safari">
</datalist>
```

### `<fieldset>`
**Description:** Groups several controls and labels within a web form, typically with a border.

**Example:**
```html
<fieldset>
  <legend>Personal Information</legend>
  <label for="fname">First name:</label>
  <input type="text" id="fname" name="fname">
</fieldset>
```

### `<legend>`
**Description:** Represents a caption for the content of its parent fieldset element.

**Example:**
```html
<fieldset>
  <legend>Contact Details</legend>
  <input type="email" name="email">
</fieldset>
```

### `<progress>`
**Description:** Displays an indicator showing task completion progress, typically rendered as a progress bar.

**Example:**
```html
<label for="file">Download progress:</label>
<progress id="file" value="70" max="100">70%</progress>
```

### `<meter>`
**Description:** Represents a scalar value within a known range or fractional value, such as disk usage or relevance ratings.

**Example:**
```html
<label for="fuel">Fuel level:</label>
<meter id="fuel" min="0" max="100" low="25" high="75" optimum="80" value="50">
  50 out of 100
</meter>
```

### `<output>`
**Description:** Container element for displaying the results of calculations or user actions performed by site or application.

**Example:**
```html
<form oninput="result.value=parseInt(a.value)+parseInt(b.value)">
  <input type="number" id="a" value="50"> +
  <input type="number" id="b" value="50"> =
  <output name="result" for="a b">100</output>
</form>
```

## Scripting

### `<script>`
**Description:** Embeds or references executable code or data, typically JavaScript. Can also be used with WebGL GLSL or JSON.

**Example:**
```html
<script src="script.js"></script>
<script>
  console.log('Inline JavaScript');
</script>
```

### `<noscript>`
**Description:** Defines content to display when JavaScript is disabled or unsupported by the browser.

**Example:**
```html
<noscript>
  <p>This page requires JavaScript. Please enable it in your browser.</p>
</noscript>
```

## Interactive Elements

### `<details>`
**Description:** Creates a disclosure widget where information is visible only when toggled to an open state. Must contain a summary element.

**Example:**
```html
<details>
  <summary>More Information</summary>
  <p>Here are the additional details that can be expanded or collapsed.</p>
</details>
```

### `<summary>`
**Description:** Specifies a summary, caption, or legend for a details element's disclosure box. Clicking it toggles the details state.

**Example:**
```html
<details>
  <summary>Click to expand</summary>
  <p>Hidden content appears here.</p>
</details>
```

### `<dialog>`
**Description:** Represents a dialog box or interactive component such as alerts, inspectors, or modal subwindows.

**Example:**
```html
<dialog id="myDialog">
  <p>This is a dialog box</p>
  <button onclick="document.getElementById('myDialog').close()">Close</button>
</dialog>
```

## Web Components

### `<template>`
**Description:** A mechanism for holding HTML not rendered immediately upon page load but instantiable later via JavaScript.

**Example:**
```html
<template id="myTemplate">
  <div class="card">
    <h2>Title</h2>
    <p>Content</p>
  </div>
</template>
```

### `<slot>`
**Description:** A placeholder within a web component for custom markup, enabling separate DOM tree creation and presentation.

**Example:**
```html
<template id="element-template">
  <style>p { color: blue; }</style>
  <p><slot name="text">Default text</slot></p>
</template>
```

## Formatting (Stylistic)

### `<b>` (revisited)
**Description:** Draws attention to text without semantic importance. Use strong for importance or CSS for pure styling.

**Example:**
```html
<p>The <b>product specification</b> includes detailed measurements.</p>
```

### `<i>` (revisited)
**Description:** Differentiates text for idiomatic, technical, or taxonomic reasons. Historically italicized but meaning is semantic.

**Example:**
```html
<p>The species <i>Homo sapiens</i> evolved in Africa.</p>
```

### `<u>` (revisited)
**Description:** Indicates non-textual annotation such as misspelled words, proper names in Chinese text, or other stylistic differentiation.

**Example:**
```html
<p>The word <u>recieve</u> is commonly misspelled.</p>
```

## Additional Specialized Elements

### `<selectedcontent>`
**Description:** Displays the content of the currently selected option inside a closed select element. (Experimental feature)

**Example:**
```html
<select>
  <selectedcontent></selectedcontent>
  <option>Option 1</option>
  <option>Option 2</option>
</select>
```

### `<fencedframe>`
**Description:** Represents a nested browsing context similar to iframe but with enhanced privacy features. (Experimental feature)

**Example:**
```html
<fencedframe src="https://example.com/content"></fencedframe>
```

## Deprecated Elements (Historical Reference)

### `<font>` (Deprecated)
**Description:** Previously defined font size, color, and face. Replaced by CSS styling properties.

**Example (Do not use):**
```html
<font color="red" size="5" face="Arial">Styled text</font>
```

### `<center>` (Deprecated)
**Description:** Previously centered content horizontally. Replaced by CSS text-align property.

**Example (Do not use):**
```html
<center>Centered content</center>
```

### `<marquee>` (Deprecated)
**Description:** Previously created scrolling text areas. Replaced by CSS animations.

**Example (Do not use):**
```html
<marquee>Scrolling text</marquee>
```

### `<frame>` and `<frameset>` (Deprecated)
**Description:** Previously created frame-based layouts. Replaced by iframe and modern layout techniques.

**Example (Do not use):**
```html
<frameset cols="50%,50%">
  <frame src="page1.html">
  <frame src="page2.html">
</frameset>
```

---

## Best Practices

1. **Semantic HTML**: Utilize elements based on their semantic meaning rather than visual presentation.
2. **Accessibility**: Always include alt attributes for images and proper labeling for form controls.
3. **Validation**: Ensure HTML validates against W3C standards for cross-browser compatibility.
4. **Modern Standards**: Avoid deprecated elements and attributes; use CSS for styling.
5. **Structure**: Maintain proper nesting and hierarchy of elements for document structure.
6. **SEO Optimization**: Use appropriate heading levels and semantic elements for search engine optimization.

---
