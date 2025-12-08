# `<track>`

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

The `<track>` element specifies timed text tracks for `<audio>` and `<video>` elements, providing captions, subtitles, descriptions, chapters, or metadata that are synchronized with media playback. It enables accessibility features, multilingual support, and enhanced user experiences by displaying text overlays during media playback.

---

## Syntax & Variants

+ **Standard syntax**: `<track>` (void element)
+ **Void element**: No closing tag required
+ **Self-closing variants**:
  - HTML5: `<track>`
  - XHTML: `<track />` or `<track></track>`
+ **Text track specifier**: Always used within parent media elements

---

## Attributes

+ **Core attributes**:
  - `src` (required): URL of the track file (WebVTT format)
  - `kind` (required): Type of text track (`subtitles`, `captions`, `descriptions`, `chapters`, `metadata`)
  - `srclang` (optional): Language of the track text (BCP 47 language tag)
  - `label` (optional): User-readable title for the track
  - `default` (optional): Indicates this track should be enabled by default
+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.
+ **No optional attributes**: All core attributes except `srclang` and `label` have specific requirements

---

## Content Model

+ **Empty element**: Must not contain any content
+ **No children permitted**: Cannot contain text or other elements
+ **Void element category**: Defined as having no content model in HTML specification
+ **External resources**: References external WebVTT (.vtt) files

---

## Context

+ **Required parent**: Must be a direct child of `<audio>` or `<video>`
+ **Sibling order**: 
  - Must come after `<source>` elements (if any)
  - Must come before fallback content
  - Multiple `<track>` elements allowed for different languages/types
+ **Invalid contexts**: Cannot be used outside of `<audio>` or `<video>` elements

---

## Behavior and Semantics

+ **Default display**: No visual representation itself
+ **Track loading**: Browser fetches WebVTT file from `src` URL
+ **Display behavior**:
  - Text overlays appear during media playback
  - Position and styling can be customized with CSS
  - User can select tracks from browser controls
+ **Semantic meaning**:
  - Provides accessibility information
  - Enhances media comprehension
  - Supports multilingual content
+ **Accessibility**: Critical for hearing-impaired users and non-native speakers

---

## Examples

**Basic video with English captions:**
```html
<video controls>
  <source src="video.mp4" type="video/mp4">
  <track src="captions-en.vtt" kind="captions" srclang="en" label="English" default>
</video>
```

**Multilingual subtitles:**
```html
<video controls>
  <source src="movie.mp4" type="video/mp4">
  <track src="subs-en.vtt" kind="subtitles" srclang="en" label="English" default>
  <track src="subs-es.vtt" kind="subtitles" srclang="es" label="Español">
  <track src="subs-fr.vtt" kind="subtitles" srclang="fr" label="Français">
  <track src="subs-de.vtt" kind="subtitles" srclang="de" label="Deutsch">
</video>
```

**Multiple track types:**
```html
<video controls>
  <source src="tutorial.mp4" type="video/mp4">
  <!-- Captions for dialogue and sound effects -->
  <track src="captions.vtt" kind="captions" srclang="en" label="English Captions" default>
  <!-- Audio descriptions for visual content -->
  <track src="descriptions.vtt" kind="descriptions" srclang="en" label="Audio Descriptions">
  <!-- Chapter markers for navigation -->
  <track src="chapters.vtt" kind="chapters" srclang="en" label="Chapters">
  <!-- Metadata for scripting -->
  <track src="metadata.vtt" kind="metadata" srclang="en">
</video>
```

**Audio with descriptions:**
```html
<audio controls>
  <source src="lecture.mp3" type="audio/mpeg">
  <track src="descriptions.vtt" kind="descriptions" srclang="en" label="Audio Descriptions" default>
</audio>
```

**Complex video with styled tracks:**
```html
<video controls id="styled-video">
  <source src="presentation.mp4" type="video/mp4">
  <track src="styled-captions.vtt" kind="captions" srclang="en" label="Styled Captions" default>
</video>

<style>
  ::cue {
    background-color: rgba(0, 0, 0, 0.8);
    color: white;
    font-family: Arial, sans-serif;
    font-size: 18px;
  }
  
  ::cue(b) {
    color: yellow;
  }
  
  ::cue(i) {
    font-style: italic;
    color: #ccc;
  }
</style>
```

**Video with chapter navigation:**
```html
<video controls id="chapter-video">
  <source src="documentary.mp4" type="video/mp4">
  <track src="chapters.vtt" kind="chapters" srclang="en" label="Chapters" default>
</video>

<script>
  const video = document.getElementById('chapter-video');
  const track = video.textTracks[0];
  
  track.addEventListener('cuechange', function() {
    const cues = this.activeCues;
    if (cues.length > 0) {
      console.log('Current chapter:', cues[0].text);
    }
  });
</script>
```

**WebVTT file example (captions-en.vtt):**
```vtt
WEBVTT

00:00:01.000 --> 00:00:04.000
Welcome to our tutorial on HTML5 video.

00:00:05.000 --> 00:00:09.000
Today we'll learn about the <b>&lt;track&gt;</b> element
and its importance for accessibility.

00:00:10.000 --> 00:00:15.000
<v Narrator>Captions make your content accessible
to hearing-impaired viewers.

00:00:16.000 --> 00:00:20.000
They also help non-native speakers
and people in noisy environments.

00:00:21.000 --> 00:00:25.000
Note: Always provide accurate captions
for better user experience.
```

**Chapters WebVTT file (chapters.vtt):**
```vtt
WEBVTT

00:00:00.000 --> 00:02:30.000
Introduction

00:02:30.000 --> 00:05:45.000
Basic Concepts

00:05:45.000 --> 00:10:20.000
Advanced Features

00:10:20.000 --> 00:15:00.000
Implementation Examples

00:15:00.000 --> 00:18:30.000
Conclusion
```

**Audio descriptions WebVTT (descriptions.vtt):**
```vtt
WEBVTT

00:00:05.000 --> 00:00:08.000
[A man in a blue shirt demonstrates coding on a laptop]

00:00:15.000 --> 00:00:20.000
[Diagram appears showing HTML structure with nested elements]

00:00:25.000 --> 00:00:30.000
[Screen transitions to show browser rendering the code]
```

---

## Notes

* **WebVTT format**: Text tracks must use Web Video Text Tracks format (.vtt files)
* **Kind attribute values**:
  - `subtitles`: Translations of dialogue (for viewers who don't understand language)
  - `captions`: Transcriptions of dialogue and sound effects (for hearing-impaired)
  - `descriptions`: Textual descriptions of video content (for visually impaired)
  - `chapters`: Chapter titles for navigation
  - `metadata`: Information for scripts (not displayed)
* **Accessibility requirements**: 
  - Captions required for WCAG compliance on video content
  - Audio descriptions required for complex visual content
* **Browser support**: Well-supported in modern browsers, but styling capabilities vary
* **CORS requirements**: Track files may require CORS headers if hosted on different domains
* **Common mistakes**:
  - Incorrect WebVTT file format
  - Missing required `src` or `kind` attributes
  - Wrong MIME type for .vtt files (should be `text/vtt`)
  - Tracks placed before `<source>` elements
  - Not providing default track when multiple languages available
* **Styling capabilities**: CSS `::cue` pseudo-element allows customization of caption appearance
* **Performance**: Track files are typically small and have minimal impact on performance
* **SEO benefits**: Search engines can index track content for better media discovery
* **Mobile considerations**: Touch interfaces handle track selection differently than desktop

---
