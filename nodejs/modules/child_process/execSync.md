# `execSync`

`execSync` runs a system command from a JavaScript program and waits until the command finishes before continuing. It executes the command synchronously, meaning the program is paused while the command runs, and it can return the command’s output as a value.


```
execSync(command[, options])
```

+ `command`: `<string>` The command to run.
+ `options`: `<object>`
  - `cwd`: `<string>` | `<URL>` Current working directory of the child process.
  - `encoding`: `<string>` The encoding used for all stdio inputs and outputs. Default: `'buffer'`.
  - `stdio`: `<string>` | `<Array>` Child's stdio configuration. Where the output of the child will be shown. `stderr` by default will be output to the parent process' stderr. Default: `'pipe'`. `'inherit'` will show all the output on the parent process' stdio.
  - Other options not documented here are: input, env, shell, uid, gid, timeout, killSignal, maxBuffer, windowsHide. They are documented in the nodejs docset.
+ Returns: `<Buffer>` | `<string>` The stdout from the command.

---
