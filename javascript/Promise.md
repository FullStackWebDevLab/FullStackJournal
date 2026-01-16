# JavaScript Promise Object Reference

## Introduction

A Promise is an object that represents the eventual completion or failure of an asynchronous operation. It allows you to attach handlers to an asynchronous action's eventual success value or failure reason.

## Promise States

A Promise can be in one of three states:

- **Pending**: The initial state. The asynchronous operation has not completed yet.
- **Fulfilled**: The operation completed successfully, and the promise has a result value.
- **Rejected**: The operation failed, and the promise has a reason for the failure.

Once a promise is fulfilled or rejected, it is considered settled. A settled promise cannot change its state.

## Constructor

### Promise()

Creates a new Promise object.

**Syntax:**
```javascript
new Promise(executor)
```

**Parameters:**
- `executor`: A function that executes immediately when the promise is created. It receives two functions as parameters:
  - `resolve(value)`: Call this function when the operation succeeds. The value becomes the fulfillment value.
  - `reject(reason)`: Call this function when the operation fails. The reason is typically an Error object.

**Example:**
```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const success = true;
    if (success) {
      resolve("Operation completed");
    } else {
      reject(new Error("Operation failed"));
    }
  }, 1000);
});
```

## Static Methods

Static methods are called on the Promise constructor itself, not on promise instances.

### Promise.all()

Takes an array of promises and returns a single promise. This promise fulfills when all input promises fulfill, or rejects when any input promise rejects.

**Syntax:**
```javascript
Promise.all(iterable)
```

**Parameters:**
- `iterable`: An array or other iterable object of promises.

**Returns:**
- A promise that fulfills with an array of fulfillment values in the same order as the input promises.
- Rejects immediately with the first rejection reason if any promise rejects.

**Example:**
```javascript
const promise1 = Promise.resolve(3);
const promise2 = Promise.resolve(42);
const promise3 = Promise.resolve("foo");

Promise.all([promise1, promise2, promise3]).then((values) => {
  console.log(values); // [3, 42, "foo"]
});
```

### Promise.allSettled()

Takes an array of promises and returns a single promise. This promise fulfills when all input promises settle, regardless of whether they fulfill or reject.

**Syntax:**
```javascript
Promise.allSettled(iterable)
```

**Parameters:**
- `iterable`: An array or other iterable object of promises.

**Returns:**
- A promise that always fulfills with an array of objects. Each object describes the outcome of each promise:
  - `{ status: "fulfilled", value: result }` for fulfilled promises
  - `{ status: "rejected", reason: error }` for rejected promises

**Example:**
```javascript
const promise1 = Promise.resolve(3);
const promise2 = Promise.reject("error");
const promise3 = Promise.resolve(42);

Promise.allSettled([promise1, promise2, promise3]).then((results) => {
  console.log(results);
  // [
  //   { status: "fulfilled", value: 3 },
  //   { status: "rejected", reason: "error" },
  //   { status: "fulfilled", value: 42 }
  // ]
});
```

### Promise.any()

Takes an array of promises and returns a single promise. This promise fulfills when any input promise fulfills, or rejects when all input promises reject.

**Syntax:**
```javascript
Promise.any(iterable)
```

**Parameters:**
- `iterable`: An array or other iterable object of promises.

**Returns:**
- A promise that fulfills with the value from the first promise to fulfill.
- Rejects with an AggregateError if all promises reject. The AggregateError contains all rejection reasons.

**Example:**
```javascript
const promise1 = Promise.reject("error1");
const promise2 = Promise.resolve(42);
const promise3 = Promise.resolve(100);

Promise.any([promise1, promise2, promise3]).then((value) => {
  console.log(value); // 42 (first fulfilled promise)
});
```

### Promise.race()

Takes an array of promises and returns a single promise. This promise settles with the state of the first promise that settles, whether it fulfills or rejects.

**Syntax:**
```javascript
Promise.race(iterable)
```

**Parameters:**
- `iterable`: An array or other iterable object of promises.

**Returns:**
- A promise that settles the same way as the first promise in the array to settle.

**Example:**
```javascript
const promise1 = new Promise((resolve) => setTimeout(resolve, 500, "one"));
const promise2 = new Promise((resolve) => setTimeout(resolve, 100, "two"));

Promise.race([promise1, promise2]).then((value) => {
  console.log(value); // "two" (promise2 settles first)
});
```

### Promise.resolve()

Returns a promise that is resolved with a given value. If the value is a promise, that promise is returned. If the value is a thenable object, it will be converted to a promise.

**Syntax:**
```javascript
Promise.resolve(value)
```

**Parameters:**
- `value`: The value to resolve the promise with. Can be a value, a promise, or a thenable object.

**Returns:**
- A promise that is resolved with the given value.

**Example:**
```javascript
Promise.resolve("Success").then((value) => {
  console.log(value); // "Success"
});

// Resolving with another promise
const promise = Promise.resolve(42);
Promise.resolve(promise).then((value) => {
  console.log(value); // 42
});
```

### Promise.reject()

Returns a promise that is rejected with a given reason.

**Syntax:**
```javascript
Promise.reject(reason)
```

**Parameters:**
- `reason`: The reason for rejection. Typically an Error object.

**Returns:**
- A promise that is rejected with the given reason.

**Example:**
```javascript
Promise.reject(new Error("Failed")).catch((error) => {
  console.error(error.message); // "Failed"
});
```

### Promise.withResolvers()

Returns an object containing a new promise and its resolve and reject functions. This allows you to resolve or reject the promise from outside the executor function.

**Syntax:**
```javascript
Promise.withResolvers()
```

