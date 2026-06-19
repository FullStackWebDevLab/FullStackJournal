# `relative`

Return the relative path from `from` to `to` based on the current working directory. If `from` to `to` each resolve to teh same path (after calling `path.resolve()` on each), a zero-length string is returned.

```
relative(from, to)
```

+ Both `from` and `to` are of type `<string>`.

If a zero-length string is passed as `from` or `to`, the current working directory will be used instead of the zero-length strings.

Example:

```js
path.relative("/data/orandea/test/aaa", "/data/orandea/impl/bbb");
// Returns: "../../impl/bbb"
```

---
