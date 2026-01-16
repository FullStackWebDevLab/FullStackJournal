# JavaScript JSON Object Reference

## Overview

JSON (JavaScript Object Notation) is a built-in global object in JavaScript. It provides methods for working with JSON data format. JSON is not a constructor and cannot be used with the `new` operator. All properties and methods of JSON are static.

## What is JSON Format?

JSON is a lightweight data format for storing and exchanging data. It is based on JavaScript syntax but is a distinct format. JSON represents data using:

- Objects (key-value pairs in curly braces)
- Arrays (ordered lists in square brackets)
- Strings (double-quoted text)
- Numbers (integers or decimals)
- Booleans (`true` or `false`)
- Null (`null`)

## JSON Format Rules

JSON has strict rules that differ from JavaScript:

1. Property names must be double-quoted strings
2. Only double-quoted strings are allowed (no single quotes)
3. Trailing commas are forbidden
4. Leading zeros in numbers are prohibited
5. A decimal point must be followed by at least one digit
6. `NaN` and `Infinity` are not supported
7. `undefined` is not supported
8. Comments are not allowed
9. No function values
10. No symbol values
11. No circular references

## Properties

### JSON[Symbol.toStringTag]

**Type:** String property

**Value:** `"JSON"`

**Description:** This property is used by `Object.prototype.toString()` to create the string description of the JSON object. When you call `Object.prototype.toString.call(JSON)`, it returns `"[object JSON]"`.

**Characteristics:**
- Not writable
- Not enumerable
- Configurable

**Example:**
```javascript
Object.prototype.toString.call(JSON);
// Returns: "[object JSON]"
```

## Methods

### JSON.parse()

**Syntax:**
```javascript
JSON.parse(text)
JSON.parse(text, reviver)
```

**Description:** Converts a JSON string into a JavaScript value or object.

**Parameters:**

1. **text** (required)
   - Type: String
   - The string to parse as JSON
   - Must be valid JSON format

2. **reviver** (optional)
   - Type: Function
   - A function that transforms values before they are returned
   - Called for each property in the parsed object
   - Receives three arguments:
     - `key`: The property name (string)
     - `value`: The property value
     - `context`: Contains state information (including `source` property for the original text)

**Return Value:** The JavaScript value or object that corresponds to the JSON text.

**How reviver Works:**

The reviver function is called in a specific order:
1. First called for nested properties (depth-first)
2. Then called for parent properties
3. Finally called with an empty string key and the entire object as the value

The `this` value inside the reviver is the object containing the property being processed (unless using arrow functions).

**Examples:**

Basic parsing:
```javascript
const json = '{"name": "John", "age": 30}';
const obj = JSON.parse(json);
console.log(obj.name); // "John"
console.log(obj.age);  // 30
```

Parsing different types:
```javascript
JSON.parse('{}');              // {}
JSON.parse('true');            // true
JSON.parse('"hello"');         // "hello"
JSON.parse('[1, 5, "false"]'); // [1, 5, "false"]
JSON.parse('null');            // null
```

Using reviver to transform values:
```javascript
const json = '{"date": "2024-01-15T10:30:00.000Z"}';

const obj = JSON.parse(json, (key, value) => {
  if (key === 'date') {
    return new Date(value);
  }
  return value;
});

console.log(obj.date instanceof Date); // true
```

Using reviver to filter properties:
```javascript
const json = '{"a": 1, "b": 2, "c": 3}';

const obj = JSON.parse(json, (key, value) => {
  if (key === 'b') {
    return undefined; // Excludes this property
  }
  return value;
});

console.log(obj); // {a: 1, c: 3}
```

Transforming numbers with context.source:
```javascript
const json = '{"bigNumber": 12345678901234567890}';

const obj = JSON.parse(json, (key, value, context) => {
  if (key === 'bigNumber') {
    // Use context.source to get original string before precision loss
    return BigInt(context.source);
  }
  return value;
});
```

**Errors:**

Throws a `SyntaxError` if the text is not valid JSON:
```javascript
try {
  JSON.parse('{invalid}');
} catch (error) {
  console.error('Invalid JSON:', error.message);
}
```

---

### JSON.stringify()

**Syntax:**
```javascript
JSON.stringify(value)
JSON.stringify(value, replacer)
JSON.stringify(value, replacer, space)
```

**Description:** Converts a JavaScript value to a JSON string.

**Parameters:**

1. **value** (required)
   - Type: Any
   - The value to convert to a JSON string

2. **replacer** (optional)
   - Type: Function or Array
   - Controls which properties are included and how values are transformed
   
   **As a function:**
   - Receives two arguments: `key` and `value`
   - The object containing the property is available as `this`
   - Called first with the object itself (empty string key)
   - Then called for each property
   - Return `undefined` to exclude a property
   
   **As an array:**
   - Contains property names to include in the output
   - Only string and number values are used
   - Symbol keys are ignored

3. **space** (optional)
   - Type: String or Number
   - Adds whitespace for readability
   
   **As a number:**
   - Specifies number of space characters for indentation
   - Clamped to 10 (maximum)
   - Values less than 1 mean no spacing
   
   **As a string:**
   - Used as the indentation string
   - Truncated to 10 characters if longer

**Return Value:** A JSON string representing the value, or `undefined` if conversion fails.

**What Gets Stringified:**

Included values:
- Objects (only enumerable own properties)
- Arrays
- Strings
- Numbers (except `NaN` and `Infinity`, which become `null`)
- Booleans
- `null`

Excluded values (result in `undefined` or are omitted):
- Functions
- `undefined`
- Symbols
- Properties with `undefined` values (in objects)
- Non-enumerable properties
- Properties from prototypes

