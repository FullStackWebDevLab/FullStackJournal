# `interface`

The `interface` declaration allows you to tell typescript what the types should be when they can't be inferred automatically.

```javascript
// Here, 'name' and 'id' types can't be inferred automatically.
const user = {
    name: "John",
    id: 0
};
```

```typescript
// Describe this object's shape using an interface declaration.
interface User {
    name: string;
    id: number;
}

// Declare that an object conforms to the new interface.
const user: User = {
    name: "John",
    id: 0
};

// Use in function parameters and return values.
function deleteUser(user: User) {
    // ...
}
function getAdminUser(): User {
    //...
}

// Use in classes.
class UserAccount {
    constructor(name: string, id: number) {
        this.name = name;
        this.id = id;
    }
}

const user: User = new UserAccount("John", 0);
```

---
