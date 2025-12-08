# `<time>`

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

The `<time>` element represents a specific period in time, either as a precise datetime or as a duration. It enables machine-readable timestamp information to be embedded within human-readable date and time representations, facilitating better search engine indexing, calendar integration, accessibility improvements, and automated processing by user agents.

---

## Syntax and Variants

+ **Standard syntax**: `<time>...</time>`
+ **Not void**: Requires both opening and closing tags
+ **Two usage patterns**:
  - With `datetime` attribute: `<time datetime="...">human-readable</time>`
  - Without `datetime` attribute: `<time>machine-readable</time>`
+ **No self-closing variant**: Must contain content

---

## Attributes

+ **Core attributes**:
  - `datetime` (optional): Machine-readable timestamp in valid date/time format
  - `pubdate` (deprecated): Previously indicated publication date (removed in HTML5)

+ **Global attributes**: `id`, `class`, `style`, `data-*`, `aria-*`, `title`, etc.

+ **Required conditions**: Either `datetime` attribute OR text content must be in valid machine-readable format

---

## Content Model

+ **Permitted content**: Transparent content model (phrasing content)
+ **Allowed content**:
  - Text content (must be valid datetime if no `datetime` attribute)
  - Phrasing elements: `<span>`, `<em>`, `<strong>`, etc.
  - Other inline elements that don't represent time-related content
+ **Content restrictions**: Cannot contain other `<time>` elements

---

## Context

+ **Valid parents**: Any element that accepts phrasing content
+ **Common locations**:
  - Within `<article>` elements for publication dates
  - In blog posts, news articles, event listings
  - As timestamps in comments or social media feeds
  - Within `<footer>` elements for copyright dates
+ **No nesting**: Cannot contain other `<time>` elements

---

## Behavior and Semantics

+ **Default display**: Inline element (`display: inline`)
+ **Default styling**:
  - No inherent visual styling
  - Appears identical to surrounding text
  - Can be styled with CSS like any inline element
+ **Semantic meaning**:
  - Provides machine-readable timestamp data
  - Enhances search engine understanding of content chronology
  - Enables browser extensions and user agents to extract date information
  - Improves accessibility for screen readers and other assistive technologies
+ **Accessibility benefits**:
  - Screen readers can announce dates in appropriate formats
  - Users can extract dates to calendars or other applications
  - Provides context for time-sensitive content

---

## Examples

**Basic date with datetime attribute:**
```html
<time datetime="2024-03-15">March 15, 2024</time>
```

**Time with datetime attribute:**
```html
<time datetime="14:30">2:30 PM</time>
```

**Combined date and time:**
```html
<time datetime="2024-03-15T14:30:00Z">March 15, 2024 at 2:30 PM UTC</time>
```

**Duration representation:**
```html
<time datetime="PT2H30M">2 hours and 30 minutes</time>
```

**Event listing with multiple time elements:**
```html
<article>
  <h2>Web Development Conference</h2>
  <p>
    Scheduled for 
    <time datetime="2024-06-10T09:00:00">June 10, 2024 at 9:00 AM</time>
    to 
    <time datetime="2024-06-12T17:00:00">June 12, 2024 at 5:00 PM</time>.
  </p>
</article>
```

**Blog post with publication date:**
```html
<article>
  <header>
    <h1>Understanding Semantic HTML</h1>
    <p>
      Published on 
      <time datetime="2024-01-15T08:00:00-05:00">January 15, 2024</time>
      by Jane Developer
    </p>
  </header>
  <!-- Article content -->
</article>
```

**Comment thread with timestamps:**
```html
<div class="comments">
  <div class="comment">
    <p>Great article! Very informative.</p>
    <footer>
      — John Smith, 
      <time datetime="2024-01-16T10:30:00-05:00">January 16, 2024 at 10:30 AM</time>
    </footer>
  </div>
  
  <div class="comment">
    <p>Thanks for sharing these insights.</p>
    <footer>
      — Sarah Johnson, 
      <time datetime="2024-01-16T14:45:00-05:00">2:45 PM EST</time>
    </footer>
  </div>
</div>
```

**Event schedule with durations:**
```html
<div class="schedule">
  <h3>Conference Schedule</h3>
  <ul>
    <li>
      <time datetime="09:00">9:00 AM</time> - 
      <time datetime="09:45">9:45 AM</time>: 
      Keynote Address
    </li>
    <li>
      <time datetime="10:00">10:00 AM</time> - 
      <time datetime="11:30">11:30 AM</time>: 
      Workshop Session
      <span class="duration">(<time datetime="PT1H30M">1h 30m</time>)</span>
    </li>
    <li>
      <time datetime="13:00">1:00 PM</time> - 
      <time datetime="14:30">2:30 PM</time>: 
      Panel Discussion
    </li>
  </ul>
</div>
```

**Relative time with absolute datetime:**
```html
<p>
  This offer expires 
  <time datetime="2024-12-31T23:59:59">in 9 months</time>.
</p>

<p>
  Last updated 
  <time datetime="2024-03-15T16:20:00Z">2 hours ago</time>.
</p>
```

**Styled time elements:**
```html
<article class="news-article">
  <h1>Breaking News: Major Discovery</h1>
  <div class="meta">
    <span class="author">By Science Reporter</span>
    <time datetime="2024-03-15T10:00:00Z" class="publish-date">
      March 15, 2024
    </time>
    <time datetime="2024-03-15T14:30:00Z" class="update-date">
      Updated: 2:30 PM UTC
    </time>
  </div>
  
  <p>Researchers have announced a groundbreaking discovery...</p>
</article>

<style>
.meta {
  color: #666;
  font-size: 0.9em;
  margin-bottom: 1.5em;
}

.publish-date {
  font-weight: 600;
  color: #333;
}

.update-date {
  background: #f0f8ff;
  padding: 2px 6px;
  border-radius: 3px;
  margin-left: 8px;
}
</style>
```

