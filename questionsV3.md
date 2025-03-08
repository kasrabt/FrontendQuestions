## HTML/CSS

### What is the box model in CSS?
The CSS box model describes the rectangular boxes that are generated for elements in the document tree. It consists of the following parts:
- **Content**: The actual content of the element (text, images, etc.).
- **Padding**: Space between the content and the border.
- **Border**: The surrounding border of the element.
- **Margin**: Space outside the border, separating the element from others.

Example:
```css
.box {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  margin: 10px;
}
```

### How do you implement responsive design?
Responsive design ensures a website looks good on all devices. Techniques include:
- **Media Queries**
- **Flexbox & Grid Layouts**
- **Relative Units (%, em, rem, vh, vw)**

Example:
```css
@media (max-width: 600px) {
  .container {
    flex-direction: column;
  }
}
```

### What is the difference between inline and block elements?
- **Inline elements**: Do not start on a new line, only take as much width as necessary. (e.g., `<span>`, `<a>`)
- **Block elements**: Start on a new line and take up full width. (e.g., `<div>`, `<p>`)

Example:
```html
<span>This is inline</span>
<div>This is block</div>
```

### How do you optimize images for web use?
- Use **proper formats** (WebP, JPEG, PNG, SVG)
- Compress images using tools like **TinyPNG**
- Implement **lazy loading**
- Use **responsive images**

Example:
```html
<img src="image.webp" loading="lazy" alt="Optimized image" />
```

## JavaScript

### What is the difference between null and undefined?
- **null**: Explicitly assigned to a variable to indicate “no value”.
- **undefined**: Automatically assigned when a variable is declared but not initialized.

Example:
```js
let x = null;
let y;
console.log(x); // null
console.log(y); // undefined
```

### What is the event loop?
The event loop is responsible for handling asynchronous operations in JavaScript. It continuously checks the call stack and callback queue.

Example:
```js
console.log('Start');
setTimeout(() => console.log('Timeout'), 0);
console.log('End');
```
Output:
```
Start
End
Timeout
```

### What is the difference between var, let, and const?
- `var`: Function-scoped, can be re-declared and updated.
- `let`: Block-scoped, can be updated but not re-declared.
- `const`: Block-scoped, cannot be updated or re-declared.

Example:
```js
var a = 10;
let b = 20;
const c = 30;
```

### What is the difference between `==` and `===`?
- `==` checks for value equality (performs type coercion).
- `===` checks for both value and type equality.

Example:
```js
console.log(5 == '5');  // true
console.log(5 === '5'); // false
```

### What is the difference between Promises and Async/Await?
- **Promises** use `.then()` and `.catch()`.
- **Async/Await** makes asynchronous code look synchronous.

Example:
```js
function fetchData() {
  return new Promise((resolve) => setTimeout(() => resolve('Data'), 1000));
}

async function getData() {
  const data = await fetchData();
  console.log(data);
}
getData();
```

## React

### What is the Virtual DOM and how does it work?
The Virtual DOM is a lightweight copy of the real DOM that React uses to optimize rendering.
- React updates the Virtual DOM first.
- It compares the updated Virtual DOM with the previous version (diffing).
- Only necessary changes are applied to the real DOM (reconciliation).

### How do you optimize the performance of a React application?
- Use **React.memo** to prevent unnecessary re-renders.
- Use **lazy loading** for components.
- Optimize **useEffect** dependencies.
- Implement **code splitting**.

Example:
```js
const MemoizedComponent = React.memo(MyComponent);
```

### What is the difference between state and props?
- **State**: Managed within a component (mutable).
- **Props**: Passed from parent to child (immutable).

Example:
```js
function Child({ name }) {
  return <h1>Hello, {name}!</h1>;
}
function Parent() {
  return <Child name="John" />;
}
```

### How do you handle side effects in React?
Use the `useEffect` hook.

Example:
```js
useEffect(() => {
  console.log('Component mounted');
  return () => console.log('Component unmounted');
}, []);
```

### What is the difference between a controlled and uncontrolled component?
- **Controlled**: The component's state is controlled by React.
- **Uncontrolled**: The state is handled by the DOM itself.

Example:
```js
// Controlled Component
function ControlledInput() {
  const [value, setValue] = useState('');
  return <input value={value} onChange={(e) => setValue(e.target.value)} />;
}
```
```js
// Uncontrolled Component
function UncontrolledInput() {
  const inputRef = useRef();
  return <input ref={inputRef} />;
}
```

