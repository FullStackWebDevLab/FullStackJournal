# `useEffect`

`useEffect` lets you synchronize a component with an external system.

```react
useEffect(setup, dependencies?)
```

+ `setup`: The function with you effect's logic.
    This function may also optionally return a cleanup function. React will run the cleanup function:
        + After every commit with changed dependencies (before running the setup function).
        + After your component is removed from the DOM.
+ `dependencies` (optional): The list of all reactive values referenced inside of the `setup` code.
    Reactive values include props, state, and all the variables and functions declared directlry inside your component body. The list of dependencies must have a constant number of items and be written inline like `[dep1, dep2, dep3]`.
    + If you omit this argument, your Effect will re-run after every commit of the component.
    + If you pass an empty array, your Effect will run once after the initial commit of the component, and never run again.
    + If you pass an array of dependencies, your Effect will run after commits where any of the depencies changed.

---
