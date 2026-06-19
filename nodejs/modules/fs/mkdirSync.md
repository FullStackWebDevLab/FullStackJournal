# `mkdirSync`

Synchronously creates a directory.

```
mkdirSync(path[, options])
```

+ `path`: `<string>` | `<Buffer>` | `<URL>`
+ `options`: `<Object>` | `<integer>`
  - `recursive`: `<boolean>`. Defaults to `false`.
  - `mode`: `<string>` | `<integer>`. Not supported on Windows. Defaults to `0o777`.
+ Returns: `<string>` | `<undefined>`. If `recursive` is `true`, returns the first directory path created.

---
