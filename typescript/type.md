# Type Aliases

A type alias is a name for any type.

```typescript
type Point = {
    x: number;
    y: number;
}

type ID = number | string;
type userInput = string;

// In use
function printCoord(pt: Point) {}
```

Note that aliases are only aliases. You cannot use type aliases to create different/distinct "versions" of the same type. When you use the alias, it's exactly as if you had written the aliased type. The following example is valid.

```typescript
type UserInputSanitizedString = string;
 
function sanitizeInput(str: string): UserInputSanitizedString {
  return sanitize(str);
}
```

---
