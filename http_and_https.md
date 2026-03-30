# HTTP/HTTPS Request Protocol

## 1. Overview

HTTP (Hypertext Transfer Protocol) is an application-layer protocol for distributed, collaborative, hypermedia information systems. HTTPS is HTTP over TLS (Transport Layer Security), providing encrypted communication and server authentication.

All HTTP requests follow a request-response model. A client initiates a request to a server. The server returns a response.

## 2. Request Structure

An HTTP request consists of the following components in order:

1. Request line
2. Header section
3. Empty line (CRLF)
4. Optional body

### 2.1 Request Line

The request line contains three elements separated by spaces:

- **Method**: The operation to perform
- **Request target**: The resource identifier
- **HTTP version**: Protocol version (HTTP/1.1, HTTP/2, HTTP/3)

Example:
```
GET /users/123 HTTP/1.1
```

### 2.2 Request Target

The request target specifies the resource. Four formats exist:

| Format | Example | Usage |
|--------|---------|-------|
| origin-form | `/path?query` | Most common. Used for standard requests |
| absolute-form | `https://example.com/path` | Used with proxies |
| authority-form | `example.com:443` | CONNECT method only |
| asterisk-form | `*` | OPTIONS method only |

Query strings are appended to the path with `?` and use percent-encoding per RFC 3986.

### 2.3 Headers

Headers are field-name and field-value pairs separated by colon. Format:
```
Field-Name: field-value
```

Headers are categorized by function:

| Category | Purpose | Examples |
|----------|---------|----------|
| General | Applies to message overall | `Connection`, `Date` |
| Request | Modifies request behavior | `Accept`, `If-Match` |
| Entity | Describes body content | `Content-Type`, `Content-Length` |

Multiple headers with the same field-name are permitted. The combined values are considered a comma-separated list unless the specification states otherwise.

### 2.4 Body

The body carries data associated with the request. Presence is determined by method and headers.

Conditions for body inclusion:
- Method allows body (POST, PUT, PATCH, others optionally)
- `Content-Length` or `Transfer-Encoding` header present

The body type is specified by the `Content-Type` header. Common values:
- `application/json`
- `application/x-www-form-urlencoded`
- `multipart/form-data`
- `text/plain`
- `application/octet-stream`

## 3. HTTP Methods

### 3.1 Method Properties

Each method has two defining properties:

- **Safe**: Does not modify server state. Safe methods are read-only.
- **Idempotent**: Multiple identical requests produce the same server state as a single request.

### 3.2 GET

| Property | Value |
|----------|-------|
| Safe | Yes |
| Idempotent | Yes |
| Body | No |
| Cachable | Yes |

Retrieves the representation of the specified resource. GET requests MUST NOT include a body. Servers MAY ignore or reject GET requests with a body.

### 3.3 HEAD

| Property | Value |
|----------|-------|
| Safe | Yes |
| Idempotent | Yes |
| Body | No |
| Cachable | Yes |

Identical to GET except the server MUST NOT return a body. The response headers contain the same metadata that a GET request would return.

### 3.4 POST

| Property | Value |
|----------|-------|
| Safe | No |
| Idempotent | No |
| Body | Optional |
| Cachable | Only with explicit freshness information |

Submits data to the server. POST has no standardized semantics. Common implementations include:
- Resource creation
- Data processing
- Form submission

### 3.5 PUT

| Property | Value |
|----------|-------|
| Safe | No |
| Idempotent | Yes |
| Body | Optional |
| Cachable | No |

Replaces all current representations of the target resource with the request payload. The client specifies the complete resource state. Partial updates are not permitted with PUT.

If the target resource does not exist, the server MAY create it.

### 3.6 PATCH

| Property | Value |
|----------|-------|
| Safe | No |
| Idempotent | Implementation-dependent |
| Body | Yes |
| Cachable | No |

Applies partial modifications to a resource. The request body contains a set of instructions describing changes.

The `Content-Type` header MUST specify the patch format. Common formats include JSON Patch (`application/json-patch+json`) and JSON Merge Patch (`application/merge-patch+json`).

### 3.7 DELETE

| Property | Value |
|----------|-------|
| Safe | No |
| Idempotent | Yes |
| Body | MAY be included but not recommended |
| Cachable | No |

Removes the specified resource. After successful deletion, subsequent DELETE requests to the same resource SHOULD return 404 (Not Found) or 204 (No Content).

### 3.8 OPTIONS

| Property | Value |
|----------|-------|
| Safe | Yes |
| Idempotent | Yes |
| Body | No |
| Cachable | No |

Requests information about the communication options available for the target resource. The response MUST include the `Allow` header listing supported methods.

For CORS preflight requests, browsers send OPTIONS automatically before non-simple requests.

### 3.9 CONNECT

| Property | Value |
|----------|-------|
| Safe | No |
| Idempotent | No |
| Body | No |
| Cachable | No |

Establishes a tunnel to the server identified by the target resource. Used primarily with proxies for HTTPS connections.

### 3.10 TRACE

| Property | Value |
|----------|-------|
| Safe | Yes |
| Idempotent | Yes |
| Body | No |
| Cachable | No |

Performs a message loop-back test. The server returns the received request in the response body. TRACE is often disabled on production servers for security reasons.

## 4. Request Processing Requirements

### 4.1 Required Components

Every HTTP request MUST contain:
- A valid HTTP method
- A request target
- The HTTP version
- The `Host` header field (for HTTP/1.1)

### 4.2 Conditional Requests

Clients MAY include conditional headers to make requests dependent on resource state:

| Header | Condition |
|--------|-----------|
| `If-Match` | Only if ETag matches |
| `If-None-Match` | Only if ETag does not match |
| `If-Modified-Since` | Only if modified after date |
| `If-Unmodified-Since` | Only if not modified since date |

### 4.3 Content Negotiation

Clients specify preferred response formats using:

| Header | Purpose |
|--------|---------|
| `Accept` | Media types accepted |
| `Accept-Language` | Preferred languages |
| `Accept-Encoding` | Supported compression |

## 5. HTTPS

HTTPS is HTTP transmitted over TLS. The protocol stack is:

```
Application: HTTP
Security: TLS 1.2 or 1.3
Transport: TCP
Network: IP
```

HTTPS provides:
- Encryption of all request and response data
- Server authentication via X.509 certificates
- Message integrity verification

The default port for HTTPS is 443. HTTP uses port 80.

When using HTTPS, the entire HTTP request, including method, path, headers, and body, is encrypted before transmission. The TLS handshake occurs before any HTTP data is sent.

---
