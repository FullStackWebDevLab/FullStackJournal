# HTML Tag-Specific Attributes Reference

## `<a>`
- **href**: Specifies the URL of the linked resource
- **target**: Defines where to open the linked document (_blank, _self, _parent, _top)
- **download**: Prompts the user to download the linked resource with optional filename
- **rel**: Specifies the relationship between current and linked document
- **hreflang**: Indicates the language of the linked resource
- **type**: Specifies the MIME type of the linked resource
- **ping**: Space-separated list of URLs to be notified when the link is followed
- **referrerpolicy**: Controls the referrer information sent with requests

## `<area>`
- **alt**: Alternative text for the area
- **coords**: Coordinates defining the clickable area shape
- **shape**: Shape of the area (default, rect, circle, poly)
- **href**: URL of the linked resource
- **target**: Where to display the linked URL
- **download**: Prompts download of the target
- **ping**: URLs to notify when link is followed
- **rel**: Relationship between current and linked document
- **referrerpolicy**: Referrer policy for the link

## `<audio>`
- **src**: URL of the audio file
- **controls**: Displays audio controls (play, pause, volume)
- **autoplay**: Automatically begins playback when ready
- **loop**: Repeats the audio indefinitely
- **muted**: Initially mutes the audio
- **preload**: Hints how much buffering is needed (none, metadata, auto)
- **crossorigin**: CORS settings for the audio resource (anonymous, use-credentials)

## `<base>`
- **href**: Base URL for all relative URLs in the document
- **target**: Default target for all hyperlinks and forms

## `<blockquote>`
- **cite**: URL of the quotation source

## `<button>`
- **type**: Button behavior type (submit, reset, button)
- **name**: Name of the button for form submission
- **value**: Value associated with the button name
- **disabled**: Disables the button
- **form**: Associates button with a form element by ID
- **formaction**: URL for form submission (overrides form action)
- **formenctype**: Encoding type for form data (overrides form enctype)
- **formmethod**: HTTP method for submission (overrides form method)
- **formnovalidate**: Bypasses form validation on submission
- **formtarget**: Where to display response (overrides form target)
- **popovertarget**: ID of popover element to control
- **popovertargetaction**: Action to perform on popover (toggle, show, hide)

## `<canvas>`
- **width**: Width of the canvas in pixels
- **height**: Height of the canvas in pixels

## `<col>`
- **span**: Number of columns the element should span

## `<colgroup>`
- **span**: Number of columns in the group

## `<data>`
- **value**: Machine-readable translation of the content

## `<del>`
- **cite**: URL explaining the reason for deletion
- **datetime**: Date and time when the text was deleted

## `<details>`
- **open**: Indicates whether details are visible on page load

## `<dialog>`
- **open**: Indicates whether the dialog is active and can be interacted with

## `<embed>`
- **src**: URL of the embedded resource
- **type**: MIME type of the embedded content
- **width**: Width of the embedded content
- **height**: Height of the embedded content

## `<fieldset>`
- **disabled**: Disables all form controls within the fieldset
- **form**: Associates fieldset with a form element by ID
- **name**: Name of the fieldset for scripting purposes

## `<form>`
- **action**: URL where form data is sent on submission
- **method**: HTTP method for sending form data (get, post, dialog)
- **enctype**: Encoding type for form data (application/x-www-form-urlencoded, multipart/form-data, text/plain)
- **target**: Where to display the response (_blank, _self, _parent, _top)
- **novalidate**: Bypasses form validation on submission
- **autocomplete**: Whether the form should have autocomplete enabled (on, off)
- **name**: Name of the form for scripting access
- **rel**: Relationship between current document and linked resource
- **accept-charset**: Character encodings accepted by the server

## `<iframe>`
- **src**: URL of the page to embed
- **srcdoc**: Inline HTML content to display
- **name**: Name of the iframe for targeting
- **width**: Width of the iframe
- **height**: Height of the iframe
- **sandbox**: Enables restrictions on iframe content (various tokens)
- **allow**: Permissions policy for features
- **allowfullscreen**: Allows fullscreen mode via requestFullscreen()
- **loading**: Lazy loading behavior (eager, lazy)
- **referrerpolicy**: Referrer policy for requests

