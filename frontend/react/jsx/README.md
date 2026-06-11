# JSX

JSX is a syntax extension for javascript that lets you write HTML-like markup inside a JavaScript file. It looks a lot like HTML, but it is a bit stricter and can display dynamic information.

**Tip:** Use a converter to convert existing HTML code to JSX code.

---

## Rules

### Return a single root element

JSX is transformed into plain JavaScript objects under the hood. In JavaScript you can't return two objects from a function without wrapping them into an array. This is also why you can't return two JSX tags without wrapping them into another tag or a fragment.

To return multiple elements from a component, wrap them with a single parent tag. You can use a `<div>` or a *Fragment* `<>...</>`.

```
<>
  <h1>Hedy Lamarr's Todos</h1>
  <img 
    src="https://i.imgur.com/yXOvdOSs.jpg" 
    alt="Hedy Lamarr" 
    class="photo"
  />
  <ul>
    ...
  </ul>
</>
```

A **Fragment** is an empty tag that lets you group things without leaving any trace in the browser HTML tree.

### Close all the tags

JSX requires tags to be explicitly closed. Self-closing tags like `<img>` must become `<img />`.

### camelCase most of the things

JSX turns into JavaScript and attributes written in JSX become keys of JavaScript objects. Use camelCase due to JavaScript's limitations on variable names.

**Note**: `class` is a reserved word. Use `className` instead.

```
<img 
  src="https://i.imgur.com/yXOvdOSs.jpg" 
  alt="Hedy Lamarr" 
  className="photo"
/>
```

---

## JavaScript in JSX

You can write JavaScript inside JSX using curly braces.

```
export default function TodoList() {
  const name = 'Gregorio Y. Zara';
  return (
    <h1>{name}'s To Do List</h1>
  );
}
```

Any JavaScript expression will work between curly braces.

You can only use curly braces in two ways inside JSX:
1. **As text** inside a JSX tag: `<h1>{name}</h1>`.
2. **As attributes** immediately following the `=` sign: `src={file}`.

The following are invalid:
    + `<{tag}>...</{tag}>`
    + `src="{file}"`: This will pass the string `"{file}"`.

### Objects

Objects are denoted with curly braces. To pass a JavaScript object in JSX, you must wrap the object in another pair of curly braces: `{{ name: "John Doe" }}`.

This can be used with inline CSS styles by passing an object to the `style` attribute.

```
export default function TodoList() {
  return (
    <ul style={{
      backgroundColor: 'black',
      color: 'pink'
    }}>
      <li>Improve the videophone</li>
      <li>Prepare aeronautics lectures</li>
      <li>Work on the alcohol-fuelled engine</li>
    </ul>
  );
}
```

**Note:** Inline `style` properties are written in camelCase.

### Final Example

```
const person = {
  name: 'Gregorio Y. Zara',
  theme: {
    backgroundColor: 'black',
    color: 'pink'
  }
};

export default function TodoList() {
  return (
    <div style={person.theme}>
      <h1>{person.name}'s Todos</h1>
      <img
        className="avatar"
        src="https://i.imgur.com/7vQD0fPs.jpg"
        alt="Gregorio Y. Zara"
      />
      <ul>
        <li>Improve the videophone</li>
        <li>Prepare aeronautics lectures</li>
        <li>Work on the alcohol-fuelled engine</li>
      </ul>
    </div>
  );
}
```

---
