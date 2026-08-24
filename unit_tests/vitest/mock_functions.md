# Mock Functions

Mock functions let you control what a dependency returns, observe how it was called, and isolate the code under test from side effects. Vitest provides mocking utilities through the `vi` object.

The simplest way to create a mock is with `vi.fn()`. This returns a function that returns `undefined` by default, but tracks every call made to it.

```
import { expect, test, vi } from 'vitest'

test('mock function basics', () => {
  const getApples = vi.fn()

  // Call it
  getApples()

  // Check it was called
  expect(getApples).toHaveBeenCalled()
  expect(getApples).toHaveBeenCalledTimes(1)

  // By default, a mock returns undefined
  expect(getApples()).toBeUndefined()
})
```

Setting return values for mock functions.

```
import { expect, test, vi } from 'vitest'

test('mock return values', () => {
  const getApples = vi.fn()

  // Always return this value
  getApples.mockReturnValue(10)
  expect(getApples()).toBe(10)

  // Return this value only once, then fall back to the default
  getApples.mockReturnValueOnce(20)
  expect(getApples()).toBe(20) // 20 (one-time)
  expect(getApples()).toBe(10) // back to default
})
```

If the function you're mocking is async, use `mockResolvedValue` and `mockRejectedValue` to control the promise outcome.

```
test('mock async return values', async () => {
  const fetchUser = vi.fn()

  fetchUser.mockResolvedValue({ name: 'Alice' })
  const user = await fetchUser()
  expect(user.name).toBe('Alice')

  fetchUser.mockRejectedValue(new Error('Not found'))
  await expect(fetchUser()).rejects.toThrow('Not found')
})
```

When you want the mock function to actually do something, `mockImplementation` lets you provide a full replacement function:

```
import { expect, test, vi } from 'vitest'

test('mock with custom implementation', () => {
  const add = vi.fn()
  add.mockImplementation((a, b) => a + b)

  expect(add(1, 2)).toBe(3)
  expect(add(10, 20)).toBe(30)
})
```

```
const add = vi.fn((a, b) => a + b)
```

You can assert on how many times a function was called, what arguments it received, and what it returned:

```
import { expect, test, vi } from 'vitest'

test('inspecting mock calls', () => {
  const greet = vi.fn()

  greet('Alice')
  greet('Bob', 'Charlie')

  // Number of calls
  expect(greet).toHaveBeenCalledTimes(2)

  // Check specific arguments
  expect(greet).toHaveBeenCalledWith('Alice')
  expect(greet).toHaveBeenCalledWith('Bob', 'Charlie')

  // Check the arguments of a specific call by position
  expect(greet).toHaveBeenNthCalledWith(1, 'Alice')
  expect(greet).toHaveBeenLastCalledWith('Bob', 'Charlie')

  // Access the raw call data
  expect(greet.mock.calls).toEqual([
    ['Alice'],
    ['Bob', 'Charlie'],
  ])
})
```

The `.mock` property gives you full access to the call history. In addition to `.mock.calls`, you can also inspect `.mock.results` to see what the mock returned (or threw) on each call.

---
