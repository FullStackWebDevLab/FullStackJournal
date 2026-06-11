# Reading And Writing Files

## NodeJS

Node.js provides a built-in `fs` (file system) module for reading and writing files.

### APIs

Node.js offers 3 different ways to work with files:

+ **Asynchronous with promises** (recommended): This API uses `async/await` and the `fs/promises` API. It is non-blocking, meaning other operations can run while the files is being read or written.
+ **Asynchronous with callbacks**: This is the traditional pattern. It is non-blocking but uses callback functions. Callback functions can lead to "callback hell" with deeply nested code. Not recommended for new projects.
+ **Synchronous**: This API uses `readFileSync` and `writeFileSync`. It is blocking, meaning your code will stop and wait for the file operation to complete before moving on. This should be avoided in a running server application as it would freeze the server for every user during the file operation.

### Example: Asynchronous with promises

```js
import * as fs from "node:fs/promises";

// Write.
const data = "Hello World!";

try {
    /* `writeFile()` will create the file if it doesn't exist,
     * and it will overwrite it if it does exist.
     */
    await fs.writeFile("file.txt", data, "utf8");
    console.log("File written successfully.");
} catch(error) {
    console.error("Error writing file:", error.message);
}

// Read.
try {
    /* For text files, specify the "utf8" encoding to get a string;
     * otherwise, `readFile` returns a raw `Buffer`.
     */
    const contents = await fs.readFile("file.txt", "utf8");
    console.log(contents);
} except(error) {
    console.error("Error reading file:", error.message);
}
```

---
