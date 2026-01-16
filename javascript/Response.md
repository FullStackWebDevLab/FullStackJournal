# JavaScript Response Object Reference

## Introduction

The Response object represents the response to a network request. It is part of the Fetch API and is typically returned by the `fetch()` function or used in Service Workers. The Response object contains information about the response, including its status, headers, and body content.

## Constructor

### Response()

Creates a new Response object.

**Syntax:**
```javascript
new Response(body, init)
```

**Parameters:**
- `body` (optional): The body content for the response. Can be one of:
  - `null` (default)
  - `ArrayBuffer`
  - `ArrayBufferView` (TypedArray or DataView)
  - `Blob`
  - `FormData`
  - `ReadableStream`
  - `String`
  - `URLSearchParams`

- `init` (optional): An object containing settings for the response:
  - `status`: The status code (default: 200)
  - `statusText`: The status message (default: "")
  - `headers`: A Headers object or object literal with header key-value pairs

**Example:**
```javascript
const response = new Response("Hello World", {
  status: 200,
  statusText: "OK",
  headers: {
    "Content-Type": "text/plain"
  }
});
```

## Static Methods

Static methods are called on the Response constructor itself.

### Response.error()

Returns a new Response object associated with a network error. This is mainly useful in Service Workers.

**Syntax:**
```javascript
Response.error()
```

**Returns:**
- A Response object with type "error", status 0, and empty headers.

**Example:**
```javascript
// In a Service Worker
self.addEventListener("fetch", (event) => {
  if (shouldBlockRequest(event.request)) {
    event.respondWith(Response.error());
  }
});
```

### Response.redirect()

Returns a new Response object that redirects to a specified URL.

**Syntax:**
```javascript
Response.redirect(url, status)
```

**Parameters:**
- `url`: The URL to redirect to.
- `status` (optional): The redirect status code (default: 302). Valid values are 301, 302, 303, 307, or 308.

**Returns:**
- A Response object configured as a redirect.

**Example:**
```javascript
const response = Response.redirect("https://example.com", 301);
```

### Response.json()

Creates a new Response object with JSON body content. This is a convenient way to return JSON data.

**Syntax:**
```javascript
Response.json(data, init)
```

**Parameters:**
- `data`: The data to be converted to JSON. Can be any value that is JSON-serializable.
- `init` (optional): An object with the same options as the Response constructor.

**Returns:**
- A Response object with the JSON body and "Content-Type: application/json" header.

**Throws:**
- `TypeError`: If the data cannot be converted to JSON (e.g., circular references, functions).

**Example:**
```javascript
const response = Response.json({ name: "Alice", age: 30 });

// With status code
const errorResponse = Response.json(
  { error: "Not found" },
  { status: 404 }
);
```

## Instance Properties

Instance properties are accessed on Response objects.

### body

A ReadableStream containing the body content. This allows you to process the response body as a stream.

**Type:** `ReadableStream` (read-only)

**Example:**
```javascript
const response = await fetch("https://example.com/data");
const reader = response.body.getReader();
```

### bodyUsed

Indicates whether the response body has already been read.

**Type:** `Boolean` (read-only)

**Value:**
- `true`: The body has been consumed.
- `false`: The body has not been consumed yet.

**Example:**
```javascript
const response = await fetch("https://example.com/data");
console.log(response.bodyUsed); // false

await response.json();
console.log(response.bodyUsed); // true
```

### headers

The Headers object containing the response headers.

**Type:** `Headers` (read-only)

**Example:**
```javascript
const response = await fetch("https://example.com");
const contentType = response.headers.get("Content-Type");
console.log(contentType);
```

### ok

Indicates whether the response was successful (status in the range 200-299).

**Type:** `Boolean` (read-only)

**Example:**
```javascript
const response = await fetch("https://example.com/data");
if (response.ok) {
  const data = await response.json();
  console.log(data);
} else {
  console.error("Request failed");
}
```

### redirected

Indicates whether the response is the result of a redirect.

**Type:** `Boolean` (read-only)

**Value:**
- `true`: The request was redirected one or more times.
- `false`: No redirection occurred.

**Example:**
```javascript
const response = await fetch("https://example.com");
if (response.redirected) {
  console.log("Request was redirected");
  console.log("Final URL:", response.url);
}
```

### status

The HTTP status code of the response.

**Type:** `Number` (read-only)

