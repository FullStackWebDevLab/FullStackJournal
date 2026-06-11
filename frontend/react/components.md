# Components

A component is a piece of the UI that has its own logic and appearance. They are javascript functions that return markup.

**Note:** React component names must always start with a capital letter, while HTML tags must be lowercase.

```
function MyButton() {
  return (
    <button>I'm a button</button>
  );
}

// Nesting
export default function MyApp() {
  return (
    <div>
      <h1>Welcome to my app</h1>
      <MyButton />
    </div>
  );
}
```

---
