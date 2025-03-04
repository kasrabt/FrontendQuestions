# JavaScript Core Concepts

## 1. Event Loop & Microtasks

The Event Loop is responsible for handling asynchronous operations in JavaScript. It continuously checks the call stack and task queue, ensuring non-blocking execution.

### Example:
```js
console.log('Start');
setTimeout(() => console.log('Timeout'), 0);
Promise.resolve().then(() => console.log('Promise'));
console.log('End');
```
**Output:**
```
Start
End
Promise
Timeout
```

## 2. Closures
A closure is a function that remembers the variables from its outer scope even after the outer function has executed.

### Example:
```js
function outerFunction(outerValue) {
    return function innerFunction(innerValue) {
        console.log(`Outer: ${outerValue}, Inner: ${innerValue}`);
    };
}
const closureFunc = outerFunction('Hello');
closureFunc('World');
```

## 3. Prototypal Inheritance
JavaScript objects inherit properties and methods from their prototype.

### Example:
```js
function Person(name) {
    this.name = name;
}
Person.prototype.greet = function() {
    console.log(`Hello, my name is ${this.name}`);
};
const person = new Person('John');
person.greet();
```

## 4. Execution Context & Call Stack
The execution context includes the variables, function calls, and scope chains during execution. The call stack maintains function calls in LIFO order.

### Example:
```js
function first() {
    second();
}
function second() {
    third();
}
function third() {
    console.log('Inside third function');
}
first();
```

## 5. Hoisting
Hoisting moves function and variable declarations to the top of their scope before execution.

### Example:
```js
console.log(myVar); // undefined
var myVar = 10;
hoistedFunction(); // Works
function hoistedFunction() {
    console.log('Hoisted!');
}
```

## 6. this Binding
`this` refers to the context in which a function is executed.

### Example:
```js
const obj = {
    name: 'John',
    greet: function() {
        console.log(this.name);
    }
};
obj.greet();
```

## 7. Currying
Currying transforms a function with multiple arguments into a sequence of nested functions.

### Example:
```js
const curry = (a) => (b) => (c) => a + b + c;
console.log(curry(1)(2)(3)); // 6
```

## 8. Memoization
Memoization stores results of expensive function calls to optimize performance.

### Example:
```js
function memoize(fn) {
    const cache = {};
    return function(...args) {
        const key = JSON.stringify(args);
        if (!cache[key]) {
            cache[key] = fn(...args);
        }
        return cache[key];
    };
}
const factorial = memoize((n) => (n <= 1 ? 1 : n * factorial(n - 1)));
console.log(factorial(5));
```

## 9. Debouncing & Throttling
- **Debouncing**: Limits the execution of a function until a certain time has passed.
- **Throttling**: Ensures a function executes at most once in a given time frame.

### Example (Debounce):
```js
function debounce(func, delay) {
    let timeout;
    return function(...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => func(...args), delay);
    };
}
```

### Example (Throttle):
```js
function throttle(func, limit) {
    let inThrottle;
    return function(...args) {
        if (!inThrottle) {
            func(...args);
            inThrottle = true;
            setTimeout(() => inThrottle = false, limit);
        }
    };
}
```

## 10. Private & Static Class Fields
Private fields are declared with `#`, while static fields belong to the class itself.

### Example:
```js
class Person {
    #privateField = 'Secret';
    static staticField = 'I am static';

    getPrivate() {
        return this.#privateField;
    }
}
const p = new Person();
console.log(p.getPrivate()); // Secret
console.log(Person.staticField); // I am static
```

## 11. Web Workers
Web Workers enable running scripts in background threads.

### Example:
```js
const worker = new Worker('worker.js');
worker.postMessage('Hello Worker');
worker.onmessage = (event) => console.log(event.data);
```

**worker.js**:
```js
onmessage = (event) => {
    postMessage(`Received: ${event.data}`);
};
```

## 12. Structured Clone Algorithm
Allows deep copying of objects that include complex types like `Map`, `Set`, `ArrayBuffer`, etc.

### Example:
```js
const obj = { name: 'John', data: new Set([1, 2, 3]) };
const cloned = structuredClone(obj);
console.log(cloned);
```

## 13. Type Coercion
JavaScript automatically converts types in certain operations.

### Example:
```js
console.log('5' + 3); // '53'
console.log('5' - 3); // 2
console.log(true + 1); // 2
```

