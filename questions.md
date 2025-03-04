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

# Advanced JavaScript and Web Development Concepts

## 1. What is PWA and Service Worker? How to Handle Caching?

**PWA (Progressive Web App)** is a web application that provides a native-like experience, including offline support, push notifications, and better performance.

**Service Worker** is a script that runs in the background, separate from the main browser thread, enabling caching, push notifications, and background sync.

### Example Caching Strategy:
```js
self.addEventListener('install', (event) => {
    event.waitUntil(
        caches.open('my-cache').then((cache) => {
            return cache.addAll(['/index.html', '/styles.css', '/script.js']);
        })
    );
});
```

---
## 2. Handling Icons in React for Better Performance
Using `<symbol>` and `<use>` with SVG sprites is an optimal way to handle icons in React.

### Example:
```xml
<svg style="display: none;">
    <symbol id="icon-star" viewBox="0 0 24 24">
        <path d="..." />
    </symbol>
</svg>
```
```jsx
<svg>
    <use href="#icon-star" />
</svg>
```

---
## 3. Difference Between `align-items` and `align-content`
- **`align-items`**: Aligns items inside a flex container along the cross-axis.
- **`align-content`**: Aligns multiple rows inside a flex container.

### Example:
```css
display: flex;
align-items: center; /* Aligns items in a single row */
align-content: space-between; /* Distributes space between multiple rows */
```

---
## 4. CSS `position` Values and Their Meaning

| Value       | Description |
|------------|-------------|
| `static`   | Default position |
| `relative` | Positioned relative to itself |
| `absolute` | Positioned relative to the nearest positioned ancestor |
| `fixed`    | Positioned relative to the viewport |
| `sticky`   | Switches between `relative` and `fixed` |

### Example:
```css
.fixed-box {
    position: fixed;
    top: 0;
}
```

---
## 5. Behavior of Identical Class Names in SASS Modules
Each class name gets a unique hash in CSS Modules, preventing conflicts.

### Example:
```scss
// styles.module.scss
.button {
    background: blue;
}
```
```js
import styles from './styles.module.scss';
console.log(styles.button); // Example output: styles_button__1a2b3c
```

---
## 6. Primitive vs Non-Primitive Data Types

| Type       | Example |
|------------|---------|
| Primitive  | `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint` |
| Non-Primitive | `object`, `array`, `function` |

### Example:
```js
let x = 5; // Primitive
let obj = { name: "John" }; // Non-Primitive
```

---
## 7. Immutable vs Mutable Values
- **Immutable**: Cannot be changed (e.g., `string`, `number`)
- **Mutable**: Can be changed (e.g., `object`, `array`)

### Example:
```js
const arr = [1, 2, 3];
arr.push(4); // Mutable change
```

---
## 8. Memoization Implementation
```js
function memoize(fn) {
    let cache = {};
    return function (...args) {
        let key = JSON.stringify(args);
        if (!cache[key]) {
            cache[key] = fn(...args);
        }
        return cache[key];
    };
}
```

---
## 9. Closure Explanation
A closure is a function that retains access to its outer function's variables.

### Example:
```js
function outer(x) {
    return function inner(y) {
        return x + y;
    };
}
const add5 = outer(5);
console.log(add5(3)); // 8
```

---
## 10. Implementing `map` in TypeScript
```ts
function customMap<T, U>(arr: T[], callback: (value: T) => U): U[] {
    let result: U[] = [];
    for (let item of arr) {
        result.push(callback(item));
    }
    return result;
}
```

---
## 11. Limiting Records in Sentry
```js
Sentry.init({
    maxBreadcrumbs: 50 // Limit to 50 logs
});
```

---
## 12-13. `useState` with `const` vs `let`
React ensures state updates via the setter function (`setState`), so `const` works.

### Example:
```js
const [count, setCount] = useState(0);
setCount(count + 1); // Works even though count is const
```

---
## 14. Merge vs Rebase in Git
- **Merge**: Combines branches with a new commit.
- **Rebase**: Moves commits from one branch to another, keeping history linear.

---
## 15. Server Components vs SSR
Server Components allow rendering on the server without sending extra JavaScript to the client, improving performance.

---
## 16. Docker Explanation
Docker helps create lightweight, portable containers.

```Dockerfile
FROM node:14
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "server.js"]
```