## `<img>`
- **src**: URL of the image
- **alt**: Alternative text for the image
- **width**: Intrinsic width of the image in pixels
- **height**: Intrinsic height of the image in pixels
- **loading**: Loading behavior (eager, lazy)
- **decoding**: Image decoding hint (sync, async, auto)
- **srcset**: Set of image sources for responsive images
- **sizes**: Image sizes for different viewport widths
- **crossorigin**: CORS settings (anonymous, use-credentials)
- **usemap**: Associates image with a map element
- **ismap**: Indicates image is a server-side image map
- **referrerpolicy**: Referrer policy for image requests
- **fetchpriority**: Priority for fetching the image (high, low, auto)

## `<input>`
- **type**: Type of input control (text, password, email, number, checkbox, radio, file, submit, etc.)
- **name**: Name of the input for form submission
- **value**: Initial value of the input
- **placeholder**: Hint text displayed when empty
- **required**: Indicates the field must be filled
- **disabled**: Disables the input
- **readonly**: Makes the input read-only
- **maxlength**: Maximum number of characters allowed
- **minlength**: Minimum number of characters required
- **min**: Minimum value for numeric/date inputs
- **max**: Maximum value for numeric/date inputs
- **step**: Increment value for numeric inputs
- **pattern**: Regular expression for validation
- **autocomplete**: Autocomplete behavior for the field
- **autofocus**: Automatically focuses the input on page load
- **form**: Associates input with a form by ID
- **formaction**: URL for form submission (type=submit/image only)
- **formenctype**: Encoding type override (type=submit/image only)
- **formmethod**: HTTP method override (type=submit/image only)
- **formnovalidate**: Bypasses validation (type=submit/image only)
- **formtarget**: Target override (type=submit/image only)
- **list**: ID of datalist element for suggestions
- **multiple**: Allows multiple values (email, file types)
- **accept**: File types accepted (type=file only)
- **capture**: Media capture method (type=file only)
- **checked**: Pre-selects checkbox or radio button
- **size**: Visible width of the input
- **src**: Image URL (type=image only)
- **alt**: Alternative text (type=image only)
- **width**: Image width (type=image only)
- **height**: Image height (type=image only)
- **dirname**: Enables submission of text directionality
- **popovertarget**: ID of popover to control
- **popovertargetaction**: Popover action (toggle, show, hide)

## `<ins>`
- **cite**: URL explaining the reason for insertion
- **datetime**: Date and time when the text was inserted

## `<label>`
- **for**: ID of the form control the label is associated with

## `<li>`
- **value**: Ordinal value of the list item (in ordered lists)

## `<link>`
- **href**: URL of the linked resource
- **rel**: Relationship between current and linked document
- **type**: MIME type of the linked resource
- **media**: Media query for which the resource is optimized
- **sizes**: Sizes of icons (when rel="icon")
- **as**: Type of content being loaded (when rel="preload")
- **crossorigin**: CORS mode for the request
- **referrerpolicy**: Referrer policy for requests
- **integrity**: Subresource integrity hash for verification
- **hreflang**: Language of the linked resource
- **disabled**: Disables the linked stylesheet
- **fetchpriority**: Priority hint for fetching (high, low, auto)
- **blocking**: Indicates resource blocks rendering

## `<map>`
- **name**: Name of the image map for referencing

## `<meta>`
- **name**: Metadata name (viewport, description, keywords, author, etc.)
- **content**: Value associated with name or http-equiv
- **http-equiv**: Pragma directive (content-type, refresh, etc.)
- **charset**: Character encoding declaration for the document

## `<meter>`
- **value**: Current numeric value
- **min**: Lower bound of the range
- **max**: Upper bound of the range
- **low**: Upper bound of the low range
- **high**: Lower bound of the high range
- **optimum**: Optimal value within the range
- **form**: Associates meter with a form by ID

## `<object>`
- **data**: URL of the resource
- **type**: MIME type of the resource
- **name**: Name of the object for form submission
- **form**: Associates object with a form by ID
- **width**: Width of the object
- **height**: Height of the object
- **usemap**: Associates object with a map element

## `<ol>`
- **reversed**: Reverses the numbering order
- **start**: Starting value for numbering
- **type**: Numbering type (1, a, A, i, I)

## `<optgroup>`
- **disabled**: Disables all options in the group
- **label**: Label for the option group

## `<option>`
- **value**: Value submitted when selected
- **selected**: Pre-selects the option
- **disabled**: Disables the option
- **label**: Label for the option (alternative to text content)

## `<output>`
- **for**: Space-separated list of IDs of elements that contributed to the output
- **form**: Associates output with a form by ID
- **name**: Name of the output for form submission

## `<param>`
- **name**: Name of the parameter
- **value**: Value of the parameter

