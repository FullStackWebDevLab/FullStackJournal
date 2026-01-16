# Fetch API RequestInit Reference

## Overview

The **RequestInit** object is the second parameter passed to the `fetch()` function. It contains options that configure how the HTTP request is made.

```javascript
fetch(url, requestInitObject)
```

You can pass RequestInit options in three ways:

1. Directly into `fetch()`
2. Into the `Request()` constructor
3. Into both (values in `fetch()` override those in `Request()`)

## Properties

### attributionReporting (Deprecated)

**Type:** Object  
**Purpose:** Controls attribution reporting for advertising

**Properties:**
- `eventSourceEligible` (boolean) - Allow response to register attribution source
- `triggerEligible` (boolean) - Allow response to register attribution trigger

**Example:**
```javascript
attributionReporting: {
  eventSourceEligible: true,
  triggerEligible: false
}
```

---

### body

**Type:** String, ArrayBuffer, Blob, DataView, File, FormData, TypedArray, URLSearchParams, or ReadableStream  
**Purpose:** Data to send to the server  
**Default:** undefined

**Important Rules:**
- Cannot be used with GET or HEAD requests
- Automatically sets Content-Type header for FormData and URLSearchParams

**Example:**
```javascript
body: JSON.stringify({ username: "john" })
```

---

### browsingTopics (Deprecated)

**Type:** Boolean  
**Purpose:** Send user's selected topics in Sec-Browsing-Topics header

---

### cache

**Type:** String  
**Purpose:** Control how the request uses the browser's HTTP cache  
**Default:** "default"

**Valid Values:**

| Value | Behavior |
|-------|----------|
| `default` | Look in cache first. If fresh, use it. If stale, make conditional request. If no match, fetch from server. |
| `no-store` | Always fetch from server. Never update cache. |
| `reload` | Always fetch from server. Update cache with result. |
| `no-cache` | Make conditional request to server regardless of cache state. |
| `force-cache` | Use cache if available (even if stale). Otherwise fetch from server. |
| `only-if-cached` | Use cache only. Return network error if not cached. Must be used with `mode: "same-origin"`. |

**Example:**
```javascript
cache: "no-cache"
```

---

### credentials

**Type:** String  
**Purpose:** Control whether cookies and authentication data are sent  
**Default:** "same-origin"

**Valid Values:**

| Value | Behavior |
|-------|----------|
| `omit` | Never send credentials |
| `same-origin` | Send credentials only for same-origin requests |
| `include` | Always send credentials, even cross-origin |

**Important:** For cross-origin requests with `credentials: "include"`, the server must send `Access-Control-Allow-Credentials: true` and cannot use `Access-Control-Allow-Origin: *`.

**Example:**
```javascript
credentials: "include"
```

---

### duplex (Experimental)

**Type:** String  
**Purpose:** Control duplex behavior for streaming requests  
**Valid Value:** "half"

**Required when:** `body` is a ReadableStream

---

### headers

**Type:** Headers object or plain object  
**Purpose:** Set HTTP headers for the request

**Restrictions:**
- Cannot set forbidden request headers (browser sets these automatically)
- With `mode: "no-cors"`, only CORS-safelisted headers allowed

**Example:**
```javascript
headers: {
  "Content-Type": "application/json",
  "Authorization": "Bearer token123"
}
```

---

### integrity

**Type:** String  
**Purpose:** Verify resource integrity using cryptographic hash  
**Default:** Empty string

**Format:** `<hash-algo>-<hash-source>`

**Valid Algorithms:** sha256, sha384, sha512

**Example:**
```javascript
integrity: "sha256-BpfBw7ivV8q2jLiT13fxDYAe2tJllusRSZ273h2nFSE="
```

**Behavior:** Browser computes hash of downloaded resource. If it does not match, request fails with network error.

---

### keepalive

**Type:** Boolean  
**Purpose:** Allow request to continue after page unload  
**Default:** false

**Use Cases:**
- Send analytics when user closes page
- Background data synchronization

**Limitations:**
- Body size limited to 64 kibibytes
- Better alternative to `Navigator.sendBeacon()` for POST requests

