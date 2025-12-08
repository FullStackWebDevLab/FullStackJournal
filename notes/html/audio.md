# `<audio>`

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

The `<audio>` element embeds sound content in HTML documents, providing native audio playback capabilities without requiring external plugins. It enables the integration of music, podcasts, sound effects, narration, and other audio media directly into web pages, with built-in controls for play, pause, volume adjustment, and seeking.

---

## Syntax & Variants

+ **Standard syntax**: `<audio>...</audio>`
+ **Not void**: Requires both opening and closing tags
+ **Container element**: Wraps `<source>` elements and fallback content
+ **No self-closing variant**: Must be properly closed
+ **HTML5 introduction**: Added in HTML5 to provide native audio support

---

## Attributes

+ **Core attributes**:
  - `src` (optional): URL of the audio file to embed
  - `controls` (optional): Shows browser's default audio controls
  - `autoplay` (optional): Automatically begins playback when ready
  - `loop` (optional): Replays audio from beginning when finished
  - `muted` (optional): Default state is muted
  - `preload` (optional): Hints how much to preload (`none`, `metadata`, `auto`)
  - `crossorigin` (optional): CORS settings for the audio file
+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No required attributes**: All attributes are optional, but `controls` is typically needed for user interaction

---

## Content Model

+ **Permitted content**:
  - Zero or more `<source>` elements
  - Zero or more `<track>` elements for captions/subtitles
  - Fallback content for unsupported browsers
  - Flow content or phrasing content as fallback
+ **Source order**: Browser uses first supported `<source>` element
+ **Fallback content**: Displayed if browser doesn't support `<audio>` element

---

## Context

+ **Valid parents**: Any element that accepts embedded content or phrasing content
+ **Common locations**:
  - Within `<article>`, `<section>` for content audio
  - Within `<figure>` for captioned audio content
  - Within `<div>` containers for UI components
  - In music players, podcasts, educational content
+ **Embedded content**: Treated as replaced element in document flow

---

## Behavior and Semantics

+ **Default display**: Inline-level element
+ **Default styling**:
  - Varies by browser for controls
  - Typically `display: inline`
  - No intrinsic dimensions without controls
+ **Playback behavior**:
  - Supports play, pause, seek, volume control
  - Buffers audio data as needed
  - Respects autoplay policies (often blocked without user interaction)
+ **Semantic meaning**:
  - Represents audio content
  - Screen readers may announce as "audio" or "media"
  - Provides audio context for assistive technologies
+ **Accessibility**: Can include text tracks for captions and descriptions

---

## Examples

**Basic audio with controls:**
```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
  Your browser does not support the audio element.
</audio>
```

**Audio with multiple formats and preload:**
```html
<audio controls preload="metadata">
  <source src="podcast.mp3" type="audio/mpeg">
  <source src="podcast.ogg" type="audio/ogg">
  <source src="podcast.wav" type="audio/wav">
  <p>Download the <a href="podcast.mp3">MP3 audio file</a>.</p>
</audio>
```

**Background audio without controls:**
```html
<audio id="bg-music" loop muted>
  <source src="ambient.mp3" type="audio/mpeg">
</audio>
```

**Audio with captions and descriptions:**
```html
<audio controls>
  <source src="lecture.mp3" type="audio/mpeg">
  <track kind="captions" src="captions.vtt" srclang="en" label="English">
  <track kind="descriptions" src="descriptions.vtt" srclang="en">
  <track kind="chapters" src="chapters.vtt" srclang="en">
</audio>
```

**Custom styled audio player:**
```html
<audio id="custom-audio" preload="metadata">
  <source src="song.mp3" type="audio/mpeg">
  <source src="song.ogg" type="audio/ogg">
</audio>

<div class="custom-player">
  <button id="play-btn">Play</button>
  <button id="pause-btn">Pause</button>
  <input type="range" id="volume-slider" min="0" max="1" step="0.1" value="0.7">
  <span id="time-display">0:00</span>
</div>
```

**Audio within figure with caption:**
```html
<figure>
  <figcaption>Listen to the bird call:</figcaption>
  <audio controls>
    <source src="bird-call.mp3" type="audio/mpeg">
    <source src="bird-call.ogg" type="audio/ogg">
    Your browser does not support audio playback.
  </audio>
</figure>
```

**Audio with JavaScript control:**
```html
<audio id="sound-effect" preload="auto">
  <source src="click.mp3" type="audio/mpeg">
</audio>

<button onclick="document.getElementById('sound-effect').play()">
  Play Sound
</button>

<button onclick="document.getElementById('sound-effect').pause()">
  Pause Sound
</button>
```

**Multiple audio instances with attributes:**
```html
<!-- Background music -->
<audio id="bgm" loop crossorigin="anonymous">
  <source src="background-music.mp3" type="audio/mpeg">
</audio>

<!-- Sound effect -->
<audio id="sfx" preload="auto">
  <source src="notification.mp3" type="audio/mpeg">
</audio>

<!-- Podcast with full controls -->
<audio controls preload="metadata" style="width: 100%">
  <source src="podcast-episode.mp3" type="audio/mpeg">
  <track kind="subtitles" src="subs-en.vtt" srclang="en" label="English">
  <p>Your browser doesn't support HTML5 audio. 
     <a href="podcast-episode.mp3">Download the audio</a> instead.</p>
</audio>
```

---

## Notes

* **Browser support**: Well-supported in all modern browsers, but format support varies
* **Audio formats**: 
  - MP3: Widely supported (patent issues)
  - OGG: Open format, good browser support
  - WAV: Uncompressed, large file sizes
  - AAC: Good quality, Apple ecosystem
* **Autoplay restrictions**: Modern browsers block autoplay with sound without user interaction
* **Mobile considerations**: 
  - Bandwidth concerns for large files
  - Autoplay often disabled
  - Preload may be ignored to save data
* **Accessibility requirements**:
  - Provide controls for user interaction
  - Include captions for spoken content
  - Offer volume control
  - Consider audio descriptions for important sounds
* **Performance considerations**:
  - Use appropriate preload settings
  - Consider streaming for long audio
  - Compress audio files appropriately
* **Common pitfalls**:
  - Forgetting the `controls` attribute
  - Not providing multiple formats for cross-browser support
  - Using autoplay without user consent
  - Large file sizes without compression
  - Missing fallback content for older browsers
* **JavaScript API**: Extensive control available through HTMLMediaElement interface
* **CORS requirements**: Audio files from different domains may require CORS headers
* **SEO impact**: Audio content should have textual alternatives for search engines

---
