# Deep Clone

To get a deep clone of something, use the `structuredClone()` method.

```javascript
const originalArray = [1, [2, 3], { a: 4, b: 5 }];

// Create a deep copy
const deepCopyArray = structuredClone(originalArray);

// Modify the deep copy
deepCopyArray[1][0] = 99;
deepCopyArray[2].a = 100;

console.log(deepCopyArray); // Output: [1, [99, 3], { a: 100, b: 5 }]
console.log(originalArray); // Output: [1, [2, 3], { a: 4, b: 5 }] (Original remains unchanged)
```

---
