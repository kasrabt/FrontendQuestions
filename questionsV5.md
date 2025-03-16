# JavaScript Core Concepts with Examples

## 1. Closures
A closure is a function that retains access to its lexical scope even when the function is executed outside that scope.

```js
function outerFunction(outerVariable) {
    return function innerFunction(innerVariable) {
        console.log(`Outer: ${outerVariable}, Inner: ${innerVariable}`);
    };
}
const newFunction = outerFunction('Hello');
newFunction('World'); // Outer: Hello, Inner: World
```

---

## 2. Event Loop and Asynchronous JavaScript
The event loop handles asynchronous operations in JavaScript by using the call stack, Web APIs, and task queue.

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

---

## 3. Hoisting
Hoisting moves function and variable declarations to the top of their scope before execution.

```js
console.log(a); // undefined
var a = 5;
hoistedFunction(); // Works!
function hoistedFunction() {
    console.log('Hoisted!');
}
```

---

## 4. Scope and Lexical Scope
Scope determines variable accessibility; lexical scope refers to accessing variables from outer scopes.

```js
function outer() {
    let outerVar = 'I am outer';
    function inner() {
        console.log(outerVar); // Accessible
    }
    inner();
}
outer();
```

---

## 5. `this` Keyword
The `this` keyword refers to different objects depending on the execution context.

```js
const obj = {
    name: 'JS',
    showName() {
        console.log(this.name);
    }
};
obj.showName(); // JS
```

---

## 6. Prototypal Inheritance
Objects inherit properties and methods from a prototype.

```js
function Animal(name) {
    this.name = name;
}
Animal.prototype.speak = function() {
    console.log(`${this.name} makes a noise.`);
};
const dog = new Animal('Dog');
dog.speak(); // Dog makes a noise.
```

---

## 7. Callbacks, Promises, and Async/Await

**Callbacks:**
```js
function fetchData(callback) {
    setTimeout(() => callback('Data received'), 1000);
}
fetchData(console.log);
```

**Promises:**
```js
const promise = new Promise((resolve) => setTimeout(() => resolve('Data received'), 1000));
promise.then(console.log);
```

**Async/Await:**
```js
async function fetchAsyncData() {
    let data = await promise;
    console.log(data);
}
fetchAsyncData();
```

---

## 8. JavaScript Engines and Optimization
JavaScript engines (like V8) optimize code using techniques like Just-In-Time (JIT) compilation and hidden classes.

---

## 9. Destructuring
Extract values from arrays or objects easily.

```js
const [a, b] = [1, 2];
const { name } = { name: 'JS' };
console.log(a, b, name);
```

---

## 10. Higher-Order Functions
Functions that accept or return other functions.

```js
function multiplyBy(factor) {
    return num => num * factor;
}
const double = multiplyBy(2);
console.log(double(5)); // 10
```

---

## 11. `bind()`, `call()`, and `apply()`

```js
const person = { name: 'John' };
function greet() {
    console.log(`Hello, ${this.name}`);
}
greet.call(person);
greet.apply(person);
const boundGreet = greet.bind(person);
boundGreet();
```

---

## 12. Modules and Imports/Exports

**module.js**
```js
export function greet() {
    console.log('Hello');
}
```

**main.js**
```js
import { greet } from './module.js';
greet();
```

---

## 13. Error Handling (`try/catch`)

```js
try {
    throw new Error('Something went wrong');
} catch (error) {
    console.error(error.message);
}
```

---

## 14. Debouncing and Throttling

**Debounce:** Executes a function after a delay, resetting on repeated calls.
```js
function debounce(func, delay) {
    let timeout;
    return function() {
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(this, arguments), delay);
    };
}
```

**Throttle:** Executes at most once per interval.
```js
function throttle(func, interval) {
    let lastCall = 0;
    return function() {
        const now = Date.now();
        if (now - lastCall >= interval) {
            lastCall = now;
            func.apply(this, arguments);
        }
    };
}
```

---

## 15. DOM Manipulation

```js
document.querySelector('#btn').addEventListener('click', () => {
    document.body.style.backgroundColor = 'blue';
});
```

---

## 16. Object-Oriented Programming (OOP) Principles in JS

```js
class Animal {
    constructor(name) {
        this.name = name;
    }
    speak() {
        console.log(`${this.name} makes a noise.`);
    }
}
class Dog extends Animal {
    speak() {
        console.log(`${this.name} barks.`);
    }
}
const dog = new Dog('Buddy');
dog.speak(); // Buddy barks.
```