# UI/UX

## What is user-centered design and how do you implement it?
User-centered design (UCD) is an iterative design process that focuses on users and their needs at each phase of the design process. It involves research, prototyping, testing, and iteration to ensure that the final product is intuitive and effective.

**Example:**
A company designing a fitness tracking app conducts user interviews to understand their exercise habits. They create wireframes, test them with potential users, and refine the design based on feedback.

---

## How do you conduct user research and testing?
User research involves gathering insights about users through methods such as interviews, surveys, and usability testing. Testing ensures that the design meets user needs and expectations.

**Example:**
A designer creating a shopping app uses A/B testing to compare two different checkout flows and determine which one leads to higher conversion rates.

---

## What is the difference between a wireframe and a prototype?
A wireframe is a low-fidelity representation of a layout, focusing on structure and content placement, while a prototype is a more interactive, high-fidelity version that simulates user interactions.

**Example:**
A wireframe may be a simple black-and-white sketch of a website, while a prototype may allow users to click on buttons to navigate between pages.

---

## How do you design for accessibility?
Designing for accessibility ensures that a product is usable by people with disabilities. This includes using proper contrast, keyboard navigability, alt text for images, and ARIA attributes.

**Example:**
A website for booking flights includes keyboard shortcuts and screen reader support to help visually impaired users complete bookings.

---

## What is the difference between a responsive and adaptive design?
Responsive design uses fluid grids and flexible layouts to adjust to different screen sizes, while adaptive design has predefined layouts that switch based on device type.

**Example:**
A news website using responsive design resizes text and images dynamically, while an adaptive design version might load a completely different layout for mobile and desktop.

---

# Frontend Build Tools

## What is Webpack and how does it work?
Webpack is a module bundler that compiles JavaScript files and assets into a single output bundle. It uses loaders to transform files and plugins to optimize builds.

**Example:**
A React project uses Webpack to bundle JavaScript files, transpile JSX using Babel, and optimize images.

---

## How do you optimize the build process for a frontend application?
Optimization techniques include minification, tree shaking, code splitting, and lazy loading to improve performance and load times.

**Example:**
A developer enables gzip compression and tree shaking in Webpack to reduce the JavaScript bundle size.

---

## What is the difference between a bundler and a transpiler?
A bundler combines multiple files into a single file, while a transpiler converts modern JavaScript code into an older version for compatibility.

**Example:**
Webpack (bundler) merges all modules into one file, while Babel (transpiler) converts ES6+ code into ES5.

---

## How do you implement tree shaking and code splitting?
Tree shaking removes unused code during the build process, and code splitting breaks the code into smaller chunks for lazy loading.

**Example:**
A React app uses Webpack's `splitChunks` plugin to load only the necessary JavaScript files per route.

---

## What is the difference between a dev and prod build?
A dev build is optimized for development with source maps and debugging tools, while a prod build is optimized for performance with minified code.

**Example:**
A Vue.js app in dev mode includes error messages, while the production build removes them to reduce file size.

---

# State Management

## What is state management and why is it important?
State management controls the state of an application, ensuring consistency and predictable behavior across components.

**Example:**
A shopping cart in an e-commerce app maintains state to track added items across different pages.

---

## How do you implement state management with Redux or MobX?
Redux uses a single store and actions to manage state, while MobX uses observables and decorators to automatically track state changes.

**Example:**
A to-do list app uses Redux to store tasks, dispatch actions to add/remove tasks, and update UI based on state changes.

---

## What is the difference between a store and a context?
A store (like Redux) is a centralized state container, while React context provides a lightweight way to pass state through components without prop drilling.

**Example:**
Redux manages global authentication state, while React Context shares theme settings across components.

---

## How do you handle side effects with state management?
Side effects like API calls are handled with middleware (e.g., Redux Thunk, Redux Saga) or effects in MobX.

**Example:**
A Redux Thunk function fetches user data from an API when a component mounts and updates the store.

---

## What is the difference between a reducer and an action?
A reducer updates state based on an action, while an action describes an event that triggers a state change.

**Example:**
An action `{ type: 'INCREMENT' }` tells the reducer to increase a counter state value.

---

# Frontend Security