**Example:**
```javascript
keepalive: true
```

---

### method

**Type:** String  
**Purpose:** HTTP method for the request  
**Default:** "GET"

**Common Values:** GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS

**Example:**
```javascript
method: "POST"
```

---

### mode

**Type:** String  
**Purpose:** Control cross-origin behavior  
**Default:** "cors"

**Valid Values:**

| Value | Behavior |
|-------|----------|
| `same-origin` | Block cross-origin requests. Return network error if cross-origin. |
| `cors` | Use CORS mechanism for cross-origin requests. Only CORS-safelisted response headers available. |
| `no-cors` | Disable CORS. Response is opaque (cannot read headers or body). Limited to HEAD, GET, POST methods and CORS-safelisted headers. |
| `navigate` | Used only for HTML navigation between documents. |

**Example:**
```javascript
mode: "cors"
```

---

### priority

**Type:** String  
**Purpose:** Set fetch priority relative to other requests  
**Default:** "auto"

**Valid Values:**

| Value | Description |
|-------|-------------|
| `high` | High priority |
| `low` | Low priority |
| `auto` | No preference |

**Example:**
```javascript
priority: "high"
```

---

### redirect

**Type:** String  
**Purpose:** Control behavior when server sends redirect  
**Default:** "follow"

**Valid Values:**

| Value | Behavior |
|-------|----------|
| `follow` | Automatically follow redirects |
| `error` | Return network error on redirect |
| `manual` | Return response with filtered fields (for service workers) |

**Example:**
```javascript
redirect: "follow"
```

---

### referrer

**Type:** String  
**Purpose:** Set the Referer header value  
**Default:** "about:client"

**Valid Values:**

| Value | Behavior |
|-------|----------|
| Same-origin URL | Set Referer to this URL |
| Empty string "" | Omit Referer header |
| "about:client" | Use default (usually the requesting page URL) |

**Example:**
```javascript
referrer: "https://example.com/page"
```

---

### referrerPolicy

**Type:** String  
**Purpose:** Set policy for Referer header

**Valid Values:** no-referrer, no-referrer-when-downgrade, same-origin, origin, strict-origin, origin-when-cross-origin, strict-origin-when-cross-origin, unsafe-url

**Example:**
```javascript
referrerPolicy: "no-referrer"
```

---

### signal

**Type:** AbortSignal  
**Purpose:** Cancel the request programmatically

**Example:**
```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch(url, { signal });

// Later, to cancel:
controller.abort();
```

---

## Common Patterns

### Simple POST Request
```javascript
fetch("https://api.example.com/data", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({ name: "John" })
});
```

### Request with Credentials
```javascript
fetch("https://api.example.com/data", {
  credentials: "include",
  mode: "cors"
});
```

### Cancellable Request
```javascript
const controller = new AbortController();

fetch(url, { signal: controller.signal });

// Cancel after 5 seconds
setTimeout(() => controller.abort(), 5000);
```

### Cache Control
```javascript
fetch(url, {
  cache: "no-cache"
});
```

---

## Invalid Combinations

1. **body with GET/HEAD:** Adding body to GET or HEAD request throws error
2. **only-if-cached without same-origin:** Using `cache: "only-if-cached"` requires `mode: "same-origin"`
3. **Misspelled properties:** Unknown properties are silently ignored

---

## Error Handling

The fetch promise rejects only for network errors or request configuration errors. HTTP error status codes (404, 500, etc.) do not cause rejection. Always check `response.ok` or `response.status`.

```javascript
try {
  const response = await fetch(url, options);
  if (!response.ok) {
    throw new Error(`HTTP error: ${response.status}`);
  }
  const data = await response.json();
} catch (error) {
  console.error("Fetch failed:", error);
}
```

---

## Browser Compatibility

All modern browsers support RequestInit. Some experimental features may have limited support:
- `duplex`: Experimental
- `attributionReporting`: Deprecated
- `browsingTopics`: Deprecated
- `only-if-cached`: Experimental

Always check current browser compatibility before using experimental features.

---
