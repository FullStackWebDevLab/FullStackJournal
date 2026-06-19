# `readFileSync`

Return the contents of the path.

```
readFileSync(path[, options])
```

+ `path`: `<string>` | `<Buffer>` | `<URL>` | `<integer>` filename or file descriptor.
+ `options`: `<Object>` | `<string>`
  - `encoding`: `<string>` | `<null>`. Defaults to `null`.
  - `flag`: `<string>`. Defaults to `'r'`.
+ Returns: `<string>` | `<Buffer>`. If the `encoding` option is specified, this function returns a string. Otherwise, it returns a buffer.

---
