# Importing Modules

## `import`

The `import` declaration is used to import read-only live bindings which are exported by another module.

```javascript
import defaultExport from "module-name";
import * as name from "module-name";
import { export1 } from "module-name";
import { export1 as alias1 } from "module-name";
import { default as alias } from "module-name";
import { export1, export2 } from "module-name";
import { export1, export2 as alias2, /* … */ } from "module-name";
import { "string name" as alias } from "module-name";
import defaultExport, { export1, /* … */ } from "module-name";
import defaultExport, * as name from "module-name";
import "module-name";
```

---

## `export`

The `export` declaration is used to export values from a JavaScript module.

The value of an imported binding is subject to change in the module that exports it (live binding). This means that when a module updates the value of a binding that it exports, the update will be visible in its imported value.

In order to use the `export` declaration in a source file, the file must be interpreted by the runtime as a module. This is done by adding `type="module"` to the `<script>` tag in HTML, or by being imported by another module.

Modules are interpreted in strict mode.

Examples:

```javascript
export let name = "John Doe"; // Also works with 'var' and 'const'.
export function functionName () {}
export class ClassName() {}
```

### Types of Exports

There are 2 types of exports; named export and default export. You can have multiple named exports per module but only one default export.

---

## CORS When Importing Modules

When you import a module, the browser fetches that file like it fetches any other resource (images, API calls, etc). This means that the Same Origin Policy will apply to module imports.

When you open a HTML file in a browser without using a server, the URL starts with `file://`. These types or URLs have no origin (`null`). CORS can't validate `null` against `Access-Control-Allow-Origin` headers. Therefore, the browser blocks the request as a security precaution. This will prevent the file from importing modules.

To fix this, have a valid origin. This is simply done by serving the file using a server. The server used doesn't need to have CORS enabled. It's role is to give the file a valid origin (like `http://localhost:8000`). When the file imports modules, the browser will make requests to the same origin as the file. Since the modules come from the same origin as the file, CORS is not required. CORS is only required when the file makes a request to different origins.

---
