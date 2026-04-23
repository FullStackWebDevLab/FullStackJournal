# Functions

This file covers how to write types that describe functions.

## Function Type Expressions

```typescript
function greeter(fn: (a: string) => void) {
  fn("Hello, World");
}
 
function printToConsole(s: string) {
  console.log(s);
}
 
greeter(printToConsole);

// Type aliases are also valid.
type GreetFunction = (a: string) => void;
function greeter(fn: GreetFunction) {}
```

`(a: string) => void` means a function that takes one parameter named `a`, of type `string`, and it doesn't return a value.

The name parameter is required. `(string) => void` means a function that takes a parameter named string of type `any`.

Also, the name of the parameter in the type doesn't have to match the name of the parameter in the function. In the example above, the name of the parameter in the type is `a` and the name of the parameter in the `printToConsole` function is `s`.

---

## Call Signatures

JavaScript functions can ahve properties in addition to being callable. To describe something callable with properties, write a call signature in an object type:

```typescript
type DescribableFunction = {
  description: string;
  (someArg: number): boolean;
};
function doSomething(fn: DescribableFunction) {
  console.log(fn.description + " returned " + fn(6));
}
 
function myFunc(someArg: number) {
  return someArg > 3;
}
myFunc.description = "default description";
 
doSomething(myFunc);
```

---
