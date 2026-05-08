# `install`

`npm install`, when executed without specifying a package, checks `package.json` and install all dependencies (under the `"dependencies"` key). When executed with a specific package (like `npm install react`), it installs the specified package and its dependencies, and updates the `package-lock.json` and `package.json`.

---

## Install Location

### Local Install

```
npm install package
```

This install `package` in the current directory in the `node_modules` directory: `./node_modules`.

```
my-app/
├── node_modules/
├── package.json
└── package-lock.json
```

### Global Install

```
npm install -g typescript
```

Installs into a global system directory. Check it with:

```
npm root -g
```

+ The output for the above command on arch linux was `/usr/lib/node_modules`.
+ The binaries are stored in `/usr/bin`.

### Cache

Get it with:

```
npm config get cache
```

Output: `~/.npm`

---

## `package.json` and `package-lock.json`
