# Hooks

Hooks let you use different React features from your components. You can either use the built-in Hooks or combine them to build your own. Hooks start with `use` like `useState`.

## Rules of Hooks

### Only Call Hooks at The Top Level

Don't call hooks inside loops, conditions, nested functions, or `try` / `catch` / `finally` blocks. Always use hooks at the top level of your React function, before any early returns.

```
function Counter() {
    const [count, setCount] = useState(0);
}
```

### Only Call Hooks From React Functions or Custom Hooks

Don't call hooks from regular JavaScript functionsn. Instead, call hooks from react function components or from custom hooks.

---
