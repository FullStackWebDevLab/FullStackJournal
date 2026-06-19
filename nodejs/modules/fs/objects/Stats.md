# Stats

This object provides information about a file.

## Methods

### `isDirectory()`

Returns `true` if the object describes a directory, `false` otherwise.

If the object was obtained from calling `fs.lstat()` on a symbolic link which resolves to a directory, this method returns `false`.

### `isFile()`

Returns `true` if the object describes a regular file, `false` otherwise.

---
