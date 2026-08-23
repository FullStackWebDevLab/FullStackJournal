# Test Filtering

Test filtering lets you narrow down which tests run. Vitest offers several ways to filter tests: from the command line, inside your test files, and through tags.

## Filtering by File Name

You can pass a filename pattern as a CLI argument. Vitest will only run files whose path contains the given string.

+ Example: `vitest basic`.
+ This matches any test file with `basic` in its path: `basic.test.ts`, `basic-foo.test.ts`, `basic/foo.test.ts`.

---

## Filtering by Test Name

The `-t`/`--testNamePattern` option filters by the test's name rather than the filename. It accepts a regex pattern and matches against the full test name, which includes any `describe` block names.

Example: `vitest -t "handles empty input"`. This runs only tests whose name matches `"handles empty input"`.

---

## Filtering by Line Number

You can also point directly to a line number.

```
vitest basic/foo.test.ts:10
```

Vitest will run the test on line 10. This requires the full filename (relative or absolute).

To run multiple line specific tests, separate them with spaces.

```
vitest basic/foo.test.ts:10 basic/foo.test.ts:25
```

---

## Filtering by Tags

You can categorize tests and run them by category. Tags let you label tests and then filter by those labels from the CLI.

```
test('renders a form', { tags: ['frontend'] }, () => {
  // ...
})

test('calls an external API', { tags: ['backend'] }, () => {
  // ...
})
```

```
vitest --tags-filter=frontend
```

---

## `.only`

`.only` tells Vitest to run only this test (or suite) and skip everything else in the file.

```
import { describe, expect, it } from 'vitest'

describe.only('suite', () => {
  it('test', () => {
    // This runs because the suite is marked with .only
    expect(Math.sqrt(4)).toBe(2)
  })
})

describe('another suite', () => {
  it('skipped test', () => {
    // This does not run
    expect(Math.sqrt(4)).toBe(2)
  })

  it.only('focused test', () => {
    // This also runs because it is marked with .only
    expect(Math.sqrt(4)).toBe(2)
  })
})
```

You can use `.only` on both `describe` blocks and individual tests.

**Note:** Remember to remove `.only` before committing. By default, Vitest will fail the entire test run if it encounters `.only` in CI (when `process.env.CI` is set), preventing you from accidentally skipping tests in your pipeline. This behavior is controlled by the `allowOnly` option.

---

## `.skip`

`.skip` skips a test without removing it. It can be useful when a test is temporarily broken or you want to ignore it.

```
import { describe, expect, it } from 'vitest'

describe.skip('skipped suite', () => {
  it('test', () => {
    // This entire suite is skipped
    expect(Math.sqrt(4)).toBe(2)
  })
})

describe('suite', () => {
  it.skip('skipped test', () => {
    // Just this one test is skipped
    expect(Math.sqrt(4)).toBe(2)
  })
})
```

---

## `.todo`

`.todo` marks a test as planned but not yet written. It shows up in the report as a reminder.

```
import { describe, it } from 'vitest'

describe.todo('unimplemented suite')

describe('suite', () => {
  it.todo('unimplemented test')
})
```

`.todo` test has no test body. It is purely a placeholder for future work.

---