## `<progress>`
- **value**: Current progress value
- **max**: Maximum value representing completion

## `<q>`
- **cite**: URL of the quotation source

## `<script>`
- **src**: URL of external script file
- **type**: MIME type of the script (text/javascript, module, importmap, etc.)
- **async**: Executes script asynchronously
- **defer**: Defers script execution until page is parsed
- **crossorigin**: CORS mode for the script
- **integrity**: Subresource integrity hash
- **referrerpolicy**: Referrer policy for script requests
- **nomodule**: Prevents execution in browsers supporting ES6 modules
- **blocking**: Indicates script blocks rendering
- **fetchpriority**: Priority hint for fetching

## `<select>`
- **name**: Name for form submission
- **multiple**: Allows multiple selections
- **size**: Number of visible options
- **disabled**: Disables the select control
- **required**: Requires a selection before form submission
- **form**: Associates select with a form by ID
- **autocomplete**: Autocomplete behavior

## `<source>`
- **src**: URL of the media resource
- **type**: MIME type of the resource
- **srcset**: Image sources for responsive images (picture context)
- **sizes**: Image sizes for different viewports (picture context)
- **media**: Media query for which the resource applies (picture context)
- **width**: Intrinsic width (picture context)
- **height**: Intrinsic height (picture context)

## `<style>`
- **media**: Media query for which styles apply
- **blocking**: Indicates stylesheet blocks rendering

## `<td>`
- **colspan**: Number of columns the cell spans
- **rowspan**: Number of rows the cell spans
- **headers**: Space-separated list of header cell IDs

## `<textarea>`
- **name**: Name for form submission
- **rows**: Visible number of text rows
- **cols**: Visible width in average character widths
- **maxlength**: Maximum number of characters
- **minlength**: Minimum number of characters
- **placeholder**: Hint text when empty
- **required**: Requires content before submission
- **disabled**: Disables the textarea
- **readonly**: Makes textarea read-only
- **autocomplete**: Autocomplete behavior
- **autofocus**: Automatically focuses on page load
- **form**: Associates textarea with a form by ID
- **wrap**: How text wrapping is handled (soft, hard)
- **dirname**: Enables submission of text directionality

## `<th>`
- **colspan**: Number of columns the cell spans
- **rowspan**: Number of rows the cell spans
- **scope**: Specifies cells the header applies to (row, col, rowgroup, colgroup)
- **abbr**: Abbreviated description of the header cell
- **headers**: Space-separated list of header cell IDs

## `<time>`
- **datetime**: Machine-readable date/time value

## `<track>`
- **src**: URL of the track file
- **kind**: Type of text track (subtitles, captions, descriptions, chapters, metadata)
- **srclang**: Language of the track text
- **label**: User-visible title for the track
- **default**: Indicates the default track

## `<video>`
- **src**: URL of the video file
- **controls**: Displays video controls
- **autoplay**: Automatically begins playback
- **loop**: Repeats the video indefinitely
- **muted**: Initially mutes the video
- **preload**: Buffering hint (none, metadata, auto)
- **poster**: URL of image to show before playback
- **width**: Width of the video player
- **height**: Height of the video player
- **crossorigin**: CORS settings (anonymous, use-credentials)
- **playsinline**: Plays inline on mobile devices
- **disablepictureinpicture**: Prevents picture-in-picture mode
- **disableremoteplayback**: Prevents remote playback

## `<html>`
- **xmlns**: XML namespace for XHTML documents

## `<body>`, `<head>`, `<title>`, `<div>`, `<span>`, `<p>`, `<section>`, `<article>`, `<nav>`, `<aside>`, `<header>`, `<footer>`, `<main>`, `<figure>`, `<figcaption>`, `<address>`, `<h1>`-`<h6>`, `<ul>`, `<dl>`, `<dt>`, `<dd>`, `<hr>`, `<pre>`, `<code>`, `<samp>`, `<kbd>`, `<var>`, `<mark>`, `<small>`, `<strong>`, `<em>`, `<b>`, `<i>`, `<u>`, `<s>`, `<sub>`, `<sup>`, `<abbr>`, `<cite>`, `<dfn>`, `<bdi>`, `<bdo>`, `<br>`, `<wbr>`, `<ruby>`, `<rt>`, `<rp>`, `<caption>`, `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<colgroup>`, `<legend>`, `<datalist>`, `<menu>`, `<hgroup>`, `<search>`, `<noscript>`, `<template>`, `<slot>`, `<summary>`
These elements have no specific attributes beyond global attributes.