**Common Values:**
- 200: OK
- 201: Created
- 204: No Content
- 301: Moved Permanently
- 302: Found
- 400: Bad Request
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 500: Internal Server Error

**Example:**
```javascript
const response = await fetch("https://example.com");
console.log(response.status); // 200
```

### statusText

The status message corresponding to the status code.

**Type:** `String` (read-only)

**Example:**
```javascript
const response = await fetch("https://example.com");
console.log(response.statusText); // "OK"
```

### type

The type of the response. This indicates how the response was obtained.

**Type:** `String` (read-only)

**Possible Values:**
- `"basic"`: Same-origin response. All headers are exposed except "Set-Cookie".
- `"cors"`: Valid cross-origin response with CORS headers. Only CORS-safe headers are exposed.
- `"error"`: Network error. Status is 0, headers are empty. This is returned by `Response.error()`.
- `"opaque"`: Response from a cross-origin request with mode "no-cors". Status is 0, body is null, headers are empty.
- `"opaqueredirect"`: Response from a request with redirect mode "manual". Status is 0, body is null, headers are empty.

**Example:**
```javascript
const response = await fetch("https://example.com");
console.log(response.type); // "basic" or "cors"

// Cross-origin with no-cors
const opaqueResponse = await fetch("https://other-domain.com", {
  mode: "no-cors"
});
console.log(opaqueResponse.type); // "opaque"
```

### url

The URL of the response. This is the final URL after any redirects.

**Type:** `String` (read-only)

**Example:**
```javascript
const response = await fetch("https://example.com/redirect");
console.log(response.url); // Final URL after redirect
```

## Instance Methods

Instance methods are called on Response objects to read the body content.

### arrayBuffer()

Reads the response body and returns it as an ArrayBuffer.

**Syntax:**
```javascript
response.arrayBuffer()
```

**Returns:**
- A Promise that resolves to an ArrayBuffer.

**Throws:**
- `TypeError`: If the body has already been consumed or is locked.

**Example:**
```javascript
const response = await fetch("https://example.com/binary-data");
const buffer = await response.arrayBuffer();
console.log(buffer.byteLength);
```

### blob()

Reads the response body and returns it as a Blob.

**Syntax:**
```javascript
response.blob()
```

**Returns:**
- A Promise that resolves to a Blob.

**Throws:**
- `TypeError`: If the body has already been consumed or is locked.

**Example:**
```javascript
const response = await fetch("https://example.com/image.jpg");
const blob = await response.blob();
const imageUrl = URL.createObjectURL(blob);
document.querySelector("img").src = imageUrl;
```

### bytes()

Reads the response body and returns it as a Uint8Array.

**Syntax:**
```javascript
response.bytes()
```

**Returns:**
- A Promise that resolves to a Uint8Array.

**Throws:**
- `TypeError`: If the body has already been consumed or is locked.

**Example:**
```javascript
const response = await fetch("https://example.com/data");
const bytes = await response.bytes();
console.log(bytes.length);
```

### clone()

Creates a copy of the Response object. This is useful when you need to use the response body multiple times.

**Syntax:**
```javascript
response.clone()
```

**Returns:**
- A new Response object that is a clone of the original.

**Throws:**
- `TypeError`: If the response body has already been used.

**Example:**
```javascript
const response = await fetch("https://example.com/data");
const clone1 = response.clone();
const clone2 = response.clone();

const data1 = await clone1.json();
const data2 = await clone2.text();
```

### formData()

Reads the response body and parses it as FormData.

**Syntax:**
```javascript
response.formData()
```

**Returns:**
- A Promise that resolves to a FormData object.

**Throws:**
- `TypeError`: If the body has already been consumed, is locked, or cannot be parsed as FormData.

**Example:**
```javascript
const response = await fetch("https://example.com/form-data");
const formData = await response.formData();
console.log(formData.get("username"));
```

### json()

Reads the response body and parses it as JSON.

**Syntax:**
```javascript
response.json()
```

**Returns:**
- A Promise that resolves to the parsed JavaScript object.

**Throws:**
- `SyntaxError`: If the response body is not valid JSON.
- `TypeError`: If the body has already been consumed or is locked.

**Example:**
```javascript
const response = await fetch("https://api.example.com/users");
const users = await response.json();
console.log(users);
```

### text()

Reads the response body and returns it as a string.

**Syntax:**
```javascript
response.text()
```

**Returns:**
- A Promise that resolves to a string containing the response body.

**Throws:**
- `TypeError`: If the body has already been consumed or is locked.

