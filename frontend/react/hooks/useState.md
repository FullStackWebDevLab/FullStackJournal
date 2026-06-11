# `useState`

`useState` is a React Hook that lets you add a state variable to your component.

**Note:** `useState` is a Hook, so you can only call it at the top level of your component or your own Hooks. You can't call it inside loops or conditions.

```
const [state, setState] = useState(initialState);
```

### Parameters

+ `initialState`: The value you want the state to be initially. It can be a value of any type.
  If you pass a function as the value, it will be treated as an initializer function. It should be pure, should take no arguments, and should return a value of any type. React will call that function when initializing the component, and store its return value as the initial state.

### Return Value

`useState` returns an array with two values:

1. The current state. During the first render, it will match the `initialState` you passed.
2. The `set` function that lets you update the state to a different value and trigger a re-render.

### Example

```
function MyComponent() {
    const [age, setAge] = useState(28);
}
```

---

## Set Function

The `set` function returned by `useState` lets you update the state to a different value and trigger a re-render.

```
setFunction(nextState);
```

### Parameters

+ `nextState`: The value that you want the state to be. It can be a value of any type. It can be a function.
  If you pass a function, it will be treated as an updater function. It must be pure, should take the pending state as its only argument, and should return the next state.

### Return Value

`set` functions do not have a return value.

### Example

```
function MyComponent() {
    const [age, setAge] = useState(28);

    function handleClick() {
        setAge(age + 1);
        // OR
        setAge(a => a + 1);
    }
}
```

---

## Updating Objects and Arrays in State

State is considered read-only, you should replace it rather than mutate your existing objects.

```
// Don't mutate an object in state like this:
form.firstName = "Taylor";

// Create a new object instead.
setForm({
    ...form,
    firstName: "Taylor"
});
```

---

## Caveats

### `set` Function State Update

Calling the `set` function does not change the current state in the already executing code. The `set` function only updates the state variable for the next render. If you read the state variable after calling the `set` function, you will get teh old value that was on the screen before your call.
```
function MyComponent() {
    const [name, setName] = useState("Taylor");
    const [age, setAge] = useState(42);

    function handleClick() {
        setName('Robin');
        console.log(name); // Still "Taylor".

        setAge(age + 1);
        setAge(age + 1);
        setAge(age + 1);
        // Here, age is 43 rather than 45.

        // Solution. Use an updater function.
        setAge(a => a + 1);
        setAge(a => a + 1);
        setAge(a => a + 1);
        // Here, age is 45.
    }
}
```
---
