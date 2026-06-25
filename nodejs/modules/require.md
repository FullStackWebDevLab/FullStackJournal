# `require()`

Used to import modules, JSON, and local files.

```
require(id)
```

+ `id`: `<string>` Module name or path.
+ Returns: `<any>` exported module content.

Modules can be imported from `node_modules`.

```
const fs = require("fs");
const crypto = require("node:crypto");
```

Local modules and JSON files can be imported using a relative path that will be resolved against the directory named by `__dirname` or the current working directory.

```
const myLocalModule = require("./path/myLocalModule");
const jsonData = require("./path/filename.json");
```

**Note:** The relative paths of POSIX style are resolved in an OS independent fashion, meaning that the examples above will work on Windows in the same way they would on Unix systems.

---
