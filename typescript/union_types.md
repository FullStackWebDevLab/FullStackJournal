# Union Types

A union type is a type formed from two or more other types. Values may be any of those types. Each of those types are referred to as the union's members.

```typescript
// id can be number or string.
const id: number | string;

// The separator is allowed before the first element.
function printTextOrNumberOrBool(
  textOrNumberOrBool:
    | string
    | number
    | boolean
) {
  console.log(textOrNumberOrBool);
}
```

Typescript will only allow operations if it is valid for every member of the union.

```typescript
function printId(id: number | string) {
  console.log(id.toUpperCase());
  // This will fail because 'toUpperCase' does not exist on type 'number'.
}

// Solution
function printId(id: number | string) {
  if (typeof id === "string") {
    // In this branch, id is of type 'string'
    console.log(id.toUpperCase());
  } else {
    // Here, id is of type 'number'
    console.log(id);
  }
}

function welcomePeople(x: string[] | string) {
  if (Array.isArray(x)) {
    // Here: 'x' is 'string[]'
    console.log("Hello, " + x.join(" and "));
  } else {
    // Here: 'x' is 'string'
    console.log("Welcome lone traveler " + x);
  }
}
```

---
