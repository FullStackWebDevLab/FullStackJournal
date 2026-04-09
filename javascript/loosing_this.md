# Loosing `this`

In JavaScript, `this` is determined by **how a function is called**, not where it's defined. When you pass a method as a callback, you're passing the function reference without its original object context.

```javascript
class Player {
  constructor(name) {
    this.name = name;
    this.health = 100;
  }
  
  takeDamage(amount) {
    this.health -= amount;
    console.log(`${this.name} took ${amount} damage! Health: ${this.health}`);
  }
}

const player = new Player("Gandalf");

// ✅ Works - called directly on the object
player.takeDamage(10); // "Gandalf took 10 damage! Health: 90"

// ❌ Loses 'this' - function reference passed without context
setTimeout(player.takeDamage, 1000); // TypeError or undefined name!

// Why? setTimeout receives just the function:
const detachedFunction = player.takeDamage;
detachedFunction(10); // 'this' is now global or undefined
```

JavaScript functions are **first-class objects** - they can be passed around like any other value. When you pass `player.takeDamage`, you're passing the function itself, not the function bound to `player`.

```javascript
// What you THINK is happening:
setTimeout(player.takeDamage, 1000); // "Keep 'player' as 'this'"

// What's ACTUALLY happening:
const fn = player.takeDamage; // Just the function, 'player' is forgotten
setTimeout(fn, 1000); // 'this' is now whatever setTimeout decides
```

---

## Other Examples

### 1. **Event Listeners**
```javascript
class Button {
  constructor() {
    this.clicks = 0;
  }
  
  handleClick() {
    this.clicks++;
    console.log(this.clicks);
  }
}

const btn = new Button();
document.getElementById('myBtn').addEventListener('click', btn.handleClick);
// 'this' inside handleClick is the DOM element, not the Button instance!
```

### 2. **setTimeout / setInterval**
```javascript
class Timer {
  constructor() {
    this.count = 0;
  }
  
  increment() {
    this.count++;
  }
}

const timer = new Timer();
setInterval(timer.increment, 1000); // 'this' is lost!
```

### 3. **Promises and Async Callbacks**
```javascript
class DataFetcher {
  constructor() {
    this.data = null;
  }
  
  processData() {
    console.log(this.data); // 'this' might be lost here
  }
  
  fetch() {
    fetch('/api/data')
      .then(response => response.json())
      .then(this.processData); // 'this' is lost!
  }
}
```

### 4. **Array Methods with Callbacks**
```javascript
class Calculator {
  constructor() {
    this.multiplier = 2;
  }
  
  double(x) {
    return x * this.multiplier; // 'this' lost if used as callback
  }
}

const calc = new Calculator();
[1, 2, 3].map(calc.double); // NaN or error - 'this.multiplier' is undefined
```

---

## How to Prevent Losing `this`

### Solution 1: Arrow Functions (Most Common)

Arrow functions don't have their own `this` - they inherit it from the surrounding scope.

```javascript
class Game {
  constructor() {
    this.score = 0;
  }
  
  start() {
    // ✅ Arrow function preserves parent's 'this'
    setInterval(() => {
      this.score++;
      console.log(this.score);
    }, 1000);
    
    // ✅ Arrow function in event listener
    button.addEventListener('click', () => {
      this.handleClick();
    });
  }
  
  handleClick() {
    console.log('Button clicked!');
  }
}
```

### Solution 2: `.bind()` Method

Creates a new function with `this` permanently bound to a specific value.

```javascript
class Logger {
  constructor() {
    this.logs = [];
  }
  
  addLog(message) {
    this.logs.push(message);
    console.log(message);
  }
  
  setup() {
    // ✅ Bind the method once
    const boundAddLog = this.addLog.bind(this);
    setInterval(boundAddLog, 1000, "Tick");
    
    // ✅ Bind inline
    setTimeout(this.addLog.bind(this), 2000, "Delayed");
    
    // ✅ Bind in event listener
    button.addEventListener('click', this.addLog.bind(this));
  }
}
```

### Solution 3: Class Fields with Arrow Functions (Modern)

Define methods as arrow function properties in the class.

```javascript
class ModernGame {
  score = 0;
  
  // ✅ Arrow function property - automatically bound
  increment = () => {
    this.score++;
    console.log(this.score);
  }
  
  start() {
    // No binding needed - already bound to instance!
    setInterval(this.increment, 1000);
    button.addEventListener('click', this.increment);
  }
}
```

**Note:** This creates a new function per instance, which uses more memory than prototype methods.

### Solution 4: Store `this` in a Variable (Classic Pattern)

```javascript
class OldSchool {
  constructor() {
    this.count = 0;
    const self = this; // Store reference
    
    setInterval(function() {
      self.count++; // Use stored reference
      console.log(self.count);
    }, 1000);
  }
}
```

### Solution 5: Wrapper Functions

```javascript
class Wrapper {
  constructor() {
    this.value = 42;
  }
  
  showValue() {
    console.log(this.value);
  }
  
  start() {
    // ✅ Wrap in another function that preserves 'this'
    setTimeout(() => {
      this.showValue();
    }, 1000);
    
    // Or using .call/.apply
    setTimeout(() => {
      this.showValue.call(this);
    }, 1000);
  }
}
```

---
