# Same-Origin Policy (SOP) And Cross-Origin Resource Sharing (CORS)

## Same-Origin Policy

The Same-Origin Policy (SOP) is a security mechanism built into web browsers that restricts how scripts from one origin can interact with resources from another origin.

The following parts in a URL define an origin:
    + *Scheme*: A scheme is the first part of a URL, preceding the colon and double slashes (`://`), that specifies the protocol or the application used to access a resource (e.g., `http`, `https`).
    + *Domain*: A domain in a URL is the human-readable address of a website that acts as a user-friendly alias for a complex numerical IP address (e.g., `ringzeroacademy.com`).
    + *Port*: A port in a URL is a specific, optional number that identifies which virtual communication endpoint, or service, on a server, the client should connect to. For example, `http://127.0.0.1:8000`. The port is `8000`.

Two URLs have the same origin only if they share the same scheme, domain, and port.

SOP prevents scripts from one origin from accessing data from another origin in three main areas: **DOM access**, **XMLHttpRequest/Fetch**, and **cookie access**.

SOP does not restrict resources that are considered safe, for example: images, css, javascript files, and form submissions.

---

## Cross-Origin Resource Sharing

Cross-Origin Resource Sharing (CORS) is defines a way for a web application running at one origin to request resources from a different origin. CORS provides a controlled way to relax the SOP restriction.

Under CORS, the server that hosts the resource must include specific HTTP headers in its response. these headers indicate which origins are permitted to access the resource. The browser checks these headers before allowing the requesting web page to read the response.

The primary headers used in CORS are:
- `Access-Control-Allow-Origin`: Specifies the allowed origins.
- `Access-Control-Allow-Methods`: Specifies the allowed HTTP methods for the request.
- `Access-Control-Allow-Headers`: Specifies the allowed custom headers.
- `Access-Control-Allow-Credentials`: Indicates whether the request can include credentials such as cookies.

For certain types of requests, the browser first sends a preflight request. This is an HTTP `OPTIONS` request that verifies permission from the server before sending the actual request.

If the server does not respond with the appropriate CORS headers, the browser blocks the request. The requesting script does not receive the response data.

CORS is a browser-enforced standard. It does not protect the server from receiving the request; the request reaches the server regardless. The policy governs whether the browser permits the client-side script to access the response.

---
