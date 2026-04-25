# JSX

JSX is a syntax extension for javascript that lets you write HTML-like markup inside a JavaScript file. It looks a lot like HTML, but it is a bit stricter and can display dynamic information.

**Tip:** Use a converter to convert existing HTML code to JSX code.

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
