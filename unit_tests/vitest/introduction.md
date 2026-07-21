# Vitest

Vitest is a fast testing framework powered by Vite.

## Installing Vitest

```
npm install -D vitest
```

+ Vitest requires Vite >=v6.0.0 and Node >=v20.0.0.

## Writing Tests

+ Files with the tests must contain `.test.` or `.spec.` in their filename. Example: `sum.test.js`.

**Example test:**
```js
// sum.js
export function sum(a, b) {
  return a + b
}

// sum.test.js
import { expect, test } from 'vitest'
import { sum } from './sum.js'

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3)
})
```

Next, add the following section to your `package.json`:

```json
 {
  "scripts": {
    "test": "vitest"
  }
}
```

Finally, run `npm run test`.

Sample output:

```text
✓ sum.test.js (1)
  ✓ adds 1 + 2 to equal 3

Test Files  1 passed (1)
     Tests  1 passed (1)
  Start at  02:15:44
  Duration  311ms
```

---