---
## 17. LocalStorage vs SessionStorage vs Cookies
| Storage   | Scope  | Expiry |
|-----------|--------|--------|
| LocalStorage | Permanent | Until manually cleared |
| SessionStorage | Per session | Cleared on tab close |
| Cookies | Server-client | Set expiration |

---
## 18. Virtual List for Performance Optimization
```js
import { FixedSizeList } from 'react-window';
const Row = ({ index, style }) => <div style={style}>Row {index}</div>;
<FixedSizeList height={500} width={300} itemSize={30} itemCount={1000}>{Row}</FixedSizeList>;
```

---
## 19. Reverse Words in a String
```js
function reverseWords(str) {
    return str.split(' ').map(word => word.split('').reverse().join('')).join(' ');
}
console.log(reverseWords("hello ali this is class"));
```

---
## 20. Heap vs Stack Memory
- **Stack**: Used for primitive values and function calls.
- **Heap**: Used for objects and complex data.

### Example:
```js
let x = 10; // Stack
let obj = { name: "John" }; // Heap
```

---
## 21. Factorial Calculation
```js
function factorial(n) {
    return n <= 1 ? 1 : n * factorial(n - 1);
}
console.log(factorial(4)); // 24
```



# Advanced React Concepts

## 1. Advanced State Management

### Redux & Redux Toolkit
Redux is a state management library that helps manage global state in a predictable manner. Redux Toolkit simplifies Redux by providing best practices.

```js
import { configureStore, createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: {
    increment: (state) => { state.value += 1; },
    decrement: (state) => { state.value -= 1; }
  }
});

export const { increment, decrement } = counterSlice.actions;
export const store = configureStore({ reducer: { counter: counterSlice.reducer } });
```

### Context API
A built-in React feature to manage state globally.

```js
const ThemeContext = createContext('light');

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}
```

### Zustand
A minimalistic state management library.

```js
import create from 'zustand';

const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 }))
}));
```

---

## 2. React Performance Optimization

### Memoization
Optimizing renders with `React.memo`, `useMemo`, and `useCallback`.

```js
const MemoizedComponent = React.memo(({ value }) => <p>{value}</p>);
```

### Code Splitting
Lazy load components.

```js
const LazyComponent = React.lazy(() => import('./LazyComponent'));
```

---

## 3. Component Design Patterns

### Higher-Order Components (HOCs)
Encapsulating logic by wrapping components.

```js
function withLogging(WrappedComponent) {
  return function (props) {
    console.log('Component rendered');
    return <WrappedComponent {...props} />;
  };
}
```

### Custom Hooks
Reusable logic abstraction.

```js
function useCounter() {
  const [count, setCount] = useState(0);
  return { count, increment: () => setCount(count + 1) };
}
```

---

## 4. Server-Side Rendering (SSR)

### Next.js Example

```js
export async function getServerSideProps() {
  const res = await fetch('https://api.example.com/data');
  const data = await res.json();
  return { props: { data } };
}
```

---

## 5. TypeScript with React

### Type Safety Example

```tsx
type ButtonProps = { label: string; };
const Button: React.FC<ButtonProps> = ({ label }) => <button>{label}</button>;
```

---

## 6. Testing

### React Testing Library

```js
test('renders component', () => {
  render(<Component />);
  expect(screen.getByText(/hello/i)).toBeInTheDocument();
});
```

### Cypress

```js
describe('My Test', () => {
  it('should load the page', () => {
    cy.visit('/');
  });
});
```

---

## 7. React Ecosystem and Tooling

### ESLint & Prettier

```json
{
  "extends": ["eslint:recommended", "plugin:react/recommended"]
}
```

---

## 8. API Integration

### GraphQL Example

```js
const { data } = useQuery(gql`{ users { name } }`);
```

### WebSockets

```js
const socket = new WebSocket('wss://example.com/socket');
socket.onmessage = (event) => console.log(event.data);
```

---

## 9. Authentication and Authorization

### JWT Authentication

```js
const token = localStorage.getItem('token');
fetch('/protected', { headers: { Authorization: `Bearer ${token}` } });
```

---

## 10. Code Architecture

### Monorepos (Nx, Lerna)

```sh
npx create-nx-workspace myworkspace
```

---

## 11. Web Performance Optimization

### Lazy Loading

```js
<img loading="lazy" src="image.jpg" alt="Lazy loaded" />
```

### PWA Example

```json
{
  "name": "My PWA",
  "short_name": "PWA",
  "start_url": "/"
}
```