## What is Cross-Site Scripting (XSS) and how do you prevent it?
Cross-Site Scripting (XSS) is a security vulnerability that allows attackers to inject malicious scripts into web pages viewed by users. These scripts can steal user data, hijack sessions, or perform actions on behalf of the user.

### Prevention:
- Use Content Security Policy (CSP) to restrict script execution.
- Escape user input before rendering it on the page.
- Use libraries like DOMPurify to sanitize input.
- Avoid `innerHTML` and use safe DOM manipulation methods.

### Example:
```javascript
const userInput = "<script>alert('XSS')</script>";
const sanitizedInput = DOMPurify.sanitize(userInput);
document.getElementById("output").innerHTML = sanitizedInput;
```

---

## How do you implement authentication and authorization?
Authentication verifies user identity, while authorization determines what actions a user is allowed to perform.

### Implementation:
- **Authentication:** Use JWT, OAuth, or session-based authentication.
- **Authorization:** Implement role-based access control (RBAC) or attribute-based access control (ABAC).

### Example:
```javascript
fetch('/api/protected-route', {
  method: 'GET',
  headers: { 'Authorization': `Bearer ${token}` }
})
  .then(response => response.json())
  .then(data => console.log(data));
```

---

## What is Cross-Site Request Forgery (CSRF) and how do you prevent it?
CSRF is an attack where an unauthorized request is sent from an authenticated user to a web application.

### Prevention:
- Use CSRF tokens for state-changing requests.
- Implement SameSite cookies.
- Require user re-authentication for critical actions.

### Example:
```javascript
fetch('/api/update-profile', {
  method: 'POST',
  headers: { 'X-CSRF-Token': csrfToken },
  body: JSON.stringify({ name: 'John Doe' })
});
```

---

## How do you handle sensitive data in a frontend application?
- Never store sensitive data (e.g., passwords, API keys) in `localStorage`.
- Use HTTPS to encrypt data in transit.
- Use environment variables for API keys in build-time configurations.

---

## What is the difference between HTTPS and HTTP?
- **HTTP:** Data is transmitted in plaintext, making it vulnerable to interception.
- **HTTPS:** Uses SSL/TLS encryption to secure data transfer.

---

# Browser APIs

## What is the difference between `localStorage` and `sessionStorage`?
- `localStorage`: Data persists even after closing the browser.
- `sessionStorage`: Data is cleared when the session ends.

---

## How do you implement geolocation and push notifications?
### Geolocation Example:
```javascript
navigator.geolocation.getCurrentPosition(position => {
  console.log(position.coords.latitude, position.coords.longitude);
});
```
### Push Notification Example:
```javascript
Notification.requestPermission().then(permission => {
  if (permission === 'granted') {
    new Notification('Hello, world!');
  }
});
```

---

## What is the difference between a cookie and a token?
- **Cookie:** Stored by the browser and automatically sent with requests.
- **Token:** Manually sent with API requests, often used in JWT authentication.

---

## How do you handle browser storage and caching?
- Use `localStorage` for persistent, non-sensitive data.
- Use HTTP cache headers (`Cache-Control`, `ETag`) to control caching.

---

## What is the difference between a Web Worker and a Service Worker?
- **Web Worker:** Runs scripts in the background without affecting the UI.
- **Service Worker:** Acts as a proxy between the browser and network, enabling offline functionality.

---

# Frontend Frameworks

## What is the difference between Angular, React, and Vue?
| Feature  | Angular | React | Vue |
|----------|--------|-------|-----|
| Type | Full framework | Library | Framework |
| Language | TypeScript | JavaScript/JSX | JavaScript |
| Architecture | MVC | Component-based | Component-based |

---

## What is the difference between a library and a framework?
- **Library:** A set of reusable functions/components (e.g., React).
- **Framework:** A structured system that dictates architecture (e.g., Angular).

---

## What is the difference between a template and a component?
- **Template:** Static structure for rendering UI.
- **Component:** Self-contained unit with logic, UI, and styles.

---

## Difference between Promises and Observables
- **Promise:** Handles a single asynchronous operation.
- **Observable:** Handles multiple values over time, supports reactive programming.

### Example:
```javascript
// Promise
const promise = new Promise(resolve => setTimeout(() => resolve('Done'), 1000));
promise.then(console.log);

// Observable (RxJS)
const observable = new Observable(subscriber => {
  subscriber.next('Value 1');
  setTimeout(() => subscriber.next('Value 2'), 1000);
});
observable.subscribe(console.log);
```