**Returns:**
- An object with three properties:
  - `promise`: A new Promise object
  - `resolve`: A function to resolve the promise
  - `reject`: A function to reject the promise

**Example:**
```javascript
const { promise, resolve, reject } = Promise.withResolvers();

setTimeout(() => {
  resolve("Resolved after delay");
}, 1000);

promise.then((value) => {
  console.log(value); // "Resolved after delay"
});
```

### Promise.try()

Executes a callback function and wraps its result in a promise. This is useful for handling functions that may throw errors synchronously or return promises.

**Syntax:**
```javascript
Promise.try(func)
Promise.try(func, arg1, arg2, ...)
```

**Parameters:**
- `func`: A function to execute. Can be synchronous or asynchronous.
- `arg1, arg2, ...`: Optional arguments to pass to the function.

**Returns:**
- A promise that fulfills with the return value if the function succeeds.
- A promise that rejects if the function throws an error or returns a rejected promise.

**Example:**
```javascript
function mightThrow() {
  if (Math.random() > 0.5) {
    throw new Error("Random error");
  }
  return "Success";
}

Promise.try(mightThrow)
  .then((result) => console.log(result))
  .catch((error) => console.error(error.message));
```

## Instance Methods

Instance methods are called on promise objects.

### then()

Attaches handlers to the promise for when it fulfills or rejects. Returns a new promise, allowing for method chaining.

**Syntax:**
```javascript
promise.then(onFulfilled)
promise.then(onFulfilled, onRejected)
```

**Parameters:**
- `onFulfilled`: A function to execute when the promise fulfills. Receives the fulfillment value as an argument.
- `onRejected` (optional): A function to execute when the promise rejects. Receives the rejection reason as an argument.

**Returns:**
- A new promise that resolves based on the return value of the handler function.

**Example:**
```javascript
const promise = Promise.resolve(10);

promise.then((value) => {
  console.log(value); // 10
  return value * 2;
}).then((value) => {
  console.log(value); // 20
});
```

### catch()

Attaches a handler for when the promise rejects. This is a shorthand for `then(undefined, onRejected)`.

**Syntax:**
```javascript
promise.catch(onRejected)
```

**Parameters:**
- `onRejected`: A function to execute when the promise rejects. Receives the rejection reason as an argument.

**Returns:**
- A new promise. If the handler function returns a value, the returned promise fulfills with that value.

**Example:**
```javascript
const promise = Promise.reject(new Error("Something failed"));

promise.catch((error) => {
  console.error(error.message); // "Something failed"
});
```

### finally()

Attaches a handler that executes when the promise settles, regardless of whether it fulfills or rejects. This is useful for cleanup operations.

**Syntax:**
```javascript
promise.finally(onFinally)
```

**Parameters:**
- `onFinally`: A function to execute when the promise settles. This function receives no arguments.

**Returns:**
- A new promise that settles with the same state and value as the original promise.

**Example:**
```javascript
let isLoading = true;

fetch("/api/data")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error(error))
  .finally(() => {
    isLoading = false;
    console.log("Request completed");
  });
```

## Properties

### Promise.prototype.constructor

References the constructor function that created the instance. For Promise instances, this is the Promise constructor.

### Promise.prototype[Symbol.toStringTag]

Returns the string "Promise". This property is used by `Object.prototype.toString()`.

**Example:**
```javascript
const promise = new Promise(() => {});
console.log(Object.prototype.toString.call(promise)); // "[object Promise]"
```

## Internal Properties

Promises have internal properties that are not directly accessible:

- `[[PromiseState]]`: The current state (pending, fulfilled, or rejected)
- `[[PromiseResult]]`: The fulfillment value or rejection reason

These properties can only be accessed through the promise methods like `then()`, `catch()`, and `finally()`.

## Promise Chaining

Promises can be chained to perform sequential asynchronous operations. Each `then()`, `catch()`, or `finally()` call returns a new promise.

**Example:**
```javascript
fetch("/api/user")
  .then((response) => response.json())
  .then((user) => fetch(`/api/posts/${user.id}`))
  .then((response) => response.json())
  .then((posts) => console.log(posts))
  .catch((error) => console.error("Error:", error))
  .finally(() => console.log("All operations completed"));
```

## Error Handling

Errors in promises are handled through the `catch()` method or the rejection handler in `then()`. Any synchronous error thrown in the executor function or in a handler will be caught and converted to a rejection.

**Example:**
```javascript
new Promise((resolve, reject) => {
  throw new Error("Error in executor");
})
.catch((error) => {
  console.error(error.message); // "Error in executor"
});
```

## Best Practices

1. Always handle rejections with `catch()` or a rejection handler to avoid unhandled promise rejections.
2. Use `Promise.all()` when you need all operations to complete successfully.
3. Use `Promise.allSettled()` when you want to wait for all operations regardless of success or failure.
4. Use `Promise.race()` for timeout implementations or when you only need the first result.
5. Use `finally()` for cleanup operations that should run regardless of success or failure.
6. Return promises from `then()` handlers to maintain proper chaining.
7. Prefer `async/await` syntax for cleaner asynchronous code when appropriate.

## Compatibility

All Promise methods and properties covered in this document are part of the ECMAScript standard. The availability of specific features varies:

- Basic Promise support: ES2015 (ES6)
- `Promise.allSettled()`: ES2020
- `Promise.any()`: ES2021
- `finally()`: ES2018
- `Promise.withResolvers()`: ES2024
- `Promise.try()`: ES2024 (newest addition)

Always check browser compatibility for newer features when targeting older environments.

---
