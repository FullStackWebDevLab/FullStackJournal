# Props

React components use props to communicate with each other. Every parent component can pass some information to its child components by giving them props. You can pass any JavaScript value through them, including objects, arrays, and functions.

React component functions accept a single argument, a `props` object:

```
function Component(props) {
  let variable1 = props.variable1;
  let variable2 = props.variable2;
  // ...
}
```

**Note:** Props are immutable. When a component needs to change its props, it will have to ask its parent component to pass it different props. The old props will then be discarded.

---

## Passing props to a component

```
export default function Profile() {
    return (
        <Avatar
         person={{ name: "John Doe", imageId: "1bX5QH6" }}
         size={100}
        />
    );
}

function Avatar({ person, size }) {
    // person and size are available here.
}
```

Listing the names of the props inside `({` and `})` directly after `function Avatar` lets you use them inside the `Avatar` code, like you would a variable.

### Specifying a default value for a prop

```
function Avatar({ person, size = 100 }) {
    // ...
}
```

`size` will default to `100` if the `size` prop is missing or if you pass `size={undefined}`. But if you pass `size={null}` or `size={0}`, the default value will not be used.

### Forwarding props with the JSX spread syntax

Use this syntax when a parent component forwards all its props to their children.

```
function Profile(props) {
  return (
    <div className="card">
      <Avatar {...props} />
    </div>
  );
}
```

This forwards all of `Profile`'s props to the `Avatar` without listing each of their names.

**Note**: Use spread syntax with restraint. If you're using it in every other component, something is wrong. Often, it indicates that you should split your components and pass children as JSX.

---

## Passing JSX as children

Sometimes you'll want to nest your components like you nest built-in browser tags.

```
<Card>
    <Avatar />
</Card>
```

When you nest content inside a JSX tag, the parent component will receive that content in a prop called `children`. For example, the `Card` component will receive a `children` prop set to `<Avatar />`.

```
function Card({ children }) {
    return (
        <div className="card">
            {children}
        </div>
    );
}

export default function Profile() {
  return (
    <Card>
      <Avatar
        size={100}
        person={{ 
          name: 'Katsuko Saruhashi',
          imageId: 'YfeOqp2'
        }}
      />
    </Card>
  );
}
```

---
