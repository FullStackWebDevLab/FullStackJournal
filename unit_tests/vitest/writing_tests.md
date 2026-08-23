# Writing Tests

This file covers how to write and organize tests in Vitest.

+ You can use the `test` function to define a test, and `expect` to make assertions.
+ Each test has a name (a string describing what it checks) and a function that contains one or more assetions. If any assertion fails, the test fails.

```js
import { expect, test } from 'vitest'

test('Math.sqrt works for perfect squares', () => {
  expect(Math.sqrt(4)).toBe(2)
  expect(Math.sqrt(144)).toBe(12)
  expect(Math.sqrt(0)).toBe(0)
})
```

+ You may also use `it` instead of `test`. They behave identically. `it` is just an alias that some people prefer because it reads more naturally with a descriptive name:
  ```js
  import { expect, it } from 'vitest'
  
  it('should compute square roots', () => {
    expect(Math.sqrt(4)).toBe(2)
  })
  ```

---

## Grouping Tests With `describe`

+ `describe` creates a test suite, which is a named group of tests.

```
import { describe, expect, test } from 'vitest'

describe('Math.sqrt', () => {
  test('returns the square root of perfect squares', () => {
    expect(Math.sqrt(4)).toBe(2)
    expect(Math.sqrt(9)).toBe(3)
  })

  test('returns NaN for negative numbers', () => {
    expect(Math.sqrt(-1)).toBeNaN()
  })

  test('returns 0 for 0', () => {
    expect(Math.sqrt(0)).toBe(0)
  })
})
```

+ You can nest `describe` blocks for further organization, but keep nesting shallow to preserve readability.

---

## Test Files

+ By default, Vitest looks for any file that contains `.test.` or `.spec.` in its name, such as `utils.test.js`.
+ It searches all subdirectories, so it doesn't matter where you place them. There is no single "right" way to organize your test files. You can place them right next to the source code they test, or in a dedicated directory.
+ If the default patterns don't work for your project, you can customize which files are included with the `include` and `exclude` config options.

---

## Parameterized Tests

When you have several test cases that only differ in their inputs and expected outputs, writing a separate `test` for each one gets repetitive. `test.for` lets you define the cases as data and run the same test logic for all of them.

```
import { expect, test } from 'vitest'

test.for([
  [1, 1, 2],
  [1, 2, 3],
  [2, 1, 3],
])('add(%i, %i) -> %i', ([a, b, expected]) => {
  expect(a + b).toBe(expected)
})
```

The placeholders `%i`, `%s`, and `%f` in the test name are replaced with the corresponding values from each row.

If your cases have more than two or three values, passing objects is more readable. Use `$property` in the name to interpolate fields:

```
test.for([
  { a: 1, b: 1, expected: 2 },
  { a: 1, b: 2, expected: 3 },
  { a: 2, b: 1, expected: 3 },
])('add($a, $b) -> $expected', ({ a, b, expected }) => {
  expect(a + b).toBe(expected)
})
```

**Tip:** Vitest also privides `test.each`. It works similarly but spreads array arguments instead of passing them as a single value, and doesn't provide access to the Test Context. It exists mainly for Jest compatibility. Prefer `test.for` in new code.

---
