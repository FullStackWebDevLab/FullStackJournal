# JavaScript Core Syntax Reference

## 1. Variables and Constants

### Declaration Keywords
- `var`: Function-scoped, hoisted, can be re-declared (legacy, discouraged)
- `let`: Block-scoped, not hoisted to usable state, cannot be re-declared
- `const`: Block-scoped, not hoisted to usable state, cannot be reassigned

```javascript
var x = 5;           // function-scoped
let y = 10;          // block-scoped
const Z = 15;        // constant, block-scoped
```

## 2. Data Types

### Primitive Types
- `Number`: Numeric values (integer and floating-point)
- `String`: Text sequences, enclosed in quotes
- `Boolean`: Logical values (`true` or `false`)
- `Undefined`: Declared but uninitialized variables
- `Null`: Intentional absence of value
- `Symbol`: Unique identifiers (ES6)
- `BigInt`: Arbitrary precision integers (ES2020)

### Non-Primitive Type
- `Object`: Collections of key-value pairs; includes arrays, functions, dates

## 3. Operators

### Arithmetic Operators
```javascript
+    // Addition
-    // Subtraction
*    // Multiplication
/    // Division
%    // Modulus (remainder)
**   // Exponentiation (ES7)
++   // Increment
--   // Decrement
```

### Assignment Operators
```javascript
=     // Assignment
+=    // Addition assignment
-=    // Subtraction assignment
*=    // Multiplication assignment
/=    // Division assignment
%=    // Modulus assignment
```

### Comparison Operators
```javascript
==    // Equal to (type coercion)
===   // Strictly equal to (type-safe)
!=    // Not equal to
!==   // Strictly not equal to
>     // Greater than
<     // Less than
>=    // Greater than or equal to
<=    // Less than or equal to
```

### Logical Operators
```javascript
&&    // Logical AND
||    // Logical OR
!     // Logical NOT
```

### Bitwise Operators
```javascript
&     // AND
|     // OR
^     // XOR
~     // NOT
<<    // Left shift
>>    // Right shift
>>>   // Unsigned right shift
```

### Ternary Operator
```javascript
condition ? expressionIfTrue : expressionIfFalse
```

## 4. Control Flow Statements

### Conditional Statements

#### if Statement
```javascript
if (condition) {
    // executed if condition is true
}
```

#### if-else Statement
```javascript
if (condition) {
    // executed if condition is true
} else {
    // executed if condition is false
}
```

#### if-else if-else Statement
```javascript
if (condition1) {
    // executed if condition1 is true
} else if (condition2) {
    // executed if condition2 is true
} else {
    // executed if all conditions are false
}
```

#### switch Statement
```javascript
switch (expression) {
    case value1:
        // code block
        break;
    case value2:
        // code block
        break;
    default:
        // default code block
}
```

### Iteration Statements

#### for Loop
```javascript
for (initialization; condition; post_iteration) {
    // code block
}
```

#### while Loop
```javascript
while (condition) {
    // code block
}
```

#### do-while Loop
```javascript
do {
    // code block
} while (condition);
```

#### for-in Loop
```javascript
for (variable in object) {
    // code block
}
```

#### for-of Loop (ES6)
```javascript
for (variable of iterable) {
    // code block
}
```

### Jump Statements
```javascript
break;      // Exits loop or switch
continue;   // Skips current iteration
```

## 5. Functions

### Function Declaration
```javascript
function functionName(parameter1, parameter2) {
    // function body
    return value;
}
```

### Function Expression
```javascript
const functionName = function(parameter1, parameter2) {
    // function body
    return value;
};
```

### Arrow Function (ES6)
```javascript
const functionName = (parameter1, parameter2) => {
    // function body
    return value;
};

// Concise syntax for single expression
const functionName = (parameter1, parameter2) => expression;

// Single parameter unnamed function
parameter => { /* Function body */ }
// This type of function is usually passed as a parameter.
```

### Immediately Invoked Function Expression (IIFE)
```javascript
(function() {
    // code
})();
```

## 6. Objects

### Object Literal
```javascript
const object = {
    property1: value1,
    property2: value2,
    method: function() {
        // method body
    }
};
```

### Property Access
```javascript
object.property         // Dot notation
object['property']      // Bracket notation
```

### Object Destructuring (ES6)
```javascript
const { property1, property2 } = object;
```

## 7. Arrays

### Array Literal
```javascript
const array = [element1, element2, element3];
```

### Array Access
```javascript
array[index]            // Access element at index
array.length            // Array length
```

### Array Destructuring (ES6)
```javascript
const [first, second, third] = array;
```

## 8. Classes (ES6)

### Class Declaration
```javascript
class ClassName {
    constructor(parameter) {
        this.property = parameter;
    }
    
    method() {
        // method body
    }
}
```

### Class Instantiation
```javascript
const instance = new ClassName(argument);
```

### Class Inheritance
```javascript
class ChildClass extends ParentClass {
    constructor(parameter) {
        super(parameter);
        // additional initialization
    }
}
```

## 9. Template Literals (ES6)

```javascript
const string = `Text ${expression} more text`;
```

## 10. Spread and Rest Operators (ES6)

### Spread Operator
```javascript
const newArray = [...array1, ...array2];
const newObject = {...object1, ...object2};
```

### Rest Parameter
```javascript
function functionName(...parameters) {
    // parameters is an array
}
```

## 11. Error Handling

### try-catch-finally
```javascript
try {
    // code that may throw error
} catch (error) {
    // error handling
} finally {
    // always executed
}
```

### throw Statement
```javascript
throw new Error('Error message');
```

## 12. Comments

```javascript
// Single-line comment

/*
   Multi-line
   comment
*/
```

## 13. Strict Mode

```javascript
'use strict';
// Enforces stricter parsing and error handling
```

## 14. Type Coercion

JavaScript automatically converts types in certain contexts. Use strict equality (`===`) to avoid unintended coercion.

### Falsy Values
- `false`
- `0`
- `''` (empty string)
- `null`
- `undefined`
- `NaN`

All other values are truthy.

## 15. Operator Precedence

Operators are evaluated in the following order (highest to lowest):
1. Grouping: `()`
2. Member access: `.` `[]`
3. Function call: `()`
4. Postfix increment/decrement: `++` `--`
5. Logical NOT, Unary negation: `!` `-`
6. Exponentiation: `**`
7. Multiplication, Division, Modulus: `*` `/` `%`
8. Addition, Subtraction: `+` `-`
9. Relational: `<` `<=` `>` `>=`
10. Equality: `==` `===` `!=` `!==`
11. Logical AND: `&&`
12. Logical OR: `||`
13. Ternary: `? :`
14. Assignment: `=` `+=` `-=` etc.

## 16. Semicolons

Statements are terminated by semicolons (`;`). JavaScript employs Automatic Semicolon Insertion (ASI), but explicit semicolons are recommended to prevent errors.

## 17. Naming Conventions

- Variables and functions: camelCase (`myVariable`, `functionName`)
- Constants: UPPER_CASE (`MAX_VALUE`)
- Classes: PascalCase (`ClassName`)
- Variables must begin with letter, underscore (`_`), or dollar sign (`$`)
- Case-sensitive: `myVar` ≠ `myvar`
- Reserved keywords cannot be used as identifiers

---
