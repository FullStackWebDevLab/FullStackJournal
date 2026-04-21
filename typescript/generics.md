# Generics

Generics exist to enable creating reusable components, that is, being able to create a component that can work over a variety of types rather than a single one.

## Example: Identity Function

An identity function is a function that will return whatever is passed in.

```javascript
function identity(arg) {
    return arg;
}
```

Arg can be of any type. Here, we can use generics to be able to determine the type of the return value.

```typescript
// The same type is used for the argument and the return value.
function identity<Type>(arg: Type): Type {
    return arg;
}
```

`Type` allows to capture the type the user provides, so it can be used later to determine the type of the return value.

```typescript
let output = identity<string>("myString");
```

Here, the type of the variable `output` is `string`, because `Type` was explicitly set to `string` as one of the arguments using `<>`.

You can fail to pass in the type argument and let the compiler figure out the type using type argument inference.

```typescript
let output = identity("myString");
```

The compiler sees that the type of the argument is `string`, and the type of the return value is the same as the type of the argument, therefore the type of the return value is also `string`.

While type argument inference can be a helpful tool to keep code shorter and more readable, you may need to explicitly pass in the type arguments when the compiler fails to infer the type, as may happen in more complex examples.

**Note**: When using generics, the compiler will enforce that you use any generically typed parameters in the body function correctly.

```typescript
function loggingIdentity<Type>(arg: Type): Type {
  console.log(arg.length);
  // This will fail because the `length` property does not exist for type 'Type'.
  return arg;
}

// Solution 1: Check if 'arg' is an array first.
function loggingIdentity<Type>(arg: Type): Type {
  if (Array.isArray(arg)) {
    console.log(arg.length);
  }
  return arg;
}

// Solution 2: Take an array of 'Type's.
function loggingIdentity<Type>(arg: Array<Type>): Array<Type> {
  console.log(arg.length);
  return arg;
}
```

---

## Type of Generic Functions

What is the type of generic functions like the one below:

```typescript
function identity<Type>(arg: Type): Type {
    return arg;
}
```

```typescript
let myIdentity: <Type>(arg: Type) => Type = identity;

// You could also use a different name for the generic type parameter.
let myIdentity: <Input>(arg: Input) => Input = identity;

// You can also write the generic type as a call signature of an object literal type.
let myIdentity: { <Type>(arg: Type): Type } = identity;
```

---

## Generic Interface

```typescript
interface GenericIdentityFn {
  <Type>(arg: Type): Type;
}
 
function identity<Type>(arg: Type): Type {
  return arg;
}
 
let myIdentity: GenericIdentityFn = identity;
```

```typescript
interface GenericIdentityFn<Type> {
  (arg: Type): Type;
}
 
function identity<Type>(arg: Type): Type {
  return arg;
}
 
let myIdentity: GenericIdentityFn<number> = identity;
```

---

## Generic Classes

```typescript
class GenericNumber<NumType> {
  zeroValue: NumType;
  add: (x: NumType, y: NumType) => NumType;
}
 
let myGenericNumber = new GenericNumber<number>();
myGenericNumber.zeroValue = 0;
myGenericNumber.add = function (x, y) {
  return x + y;
}

let stringNumeric = new GenericNumber<string>();
stringNumeric.zeroValue = "";
stringNumeric.add = function (x, y) {
  return x + y;
};
```

---