Special cases:
- `Date` objects: Converted to ISO strings via `toJSON()`
- `NaN` and `Infinity`: Become `null`
- Maps, Sets, WeakMaps, WeakSets: Become `{}`
- Typed Arrays: Serialized as arrays
- BigInt: Throws TypeError (cannot be serialized)

**Examples:**

Basic stringification:
```javascript
const obj = {name: 'Alice', age: 25};
const json = JSON.stringify(obj);
console.log(json); // '{"name":"Alice","age":25}'
```

With formatting (space parameter):
```javascript
const obj = {name: 'Alice', age: 25, city: 'NYC'};

// Using number for spaces
console.log(JSON.stringify(obj, null, 2));
// {
//   "name": "Alice",
//   "age": 25,
//   "city": "NYC"
// }

// Using string for indentation
console.log(JSON.stringify(obj, null, '--'));
// {
// --"name": "Alice",
// --"age": 25,
// --"city": "NYC"
// }
```

Using replacer as an array (whitelist properties):
```javascript
const obj = {
  name: 'Bob',
  age: 30,
  password: 'secret123',
  city: 'London'
};

const json = JSON.stringify(obj, ['name', 'city']);
console.log(json); // '{"name":"Bob","city":"London"}'
```

Using replacer as a function (transform values):
```javascript
const obj = {
  name: 'Charlie',
  age: 35,
  password: 'mypassword'
};

const json = JSON.stringify(obj, (key, value) => {
  if (key === 'password') {
    return undefined; // Exclude password
  }
  if (key === 'age') {
    return value + 1; // Transform age
  }
  return value;
});

console.log(json); // '{"name":"Charlie","age":36}'
```

Handling Sets and Maps with replacer:
```javascript
const obj = {
  name: 'Dave',
  tags: new Set(['js', 'web', 'coding'])
};

const json = JSON.stringify(obj, (key, value) => {
  if (value instanceof Set) {
    return Array.from(value);
  }
  return value;
});

console.log(json); // '{"name":"Dave","tags":["js","web","coding"]}'
```

Nested objects are automatically handled:
```javascript
const obj = {
  user: {
    name: 'Eve',
    details: {
      age: 28,
      location: 'Paris'
    }
  }
};

console.log(JSON.stringify(obj, null, 2));
// {
//   "user": {
//     "name": "Eve",
//     "details": {
//       "age": 28,
//       "location": "Paris"
//     }
//   }
// }
```

**Custom toJSON() method:**

Objects can define a `toJSON()` method to customize serialization:
```javascript
const obj = {
  name: 'Frank',
  date: new Date('2024-01-15'),
  toJSON() {
    return {
      name: this.name,
      dateString: this.date.toISOString()
    };
  }
};

console.log(JSON.stringify(obj));
// '{"name":"Frank","dateString":"2024-01-15T00:00:00.000Z"}'
```

**Errors:**

Throws `TypeError` for:
- Circular references
- BigInt values

```javascript
// Circular reference
const obj = {name: 'Alice'};
obj.self = obj;

try {
  JSON.stringify(obj);
} catch (error) {
  console.error('Error:', error.message);
  // Error: Converting circular structure to JSON
}

// BigInt
try {
  JSON.stringify({value: 123n});
} catch (error) {
  console.error('Error:', error.message);
  // Error: Do not know how to serialize a BigInt
}
```

## Common Use Cases

### 1. Data Storage

```javascript
// Save to localStorage
const user = {name: 'Alice', age: 30};
localStorage.setItem('user', JSON.stringify(user));

// Retrieve from localStorage
const stored = localStorage.getItem('user');
const parsed = JSON.parse(stored);
```

### 2. API Communication

```javascript
// Sending data
fetch('/api/users', {
  method: 'POST',
  headers: {'Content-Type': 'application/json'},
  body: JSON.stringify({name: 'Bob', email: 'bob@example.com'})
});

// Receiving data
fetch('/api/users/1')
  .then(response => response.json())
  .then(data => console.log(data));
```

### 3. Deep Cloning Objects

```javascript
const original = {name: 'Charlie', hobbies: ['reading', 'coding']};
const clone = JSON.parse(JSON.stringify(original));

// Note: This only works for JSON-serializable values
// Functions, undefined, Symbols, etc. will be lost
```

### 4. Data Validation

```javascript
function isValidJSON(text) {
  try {
    JSON.parse(text);
    return true;
  } catch {
    return false;
  }
}

console.log(isValidJSON('{"valid": true}'));  // true
console.log(isValidJSON('{invalid}'));        // false
```

### 5. Custom Date Serialization

```javascript
// Serialize dates as timestamps
const data = {
  event: 'Meeting',
  date: new Date('2024-01-15')
};

const json = JSON.stringify(data, (key, value) => {
  if (value instanceof Date) {
    return value.getTime();
  }
  return value;
});

// Deserialize timestamps back to dates
const parsed = JSON.parse(json, (key, value) => {
  if (key === 'date') {
    return new Date(value);
  }
  return value;
});
```

## Performance Considerations

1. **Speed:** `JSON.parse()` and `JSON.stringify()` are highly optimized in modern browsers
2. **Large data:** For very large objects, consider streaming or chunking
3. **Deep cloning:** For performance-critical code, specialized libraries may be faster than `JSON.parse(JSON.stringify())`
4. **Avoid unnecessary conversions:** Cache stringified results when possible

## Browser and Node.js Support

JSON is supported in all modern browsers and Node.js environments:
- All modern browsers (Chrome, Firefox, Safari, Edge)
- Internet Explorer 8+
- Node.js (all versions)

---
