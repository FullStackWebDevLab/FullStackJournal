# Tips

## List Items

For each item in a list, you should pass a string or a number that uniquely identifies that item among its siblings.

```
const listItems = products.map(product =>
  <li key={product.id}>
    {product.title}
  </li>
);

return (
  <ul>{listItems}</ul>
);
```

React uses your keys to know what happend if you later insert, delete, or reorder the items.

---
