# `<video>`

## Key Topics

+ [Definition and Purpose](#definition-and-purpose)
+ [Syntax and Variants](#syntax-and-variants)
+ [Attributes](#attributes)
+ [Content Model](#content-model)
+ [Context](#context)
+ [Behavior and Semantics](#behavior-and-semantics)
+ [Examples](#examples)
+ [Notes](#notes)

---

## Definition and Purpose

The `<video>` element embeds video content in HTML documents, providing native video playback capabilities without requiring external plugins. It enables the integration of movies, clips, tutorials, presentations, and other video media directly into web pages, with built-in controls for play, pause, volume, fullscreen, and seeking, while supporting multiple video formats and accessibility features.

---

## Syntax & Variants

+ **Standard syntax**: `<video>...</video>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps `<source>` elements, `<track>` elements, and fallback content
+ **No self-closing variant**: Must be properly closed
+ **HTML5 introduction**: Added in HTML5 to provide native video support

---

## Attributes

+ **Core attributes**:
  - `src` (optional): URL of the video file to embed
  - `controls` (optional): Shows browser's default video controls
  - `autoplay` (optional): Automatically begins playback when ready
  - `loop` (optional): Replays video from beginning when finished
  - `muted` (optional): Default state is muted
  - `preload` (optional): Hints how much to preload (`none`, `metadata`, `auto`)
  - `poster` (optional): URL of image to show before video plays
  - `width`/`height` (optional): Display dimensions in CSS pixels
  - `crossorigin` (optional): CORS settings for the video file
  - `playsinline` (optional): Prevents fullscreen on iOS devices
+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional, but `controls` is typically needed for user interaction

---

## Content Model

+ **Permitted content**:
  - Zero or more `<source>` elements
  - Zero or more `<track>` elements for subtitles/captions
  - Fallback content for unsupported browsers
  - Transparent content model when has `src` attribute
+ **Source order**: Browser uses first supported `<source>` element
+ **Fallback content**: Displayed if browser doesn't support `<video>` element

---

## Context

+ **Valid parents**: Any element that accepts embedded content or flow content
+ **Common locations**:
  - Within `<article>`, `<section>` for content videos
  - Within `<figure>` for captioned video content
  - Within `<div>` containers for video players
  - In tutorials, product demos, entertainment sites
+ **Embedded content**: Treated as replaced element in document flow

---

## Behavior and Semantics

+ **Default display**: Inline-level element
+ **Default styling**:
  - Varies by browser for controls
  - Typically `display: inline`
  - Intrinsic dimensions based on video resolution
+ **Playback behavior**:
  - Supports play, pause, seek, volume, fullscreen controls
  - Buffers video data as needed
  - Respects autoplay policies (often blocked without user interaction)
+ **Semantic meaning**:
  - Represents video content
  - Screen readers may announce as "video" or "media"
  - Provides video context for assistive technologies
+ **Accessibility**: Supports text tracks for captions, subtitles, and descriptions

---

## Examples

**Basic video with controls:**
```html
<video controls>
  <source src="video.mp4" type="video/mp4">
  <source src="video.webm" type="video/webm">
  Your browser does not support the video tag.
</video>
```

**Video with poster and dimensions:**
```html
<video controls width="640" height="360" poster="thumbnail.jpg">
  <source src="presentation.mp4" type="video/mp4">
  <source src="presentation.webm" type="video/webm">
  <p>Your browser doesn't support HTML5 video. 
     <a href="presentation.mp4">Download the video</a> instead.</p>
</video>
```

**Video with multiple tracks for accessibility:**
```html
<video controls width="800" height="450">
  <source src="tutorial.mp4" type="video/mp4">
  <source src="tutorial.webm" type="video/webm">
  <track kind="subtitles" src="subs-en.vtt" srclang="en" label="English" default>
  <track kind="subtitles" src="subs-es.vtt" srclang="es" label="Español">
  <track kind="captions" src="caps-en.vtt" srclang="en" label="English Captions">
  <track kind="chapters" src="chapters.vtt" srclang="en">
</video>
```

**Autoplaying muted video (for backgrounds):**
```html
<video autoplay muted loop playsinline poster="background-poster.jpg">
  <source src="background-video.mp4" type="video/mp4">
  <source src="background-video.webm" type="video/webm">
</video>
```

**Custom video player with JavaScript:**
```html
<video id="custom-video" preload="metadata" poster="preview.jpg">
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.webm" type="video/webm">
</video>

<div class="custom-controls">
  <button id="play">Play</button>
  <button id="pause">Pause</button>
  <input type="range" id="progress" min="0" max="100" value="0">
  <input type="range" id="volume" min="0" max="1" step="0.1" value="1">
  <button id="fullscreen">Fullscreen</button>
</div>
```

**Video within figure with caption:**
```html
<figure>
  <video controls width="640" height="360">
    <source src="demo.mp4" type="video/mp4">
    <source src="demo.webm" type="video/webm">
  </video>
  <figcaption>Video 1: Product demonstration showing key features and usage</figcaption>
</figure>
```

**Responsive video container:**
```html
<div class="video-container">
  <video controls preload="metadata" 
         poster="video-poster.jpg"
         style="width: 100%; height: auto;">
    <source src="responsive-video.mp4" type="video/mp4">
    <source src="responsive-video.webm" type="video/webm">
    <track kind="subtitles" src="subs.vtt" srclang="en" label="English">
  </video>
</div>
```

**Multiple video formats with fallback:**
```html
<video controls width="800" height="450" preload="auto">
  <!-- Modern formats -->
  <source src="video.av1.mp4" type="video/mp4; codecs=av01.0.05M.08">
  <source src="video.vp9.webm" type="video/webm; codecs=vp9">
  
  <!-- Standard formats -->
  <source src="video.h264.mp4" type="video/mp4">
  <source src="video.vp8.webm" type="video/webm">
  <source src="video.ogg" type="video/ogg">
  
  <!-- Fallback options -->
  <object data="flash-player.swf" type="application/x-shockwave-flash">
    <param name="movie" value="video.mp4">
    <p>Download the <a href="video.mp4">MP4 video file</a>.</p>
  </object>
</video>
```

**Video with detailed attributes:**
```html
<video id="main-video"
       controls
       width="960"
       height="540"
       poster="video-preview.jpg"
       preload="metadata"
       crossorigin="anonymous"
       playsinline>
  <source src="https://cdn.example.com/videos/main.mp4" type="video/mp4">
  <source src="https://cdn.example.com/videos/main.webm" type="video/webm">
  <track kind="subtitles" src="captions-en.vtt" srclang="en" label="English" default>
  <track kind="subtitles" src="captions-fr.vtt" srclang="fr" label="Français">
  <p>Your browser doesn't support HTML5 video. 
     Please <a href="https://cdn.example.com/videos/main.mp4">download the MP4 file</a>.</p>
</video>
```

---

## Notes

* **Browser support**: Well-supported in all modern browsers, but format support varies significantly
* **Video formats**:
  - MP4/H.264: Widely supported, good balance of quality and compression
  - WebM/VP9: Open format, good quality, supported in most modern browsers
  - OGG/Theora: Open format, less common now
  - AV1: Emerging format, excellent compression, growing support
* **Autoplay policies**: Strict restrictions on autoplay with sound; muted autoplay is generally allowed
* **Mobile considerations**:
  - `playsinline` attribute needed for iOS to prevent fullscreen
  - Preload may be limited to save data
  - Touch controls optimized for mobile
* **Accessibility requirements**:
  - Provide captions for dialogue and important sounds
  - Include audio descriptions for visual content
  - Ensure keyboard accessibility for controls
  - Provide transcripts for complex content
* **Performance considerations**:
  - Use appropriate preload settings
  - Consider adaptive streaming for long videos
  - Optimize video compression
  - Use CDN for better delivery
* **Common pitfalls**:
  - Forgetting multiple source formats
  - Missing `controls` attribute
  - Not providing captions for accessibility
  - Large file sizes without compression
  - Ignoring mobile user experience
* **JavaScript API**: Extensive control through HTMLMediaElement interface
* **CORS requirements**: Videos from different domains may require CORS headers
* **SEO impact**: Video content should have proper metadata, transcripts, and structured data
* **Responsive design**: Use CSS for responsive containers rather than fixed dimensions

---
