# Basic CSS Concepts

## 1. Class and Other Selectors
CSS selectors are used to target HTML elements for styling.

### Example:
```css
/* Class Selector */
.my-class {
  color: blue;
}

/* ID Selector */
#my-id {
  font-size: 20px;
}

/* Attribute Selector */
input[type="text"] {
  border: 1px solid black;
}
```

---
## 2. Pseudo Classes
Pseudo-classes define a special state of an element.

### Example:
```css
/* Change color on hover */
a:hover {
  color: red;
}

/* Style first child */
p:first-child {
  font-weight: bold;
}
```

---
## 3. Box Model
The CSS box model consists of margins, borders, padding, and content.

### Example:
```css
div {
  width: 200px;
  padding: 10px;
  border: 5px solid black;
  margin: 20px;
}
```

---
## 4. Pseudo Elements
Pseudo-elements style specific parts of an element.

### Example:
```css
p::first-letter {
  font-size: 24px;
  color: red;
}

p::before {
  content: "★ ";
  color: gold;
}
```

---
## 5. CSS Layout Types: Flex, Grid, Normal
CSS offers different layout systems.

### Example (Flexbox):
```css
div {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

### Example (Grid):
```css
div {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}
```

---
## 6. How to Center Elements

### Example (Flexbox):
```css
div {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

### Example (Grid):
```css
div {
  display: grid;
  place-items: center;
  height: 100vh;
}
```

---
## 7. Pseudo Classes and Elements
Pseudo-classes modify element states, and pseudo-elements style parts of elements.

### Example:
```css
a:visited {
  color: purple;
}

p::after {
  content: " ✔";
  color: green;
}
```

---
## 8. All Element States: Active, Hover, Focus, etc.
CSS allows styling different element states.

### Example:
```css
button:active {
  background-color: red;
}

input:focus {
  border: 2px solid blue;
}
```

---
## 9. Media Queries
Used to create responsive designs.

### Example:
```css
@media (max-width: 600px) {
  body {
    background-color: lightgray;
  }
}
```

---
## 10. Pre-processors: SCSS or LESS
CSS preprocessors extend CSS with features like variables and nesting.

### Example (SCSS):
```scss
$primary-color: blue;

h1 {
  color: $primary-color;
}
```

---
## 11. Mixins
Mixins allow reusable styles in SCSS.

### Example:
```scss
@mixin button-style {
  padding: 10px;
  border-radius: 5px;
  background-color: blue;
  color: white;
}

button {
  @include button-style;
}
```

---
## 12. CSS Constants
CSS custom properties (variables) make styles reusable.

### Example:
```css
:root {
  --main-color: blue;
}

div {
  color: var(--main-color);
}
```

---
## 13. BEM (Block, Element, Modifier)
BEM is a naming convention for CSS classes.

### Example:
```css
.button--primary {
  background-color: blue;
}

.button--secondary {
  background-color: gray;
}
```

---
## 14. Importing CSS
CSS files can be imported into stylesheets or JavaScript files.

### Example:
```css
@import url("styles.css");
```

OR in JavaScript (React):
```js
import "./styles.css";
```



# Basic JavaScript Concepts

## 1. Data Types
JavaScript has several data types, including:
- **Primitive Types**: `string`, `number`, `boolean`, `null`, `undefined`, `bigint`, `symbol`
- **Reference Types**: `object`, `array`, `function`

Example:
```js
let name = "John"; // string
let age = 25; // number
let isStudent = false; // boolean
let hobbies = ["reading", "coding"]; // array (object)
```

## 2. Functions
Functions are reusable blocks of code.

Example:
```js
function greet(name) {
  return `Hello, ${name}!`;
}
console.log(greet("Alice"));
```

## 3. Scope in JavaScript
JavaScript has three types of scope:
- **Global Scope**: Variables declared outside any function.
- **Local Scope**: Variables declared inside a function.
- **Block Scope** (introduced in ES6): Variables declared with `let` or `const` inside `{}`.

Example:
```js
let globalVar = "I am global";
function testScope() {
  let localVar = "I am local";
  console.log(globalVar);
}
console.log(localVar); // Error: localVar is not defined
```

## 4. Closure
A closure is a function that remembers the scope in which it was created.

Example:
```js
function outer() {
  let count = 0;
  return function inner() {
    count++;
    console.log(count);
  };
}
const counter = outer();
counter(); // 1
counter(); // 2
```

## 5. Event Loop
The event loop handles asynchronous operations in JavaScript.

Example:
```js
console.log("Start");
setTimeout(() => console.log("Async task"), 0);
console.log("End");
```
Output:
```
Start
End
Async task
```

## 6. Prototype and Prototype Chain
JavaScript uses prototypal inheritance.

Example:
```js
function Person(name) {
  this.name = name;
}
Person.prototype.greet = function() {
  console.log(`Hello, I am ${this.name}`);
};
const person1 = new Person("Alice");
person1.greet();
```

## 7. Class and Inheritance
ES6 introduced classes in JavaScript.

Example:
```js
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}
class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}
const dog = new Dog("Rex");
dog.speak();
```

## 8. DOM
The Document Object Model (DOM) represents the HTML document.

Example:
```js
document.getElementById("demo").innerText = "Hello, World!";
```

## 9. bind/call/apply
These methods control `this` in JavaScript.

Example:
```js
const obj = { name: "Alice" };
function greet() {
  console.log(`Hello, ${this.name}`);
}
greet.call(obj); // Hello, Alice
```

## 10. Promise
Promises handle asynchronous operations.

Example:
```js
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success!"), 2000);
});
myPromise.then(console.log);
```

## 11. WebAPI
Web APIs provide browser functionalities like `fetch` and `localStorage`.

Example:
```js
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then(response => response.json())
  .then(data => console.log(data));
```

## 12. Task Queue
Tasks in JavaScript are managed in queues.

Example:
```js
console.log("Start");
setTimeout(() => console.log("Timeout"), 0);
Promise.resolve().then(() => console.log("Promise"));
console.log("End");
```
Output:
```
Start
End
Promise
Timeout
```

## 13. Call Stack
The call stack maintains function execution order.

Example:
```js
function first() {
  console.log("First");
  second();
}
function second() {
  console.log("Second");
}
first();
```

## 14. Async/Await
Async/Await simplifies promises.

Example:
```js
async function fetchData() {
  let response = await fetch("https://jsonplaceholder.typicode.com/todos/1");
  let data = await response.json();
  console.log(data);
}
fetchData();
```

## 15. Generators
Generators allow pausing function execution.

Example:
```js
function* generatorFunction() {
  yield 1;
  yield 2;
  yield 3;
}
const gen = generatorFunction();
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
```

## 16. TypeScript
TypeScript is a superset of JavaScript with static types.

Example:
```ts
function add(a: number, b: number): number {
  return a + b;
}
console.log(add(2, 3));
```


# Basic Web Concepts

## 1. Page Rendering Cycle
The page rendering cycle involves the steps a browser takes to display a webpage:
- Browser requests an HTML document from the server.
- Parses HTML and constructs the DOM (Document Object Model).
- Parses CSS and applies styles.
- Executes JavaScript.
- Paints content to the screen.

### Example:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Rendering Example</title>
    <style>
        body { background-color: lightblue; }
    </style>
</head>
<body>
    <h1>Hello, World!</h1>
    <script>
        console.log('Page Loaded');
    </script>
</body>
</html>
```

## 2. HTTP/HTTPS/HTTP2
- **HTTP**: Standard protocol for communication between browsers and servers.
- **HTTPS**: Secure version of HTTP using SSL/TLS encryption.
- **HTTP/2**: Faster, allows multiplexing multiple requests over a single connection.

### Example:
```bash
curl -I https://example.com
```

## 3. CORS (Cross-Origin Resource Sharing)
Mechanism that allows restricted resources on a web page to be requested from another domain.

### Example:
```js
fetch('https://api.example.com/data', {
    mode: 'cors'
})
.then(response => response.json())
.then(data => console.log(data));
```

## 4. Local Storage / Session Storage
- **Local Storage**: Stores data persistently in the browser.
- **Session Storage**: Stores data for a single session (deleted after closing the tab).

### Example:
```js
localStorage.setItem('key', 'value');
console.log(localStorage.getItem('key'));
```

## 5. Cookies
Used to store small pieces of data on the client side.

### Example:
```js
document.cookie = "username=JohnDoe; expires=Fri, 31 Dec 2024 23:59:59 GMT";
```

## 6. JWT (JSON Web Token)
Secure way to transmit data between parties.

### Example:
```js
const token = "eyJhbGciOiJI...";
const payload = JSON.parse(atob(token.split('.')[1]));
console.log(payload);
```

## 7. XHR (XMLHttpRequest)
Old way to make HTTP requests before `fetch` was introduced.

### Example:
```js
var xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data", true);
xhr.onreadystatechange = function () {
    if (xhr.readyState == 4 && xhr.status == 200) {
        console.log(xhr.responseText);
    }
};
xhr.send();
```

## 8. Micro Frontend
Architecture pattern where a web app is divided into smaller independent frontend modules.

## 9. REST / GraphQL / Socket Connection
- **REST**: Standard API architecture.
- **GraphQL**: Query language for APIs.
- **Socket Connection**: Real-time bi-directional communication.

### Example (WebSocket):
```js
const socket = new WebSocket('ws://example.com/socket');
socket.onmessage = event => console.log(event.data);
```

## 10. Browser Concepts
Covers event loop, rendering optimization, and browser internals.

## 11. Debugging Application
Using breakpoints, console logs, and network monitoring.

## 12. Chrome DevTool Features
Includes Elements, Console, Network, Performance, Memory, and Application panels.

---
This guide covers the fundamentals of web development concepts.




# Advanced JavaScript Concepts

## 1. Object-Oriented Programming (OOP) in JavaScript
JavaScript supports Object-Oriented Programming (OOP) using prototypes and ES6 classes. The core principles of OOP include:

- **Encapsulation**: Wrapping data and methods into a single unit (class/object).
- **Abstraction**: Hiding complex logic and exposing only essential parts.
- **Inheritance**: Allowing objects to inherit properties/methods from another object.
- **Polymorphism**: Enabling objects to be treated as instances of a parent class.

Example:
```javascript
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

const dog = new Dog('Rex');
dog.speak(); // Rex barks.
```

## 2. Design Patterns
### a. Singleton Pattern
Ensures a class has only one instance and provides a global point of access.

Example:
```javascript
class Singleton {
    constructor() {
        if (!Singleton.instance) {
            Singleton.instance = this;
        }
        return Singleton.instance;
    }
}

const instance1 = new Singleton();
const instance2 = new Singleton();
console.log(instance1 === instance2); // true
```

### b. Provider Pattern
Used to provide a shared resource to multiple parts of an application, commonly seen in frameworks like React.

Example:
```javascript
const ConfigProvider = {
    config: {
        apiUrl: "https://api.example.com",
        theme: "dark"
    }
};

function getConfig() {
    return ConfigProvider.config;
}
```

### c. Prototype Pattern
Uses JavaScript's prototype mechanism to share properties among objects.

Example:
```javascript
function Person(name) {
    this.name = name;
}
Person.prototype.greet = function () {
    console.log(`Hello, my name is ${this.name}`);
};

const person1 = new Person("Alice");
person1.greet(); // Hello, my name is Alice
```

### d. Observer Pattern
Allows objects to subscribe to events and be notified of changes.

Example:
```javascript
class Subject {
    constructor() {
        this.observers = [];
    }
    subscribe(observer) {
        this.observers.push(observer);
    }
    notify(data) {
        this.observers.forEach(observer => observer.update(data));
    }
}

class Observer {
    update(data) {
        console.log("Received update:", data);
    }
}

const subject = new Subject();
const observer1 = new Observer();
subject.subscribe(observer1);
subject.notify("New Data");
```

### e. Module Pattern
Encapsulates code into reusable, self-contained modules.

Example:
```javascript
const MyModule = (function() {
    let privateVariable = "I am private";
    function privateMethod() {
        console.log(privateVariable);
    }
    return {
        publicMethod: function() {
            privateMethod();
        }
    };
})();

MyModule.publicMethod(); // I am private
```

### f. Higher-Order Component (HOC) Pattern (React Specific)
A function that takes a component and returns an enhanced version of it.

Example:
```javascript
const withLogger = (Component) => {
    return (props) => {
        console.log("Rendering Component with props:", props);
        return <Component {...props} />;
    };
};

const MyComponent = ({ name }) => <h1>Hello, {name}</h1>;
const EnhancedComponent = withLogger(MyComponent);
// <EnhancedComponent name="John" /> will log props before rendering
```

# Understanding V8 in Depth

## 1. Just-In-Time (JIT) Compilation
JIT compilation is a technique used by V8 to improve JavaScript execution speed. Instead of interpreting JavaScript line by line, V8 compiles it into machine code at runtime.

### Example:
```js
function add(a, b) {
    return a + b;
}
console.log(add(2, 3));
```
V8 optimizes functions like `add` by compiling them into efficient machine code, reducing execution time.

## 2. Interpreter
V8 includes an interpreter called `Ignition`, which quickly converts JavaScript code into bytecode before it is optimized.

### Example:
```js
function multiply(a, b) {
    return a * b;
}
console.log(multiply(2, 4));
```
`Ignition` interprets this code before handing it off to the optimizing compiler.

## 3. Execution
V8 executes JavaScript in multiple steps: parsing, interpreting, compiling, and optimizing.

### Steps:
1. Parsing: Converts JavaScript code into an Abstract Syntax Tree (AST).
2. Bytecode Generation: `Ignition` generates bytecode for execution.
3. Optimization: `TurboFan` optimizes frequently executed code.
4. Execution: The optimized code runs efficiently.

## 4. Compiler
V8 uses two compilers:
- `Ignition`: Converts JavaScript into bytecode.
- `TurboFan`: Optimizes and compiles hot code into machine code.

### Example:
```js
function square(n) {
    return n * n;
}
square(5);
```
Initially, `Ignition` interprets `square`, but if it's used frequently, `TurboFan` optimizes it.

# Currying
Currying is a functional programming technique where a function takes multiple arguments one at a time.

### Example:
```js
function currySum(a) {
    return function (b) {
        return function (c) {
            return a + b + c;
        };
    };
}
console.log(currySum(1)(2)(3)); // Output: 6
```
Here, `currySum` takes arguments one at a time, making it flexible for partial application.


This document provides a foundational understanding of these advanced JavaScript concepts with practical examples.



# Basic ReactJS Concepts

## 1. Introduction to JSX
JSX (JavaScript XML) allows writing HTML elements inside JavaScript and placing them in the DOM.
```jsx
const element = <h1>Hello, JSX!</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

## 2. React Component
Components are independent and reusable pieces of UI.
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

## 3. Component State and Props
State is a local storage in components, and props are used to pass data between components.
```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>Increment</button>
      </div>
    );
  }
}
```

## 4. Adding Style (CSS)
Styles can be added using external CSS files, inline styles, or CSS-in-JS libraries like styled-components.
```jsx
const buttonStyle = { backgroundColor: 'blue', color: 'white' };
<button style={buttonStyle}>Click me</button>
```

## 5. Functional and Class Components
Functional components are stateless before hooks, while class components support state.
```jsx
function Hello() { return <h1>Hello, World!</h1>; }
```
```jsx
class Hello extends React.Component {
  render() { return <h1>Hello, World!</h1>; }
}
```

## 6. React Lifecycle Methods
Class components have lifecycle methods like `componentDidMount` and `componentWillUnmount`.
```jsx
class Example extends React.Component {
  componentDidMount() { console.log("Component Mounted"); }
  componentWillUnmount() { console.log("Component Unmounted"); }
  render() { return <h1>Lifecycle Example</h1>; }
}
```

## 7. Virtual DOM
React uses a virtual DOM to improve performance by minimizing direct manipulations of the real DOM.

## 8. React Hooks
Hooks allow using state and other features in functional components.
```jsx
import { useState } from 'react';
function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>Count: {count}</button>;
}
```

## 9. Custom Hooks
Custom hooks reuse logic across components.
```jsx
function useCounter(initialValue) {
  const [count, setCount] = useState(initialValue);
  const increment = () => setCount(count + 1);
  return [count, increment];
}
```

## 10. Context API
Context provides a way to pass data through the component tree without props.
```jsx
const ThemeContext = React.createContext('light');
```

## 11. Synthetic Events
React normalizes browser events into synthetic events.
```jsx
function handleClick(event) {
  console.log(event.type);
}
<button onClick={handleClick}>Click Me</button>
```

## 12. Routing
React Router allows navigation between pages.
```jsx
import { BrowserRouter, Route, Switch } from 'react-router-dom';
```

## 13. Data Flow (Redux/Flux)
Redux is a state management library following a unidirectional data flow.
```jsx
const store = createStore(reducer);
```

## 14. Server-Side Rendering
React can render on the server using Next.js.

## 15. Unit Testing
Jest and React Testing Library are used for testing React components.

## 16. Jest & React Testing Library
Jest is a testing framework, and RTL is for component testing.
```jsx
test('renders learn react link', () => {
  render(<App />);
});
```

## 17. Mocking Data
Mock data is used for testing and development.
```jsx
const mockData = [{ id: 1, name: "John Doe" }];
```

## 18. Understanding Webpack (Bundler)
Webpack is a module bundler for managing dependencies.

## 19. Babel, env, prettier, linter
Babel transpiles modern JavaScript, `.env` manages environment variables, Prettier formats code, and linters enforce coding standards.
