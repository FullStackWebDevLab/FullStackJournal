# `execSync`

`execSync` runs a system command from a JavaScript program and waits until the command finishes before continuing. It executes the command synchronously, meaning the program is paused while the command runs, and it can return the command’s output as a value.


```
execSync(command[, options])
```

+ `command`: `<string>` The command to run.
+ `options`: `<object>`
  - `encoding`: `<string>` The encoding used for all stdio inputs and outputs. Default: `'buffer'`.
  - Other options not documented here are: cwd, input, stdio, env, shell, uid, gid, timeout, killSignal, maxBuffer, windowsHide. They are documented in the nodejs docset.
+ Returns: `<Buffer>` | `<string>` The stdout from the command.

---
