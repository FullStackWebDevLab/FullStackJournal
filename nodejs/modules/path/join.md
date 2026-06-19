# `join`

Join all given path segments together using the platform-specific separator as a delimiter, then normalize the resulting path.

If the joined path is a zero-length string, then '.' is returned.

```
join([...paths])
```

+ `...paths`: `<string>` A sequence of path segments.
+ Returns: `<string>`

---