**Example:**
```javascript
const response = await fetch("https://example.com/text-file.txt");
const text = await response.text();
console.log(text);
```

## Common Usage Patterns

### Basic Fetch Request

```javascript
fetch("https://api.example.com/data")
  .then(response => {
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error("Error:", error));
```

### Using async/await

```javascript
async function fetchData() {
  try {
    const response = await fetch("https://api.example.com/data");
    
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Error:", error);
  }
}

fetchData();
```

### Checking Response Type

```javascript
const response = await fetch("https://api.example.com/data");

const contentType = response.headers.get("Content-Type");

if (contentType && contentType.includes("application/json")) {
  const data = await response.json();
  console.log(data);
} else {
  const text = await response.text();
  console.log(text);
}
```

### Handling Different Status Codes

```javascript
const response = await fetch("https://api.example.com/data");

switch (response.status) {
  case 200:
    const data = await response.json();
    console.log("Success:", data);
    break;
  case 404:
    console.error("Resource not found");
    break;
  case 500:
    console.error("Server error");
    break;
  default:
    console.error(`Unexpected status: ${response.status}`);
}
```

### Cloning Responses

```javascript
const response = await fetch("https://api.example.com/data");

// Clone the response to use it multiple times
const clone = response.clone();

// Cache the original response
cache.put(request, response);

// Use the clone for processing
const data = await clone.json();
console.log(data);
```

## Error Handling

### Network Errors

When a network error occurs, `fetch()` rejects the promise. The Response object is never created.

```javascript
fetch("https://api.example.com/data")
  .then(response => response.json())
  .catch(error => {
    // This catches network errors
    console.error("Network error:", error);
  });
```

### HTTP Errors

HTTP errors (4xx, 5xx) do not cause `fetch()` to reject. You must check `response.ok` or `response.status`.

```javascript
const response = await fetch("https://api.example.com/data");

if (!response.ok) {
  // Handle HTTP errors
  throw new Error(`HTTP error! status: ${response.status}`);
}

const data = await response.json();
```

### JSON Parsing Errors

If the response body is not valid JSON, `response.json()` will throw a SyntaxError.

```javascript
try {
  const response = await fetch("https://api.example.com/data");
  const data = await response.json();
  console.log(data);
} catch (error) {
  if (error instanceof SyntaxError) {
    console.error("Invalid JSON:", error);
  } else {
    console.error("Other error:", error);
  }
}
```

## Important Notes

### Body Can Only Be Read Once

Once you call a body reading method (like `json()`, `text()`, `blob()`), the body is consumed and cannot be read again. Use `clone()` if you need to read the body multiple times.

```javascript
const response = await fetch("https://api.example.com/data");

// First read
const data1 = await response.json();

// This will throw an error
try {
  const data2 = await response.json();
} catch (error) {
  console.error("Body already used");
}
```

### CORS and Opaque Responses

When making cross-origin requests with `mode: "no-cors"`, you receive an opaque response. You cannot read the body or headers of opaque responses.

```javascript
const response = await fetch("https://other-domain.com/api", {
  mode: "no-cors"
});

console.log(response.type); // "opaque"
console.log(response.status); // 0
console.log(response.body); // null
```

### Service Workers

The Response object is commonly used in Service Workers to intercept and modify network requests.

```javascript
self.addEventListener("fetch", (event) => {
  event.respondWith(
    caches.match(event.request).then(cachedResponse => {
      if (cachedResponse) {
        return cachedResponse;
      }
      return fetch(event.request);
    })
  );
});
```

## Best Practices

1. Always check `response.ok` before processing the body to handle HTTP errors properly.
2. Use appropriate error handling for both network errors and HTTP errors.
3. Use `clone()` when you need to read the response body multiple times.
4. Check the `Content-Type` header to determine how to parse the response body.
5. Use `async/await` for cleaner, more readable code.
6. Consider using `response.json()` static method for creating JSON responses in server code.
7. Be aware of CORS restrictions when making cross-origin requests.

## Compatibility

The Response object is part of the Fetch API, which is supported in all modern browsers and Node.js (version 18+). Specific features:

- Basic Response support: Available in all modern browsers
- `Response.json()` static method: Available in modern browsers and Node.js 18+
- `Response.bytes()`: Newer addition, check browser compatibility
- Service Worker support: Requires HTTPS (except for localhost)

Always check browser compatibility for your target environments, especially for newer features.

---