**Business hours with time elements:**
```html
<div class="business-hours">
  <h3>Store Hours</h3>
  <dl>
    <dt>Monday - Friday</dt>
    <dd>
      <time datetime="09:00">9:00 AM</time> - 
      <time datetime="18:00">6:00 PM</time>
    </dd>
    
    <dt>Saturday</dt>
    <dd>
      <time datetime="10:00">10:00 AM</time> - 
      <time datetime="17:00">5:00 PM</time>
    </dd>
    
    <dt>Sunday</dt>
    <dd>Closed</dd>
  </dl>
</div>
```

**Historical dates with BCE/CE:**
```html
<p>
  The construction of the Great Pyramid of Giza was completed around 
  <time datetime="-02560">2560 BCE</time>.
</p>

<p>
  The first personal computer was introduced in 
  <time datetime="1975">1975</time>.
</p>
```

**Recipe with preparation times:**
```html
<div class="recipe">
  <h1>Classic Chocolate Chip Cookies</h1>
  
  <div class="recipe-meta">
    <div class="time-info">
      <strong>Prep time:</strong> 
      <time datetime="PT15M">15 minutes</time>
    </div>
    <div class="time-info">
      <strong>Cook time:</strong> 
      <time datetime="PT10M">10 minutes</time>
    </div>
    <div class="time-info">
      <strong>Total time:</strong> 
      <time datetime="PT25M">25 minutes</time>
    </div>
  </div>
  
  <!-- Recipe ingredients and instructions -->
</div>

<style>
.recipe-meta {
  display: flex;
  gap: 20px;
  margin-bottom: 20px;
  padding: 15px;
  background: #f9f9f9;
  border-radius: 5px;
}

.time-info {
  font-size: 0.9em;
}
</style>
```

**Countdown timer with time element:**
```html
<div class="countdown">
  <h3>Sale Ends In:</h3>
  <time datetime="2024-03-20T23:59:59" id="sale-end">
    March 20, 2024 at 11:59 PM
  </time>
  <div class="timer-display" aria-live="polite">
    <span id="days">5</span> days, 
    <span id="hours">12</span> hours, 
    <span id="minutes">30</span> minutes
  </div>
</div>

<script>
// JavaScript would update the display while maintaining
// the machine-readable datetime in the time element
function updateCountdown() {
  const saleEnd = new Date('2024-03-20T23:59:59');
  const now = new Date();
  const diff = saleEnd - now;
  
  // Update display elements
  document.getElementById('days').textContent = 
    Math.floor(diff / (1000 * 60 * 60 * 24));
  // ... update hours and minutes
}

setInterval(updateCountdown, 60000);
</script>
```

**Academic citation with dates:**
```html
<blockquote cite="https://example.com/research-paper">
  <p>Recent studies have shown significant improvements in web accessibility...</p>
  <footer>
    — Dr. Emily Chen, 
    <cite>Modern Web Standards</cite>, 
    published <time datetime="2023-11-15">November 2023</time>
  </footer>
</blockquote>
```

**Calendar event with timezone:**
```html
<div class="calendar-event">
  <h3>Team Meeting</h3>
  <p>
    <time datetime="2024-03-20T15:00:00-04:00">
      Wednesday, March 20, 2024 at 3:00 PM EDT
    </time>
  </p>
  <p>Location: Conference Room B</p>
</div>
```

---

## Notes

* **Date/time formats**:
  - **Date only**: `YYYY-MM-DD` (e.g., `2024-03-15`)
  - **Time only**: `HH:MM:SS` or `HH:MM` (e.g., `14:30` or `14:30:00`)
  - **Combined**: `YYYY-MM-DDTHH:MM:SS` (e.g., `2024-03-15T14:30:00`)
  - **With timezone**: `YYYY-MM-DDTHH:MM:SS±HH:MM` (e.g., `2024-03-15T14:30:00-05:00`)
  - **Duration**: `PTDHHMMSS` (e.g., `PT2H30M` for 2 hours 30 minutes)

* **Validation requirements**:
  - If no `datetime` attribute, text content must be valid machine-readable date/time
  - With `datetime` attribute, text content can be any human-readable representation
  - Invalid usage may result in the element being treated as regular text

* **Browser support**: Excellent across all modern browsers
* **Common mistakes**:
  - Using invalid date/time formats in `datetime` attribute
  - Nesting `<time>` elements within each other
  - Using human-readable formats without `datetime` attribute
  - Confusing timezone offsets (UTC vs local time)
  - Using deprecated `pubdate` attribute

* **SEO benefits**: Search engines can better understand content chronology and relevance
* **Accessibility considerations**:
  - Screen readers can interpret and announce dates appropriately
  - Users with cognitive disabilities benefit from clear, consistent date formatting
  - Timezone information helps international users understand timing

* **Best practices**:
  - Always include timezone information for events
  - Use `datetime` attribute for human-readable date representations
  - Be consistent with date formatting throughout your site
  - Consider user's locale when choosing date display formats
  - Use durations for time periods rather than specific clock times when appropriate

* **JavaScript integration**:
  - Can be easily parsed with `Date` constructor: `new Date(element.datetime)`
  - Useful for countdown timers, calendar integrations, and time-based interactions
  - Enables dynamic updating while maintaining semantic structure
