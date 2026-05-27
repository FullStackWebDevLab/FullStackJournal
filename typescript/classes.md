# Classes

## Writing Types For Classes

```ts
interface IMyClass {
    sum(a: number, b: number): number;
    increment(a: number): number;
}

class MyClass implements IMyClass {
    sum(a: number, b: number): number {
        return a+b;
    }

    increment(a: number) {
        return a+1;
    }
}
```

The `implements` keyword allows a class to enforce a specific structure defined by an interface or type alias. It ensures the class contains all the properties and methods required by that contract.

---
