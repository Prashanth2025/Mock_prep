#  React Interview Prep (Detailed Answers: Topics 1–10)

---

### 1. Function-Based Component
**Interview Answer:**  
Function components are plain JavaScript functions that return JSX. They are lightweight, easier to read, and use **React Hooks** for state and lifecycle management. Preferred in modern React over class components.  

**Syntax & Example:**
```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Usage
<Greeting name="Prashanth" />
```

---

### 2. Class-Based Component
**Interview Answer:**  
Class components extend `React.Component`. They use `render()` to return JSX and manage state with `this.state`. Lifecycle methods (`componentDidMount`, `componentDidUpdate`, `componentWillUnmount`) are available.  

**Syntax & Example:**
```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>+</button>
      </div>
    );
  }
}
```

---

### 3. HMR (Hot Module Replacement)
**Interview Answer:**  
HMR updates modules in real-time without refreshing the page. It preserves state, making development faster. Enabled by default in **Create React App**.  

**Syntax & Example:**  
No explicit code needed in CRA.  
```bash
npm start   # CRA enables HMR automatically
```

---

### 4. CRA Tool (Create React App)
**Interview Answer:**  
CRA bootstraps React projects with Webpack, Babel, ESLint, and HMR preconfigured. It saves setup time.  

**Syntax & Example:**
```bash
npx create-react-app my-app
cd my-app
npm start
```

---

### 5. npm
**Interview Answer:**  
npm (Node Package Manager) installs and manages dependencies. It’s bundled with Node.js.  

**Syntax & Example:**
```bash
npm install react
npm install axios
```

---

### 6. npx
**Interview Answer:**  
npx executes npm packages without installing them globally. Useful for one-time commands like CRA.  

**Syntax & Example:**
```bash
npx create-react-app my-app
```

---

### 7. Minor/Major Change
**Interview Answer:**  
Semantic versioning:  
- **Major (X.0.0):** Breaking changes.  
- **Minor (0.X.0):** New features, backward compatible.  
- **Patch (0.0.X):** Bug fixes.  

**Example:**  
- `react@17.0.0 → 18.0.0` (Major)  
- `react@17.1.0 → 17.2.0` (Minor)  
- `react@17.1.1 → 17.1.2` (Patch)

---

### 8. Babel
**Interview Answer:**  
Babel transpiles modern JavaScript (ES6+) and JSX into browser-compatible JS. Without Babel, browsers can’t understand JSX.  

**Syntax & Example:**
```jsx
// JSX
const element = <h1>Hello World</h1>;

// Babel transpiles to:
React.createElement("h1", null, "Hello World");
```

---

### 9. Default Export
**Interview Answer:**  
Default export allows exporting a single value per file. Import without curly braces.  

**Syntax & Example:**
```jsx
// File: App.js
export default function App() {
  return <h1>Default Export Example</h1>;
}

// Import
import App from './App';
```

---

### 10. Named Export
**Interview Answer:**  
Named exports allow multiple exports per file. Import with curly braces.  

**Syntax & Example:**
```jsx
// File: Layout.js
export const Header = () => <h1>Header</h1>;
export const Footer = () => <h1>Footer</h1>;

// Import
import { Header, Footer } from './Layout';
```

---

Perfect — let’s reformat the **React Interview Prep (Topics 1–10)** into clean **Markdown (MD) format** so you can use it directly as notes or a study guide.  

---

# 📘 React Interview Prep (Topics 1–10)

---

## 1. Function-Based Component
**Interview Answer:**  
Function components are plain JavaScript functions that return JSX. They are lightweight, easier to read, and use **React Hooks** for state and lifecycle management. Preferred in modern React over class components.  

**Syntax & Example:**
```jsx
function Greeting(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Usage
<Greeting name="Prashanth" />
```

---

## 2. Class-Based Component
**Interview Answer:**  
Class components extend `React.Component`. They use `render()` to return JSX and manage state with `this.state`. Lifecycle methods (`componentDidMount`, `componentDidUpdate`, `componentWillUnmount`) are available.  

**Syntax & Example:**
```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  increment = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.increment}>+</button>
      </div>
    );
  }
}
```

---

## 3. HMR (Hot Module Replacement)
**Interview Answer:**  
HMR updates modules in real-time without refreshing the page. It preserves state, making development faster. Enabled by default in **Create React App**.  

**Syntax & Example:**  
```bash
npm start   # CRA enables HMR automatically
```

---

## 4. CRA Tool (Create React App)
**Interview Answer:**  
CRA bootstraps React projects with Webpack, Babel, ESLint, and HMR preconfigured. It saves setup time.  

**Syntax & Example:**
```bash
npx create-react-app my-app
cd my-app
npm start
```

---

## 5. npm
**Interview Answer:**  
npm (Node Package Manager) installs and manages dependencies. It’s bundled with Node.js.  

**Syntax & Example:**
```bash
npm install react
npm install axios
```

---

## 6. npx
**Interview Answer:**  
npx executes npm packages without installing them globally. Useful for one-time commands like CRA.  

**Syntax & Example:**
```bash
npx create-react-app my-app
```

---

## 7. Minor/Major Change
**Interview Answer:**  
Semantic versioning:  
- **Major (X.0.0):** Breaking changes.  
- **Minor (0.X.0):** New features, backward compatible.  
- **Patch (0.0.X):** Bug fixes.  

**Example:**  
- `react@17.0.0 → 18.0.0` (Major)  
- `react@17.1.0 → 17.2.0` (Minor)  
- `react@17.1.1 → 17.1.2` (Patch)

---

## 8. Babel
**Interview Answer:**  
Babel transpiles modern JavaScript (ES6+) and JSX into browser-compatible JS. Without Babel, browsers can’t understand JSX.  

**Syntax & Example:**
```jsx
// JSX
const element = <h1>Hello World</h1>;

// Babel transpiles to:
React.createElement("h1", null, "Hello World");
```

---

## 9. Default Export
**Interview Answer:**  
Default export allows exporting a single value per file. Import without curly braces.  

**Syntax & Example:**
```jsx
// File: App.js
export default function App() {
  return <h1>Default Export Example</h1>;
}

// Import
import App from './App';
```

---

## 10. Named Export
**Interview Answer:**  
Named exports allow multiple exports per file. Import with curly braces.  

**Syntax & Example:**
```jsx
// File: Layout.js
export const Header = () => <h1>Header</h1>;
export const Footer = () => <h1>Footer</h1>;

// Import
import { Header, Footer } from './Layout';
```

---

Great — let’s continue with the **next section (Topics 11–20)** in the same **Markdown (MD) format** with **detailed interview-style answers, syntax, and examples**.  

---

# 📘 React Interview Prep (Topics 11–20)

---

## 11. React Fragment
**Interview Answer:**  
React Fragment lets you group multiple elements without adding extra nodes to the DOM. Useful when returning multiple elements from a component.  

**Syntax & Example:**
```jsx
function Demo() {
  return (
    <>
      <h1>Title</h1>
      <p>Description</p>
    </>
  );
}
```

---

## 12. Structure of React App
**Interview Answer:**  
A typical React app created with CRA has:  
- `public/` → static files (index.html, images)  
- `src/` → components, App.js, index.js  
- `package.json` → dependencies  
- `node_modules/` → installed libraries  

**Example Structure:**
```
my-app/
  public/
    index.html
  src/
    App.js
    index.js
    components/
  package.json
```

---

## 13. React Expression
**Interview Answer:**  
React allows embedding JavaScript expressions inside JSX using `{}`. Expressions can be variables, functions, or calculations.  

**Syntax & Example:**
```jsx
function Demo() {
  const name = "Prashanth";
  return <h1>Hello, {name.toUpperCase()}</h1>;
}
```

---

## 14. JSX File
**Interview Answer:**  
JSX (JavaScript XML) is a syntax extension that lets you write HTML-like code inside JavaScript. Babel transpiles JSX into `React.createElement`.  

**Syntax & Example:**
```jsx
const element = <h1>Hello JSX</h1>;
```

---

## 15. Styling React Component
**Interview Answer:**  
React supports multiple styling approaches:  
- Inline styles  
- CSS files  
- CSS Modules  
- Styled-components  

**Syntax & Example:**
```jsx
// Inline
const style = { color: "blue", fontSize: "20px" };
function Demo() {
  return <h1 style={style}>Styled Text</h1>;
}

// External CSS
import "./App.css";
function Demo() {
  return <h1 className="heading">Styled Text</h1>;
}
```

---

## 16. Props
**Interview Answer:**  
Props (properties) are read-only inputs passed from parent to child components. They make components reusable.  

**Syntax & Example:**
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Usage
<Welcome name="Prashanth" />
```

---

## 17. Declarative Approach
**Interview Answer:**  
React uses a declarative approach: you describe **what** UI should look like, not **how** to update it. React handles DOM updates via Virtual DOM.  

**Example:**
```jsx
// Declarative
<button onClick={() => setCount(count + 1)}>+</button>

// Imperative (Vanilla JS)
document.getElementById("btn").addEventListener("click", () => count++);
```

---

## 18. React Event Handling
**Interview Answer:**  
React normalizes events across browsers. Events are written in camelCase and passed functions instead of strings.  

**Syntax & Example:**
```jsx
function Demo() {
  function handleClick() {
    alert("Button clicked!");
  }
  return <button onClick={handleClick}>Click Me</button>;
}
```

---

## 19. React Hooks
**Interview Answer:**  
Hooks let you use state and lifecycle features in function components. Common hooks:  
- `useState` → state management  
- `useEffect` → side effects  
- `useRef` → references  
- `useContext` → context  

**Syntax & Example:**
```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <button onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
```

---

## 20. State in React
**Interview Answer:**  
State is mutable data managed inside a component. Changing state triggers re-render.  
- In **class components**: `this.state` and `this.setState()`  
- In **function components**: `useState()`  

**Syntax & Example:**
```jsx
// Function Component
const [count, setCount] = useState(0);

// Class Component
this.state = { count: 0 };
this.setState({ count: this.state.count + 1 });
```

---

Perfect — let’s continue with the **next section (Topics 21–30)** in the same **Markdown (MD) format** with **detailed interview-style answers, syntax, and examples**.  

---

# 📘 React Interview Prep (Topics 21–30)

---

## 21. Image Handling in React
**Interview Answer:**  
Images in React can be handled in multiple ways:  
- Importing directly into components  
- Using `public/` folder for static assets  
- Using URLs for external images  

**Syntax & Example:**
```jsx
// Importing
import logo from './logo.png';

function Demo() {
  return <img src={logo} alt="Logo" />;
}

// Public folder
function Demo() {
  return <img src="/images/banner.jpg" alt="Banner" />;
}
```

---

## 22. Update State Based on Previous Value
**Interview Answer:**  
When updating state based on the previous value, always use the **functional form of setState/useState** to avoid stale state issues.  

**Syntax & Example:**
```jsx
// Function Component
const [count, setCount] = useState(0);
setCount(prevCount => prevCount + 1);

// Class Component
this.setState(prevState => ({ count: prevState.count + 1 }));
```

---

## 23. Children Props
**Interview Answer:**  
`props.children` allows components to render nested elements passed between opening and closing tags.  

**Syntax & Example:**
```jsx
function Card(props) {
  return <div className="card">{props.children}</div>;
}

// Usage
<Card>
  <h1>Title</h1>
  <p>Description</p>
</Card>
```

---

## 24. List Rendering
**Interview Answer:**  
React uses `map()` to render lists. Each item should have a unique `key` for efficient reconciliation.  

**Syntax & Example:**
```jsx
const items = ["Apple", "Banana", "Cherry"];

function Demo() {
  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>{item}</li>
      ))}
    </ul>
  );
}
```

---

## 25. Controlled Elements
**Interview Answer:**  
Controlled components are form inputs whose values are controlled by React state.  

**Syntax & Example:**
```jsx
function Demo() {
  const [value, setValue] = useState("");

  return (
    <input
      type="text"
      value={value}
      onChange={e => setValue(e.target.value)}
    />
  );
}
```

---

## 26. Why Index Should Not Be Passed as Key
**Interview Answer:**  
Using index as a key can cause rendering issues when list items change order, leading to incorrect UI updates. Always use unique IDs.  

**Example:**
```jsx
// Bad
items.map((item, index) => <li key={index}>{item}</li>);

// Good
items.map(item => <li key={item.id}>{item.name}</li>);
```

---

## 27. React Form Handling
**Interview Answer:**  
React handles forms using controlled components. Form data is stored in state and updated via `onChange`.  

**Syntax & Example:**
```jsx
function FormDemo() {
  const [name, setName] = useState("");

  const handleSubmit = e => {
    e.preventDefault();
    alert(`Submitted: ${name}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input value={name} onChange={e => setName(e.target.value)} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## 28. Uncontrolled Component in React
**Interview Answer:**  
Uncontrolled components rely on the DOM for state instead of React. Use `ref` to access values.  

**Syntax & Example:**
```jsx
function Demo() {
  const inputRef = useRef();

  const handleSubmit = () => {
    alert(inputRef.current.value);
  };

  return (
    <div>
      <input ref={inputRef} />
      <button onClick={handleSubmit}>Submit</button>
    </div>
  );
}
```

---

## 29. useRef vs useState
**Interview Answer:**  
- **useState:** Triggers re-render when updated.  
- **useRef:** Stores mutable values without re-rendering. Useful for DOM references.  

**Syntax & Example:**
```jsx
// useState
const [count, setCount] = useState(0);

// useRef
const inputRef = useRef();
<input ref={inputRef} />;
```

---

## 30. Component Composition
**Interview Answer:**  
Component composition is combining smaller components to build complex UIs. Encourages reusability and clean architecture.  

**Syntax & Example:**
```jsx
function Header() {
  return <h1>Header</h1>;
}

function Footer() {
  return <p>Footer</p>;
}

function Layout() {
  return (
    <div>
      <Header />
      <p>Main Content</p>
      <Footer />
    </div>
  );
}
```

---

Excellent — let’s continue with the **next section (Topics 31–40)** in the same **Markdown (MD) format** with **detailed interview-style answers, syntax, and examples**.  

---

# 📘 React Interview Prep (Topics 31–40)

---

## 31. Props Drilling
**Interview Answer:**  
Props drilling occurs when data is passed down through multiple layers of components, even if intermediate components don’t use it. This can make code harder to maintain. **Solution:** Context API or state management libraries.  

**Syntax & Example:**
```jsx
function Child({ name }) {
  return <h1>Hello {name}</h1>;
}

function Parent({ name }) {
  return <Child name={name} />;
}

function GrandParent() {
  return <Parent name="Prashanth" />;
}
```

---

## 32. Derived State
**Interview Answer:**  
Derived state is when component state is calculated from props or other state. It should be avoided if possible, since it can cause duplication. Instead, compute values directly during rendering.  

**Syntax & Example:**
```jsx
function Price({ amount, discount }) {
  const finalPrice = amount - discount; // derived from props
  return <p>Final Price: {finalPrice}</p>;
}
```

---

## 33. Context API
**Interview Answer:**  
Context API provides a way to share data across components without props drilling. It uses `React.createContext`, `Provider`, and `useContext`.  

**Syntax & Example:**
```jsx
const UserContext = React.createContext();

function App() {
  return (
    <UserContext.Provider value="Prashanth">
      <Profile />
    </UserContext.Provider>
  );
}

function Profile() {
  const user = React.useContext(UserContext);
  return <h1>Hello {user}</h1>;
}
```

---

## 34. Ways to Create Context API
**Interview Answer:**  
Steps to create and use Context API:  
1. Create context → `const MyContext = React.createContext()`  
2. Provide value → `<MyContext.Provider value={...}>`  
3. Consume value → `useContext(MyContext)` or `MyContext.Consumer`  

---

## 35. useEffect
**Interview Answer:**  
`useEffect` handles side effects in function components (API calls, subscriptions, DOM updates).  
- Runs after render.  
- Dependencies array controls when it runs.  

**Syntax & Example:**
```jsx
useEffect(() => {
  console.log("Component mounted");
}, []); // runs once

useEffect(() => {
  console.log("Count changed");
}, [count]); // runs when count changes
```

---

## 36. Reconciliation
**Interview Answer:**  
Reconciliation is React’s process of updating the DOM efficiently using the **Virtual DOM**. It compares the new virtual DOM with the previous one and updates only the changed parts.  

---

## 37. Virtual DOM
**Interview Answer:**  
Virtual DOM is a lightweight copy of the real DOM. React updates the virtual DOM first, then efficiently syncs changes to the real DOM. Improves performance.  

**Example:**  
```jsx
const element = <h1>Hello</h1>; // Virtual DOM representation
```

---

## 38. Lifecycle Methods
**Interview Answer:**  
Lifecycle methods exist in class components:  
- **Mounting:** `constructor`, `componentDidMount`  
- **Updating:** `componentDidUpdate`  
- **Unmounting:** `componentWillUnmount`  

**Syntax & Example:**
```jsx
class Demo extends React.Component {
  componentDidMount() {
    console.log("Mounted");
  }
  componentDidUpdate() {
    console.log("Updated");
  }
  componentWillUnmount() {
    console.log("Unmounted");
  }
  render() {
    return <h1>Lifecycle Demo</h1>;
  }
}
```

---

## 39. State in Class-Based Components
**Interview Answer:**  
State is defined in the constructor and updated using `this.setState()`.  

**Syntax & Example:**
```jsx
class Counter extends React.Component {
  constructor() {
    super();
    this.state = { count: 0 };
  }
  increment = () => {
    this.setState({ count: this.state.count + 1 });
  };
  render() {
    return <button onClick={this.increment}>{this.state.count}</button>;
  }
}
```

---

## 40. State in Function-Based Components
**Interview Answer:**  
Function components use the `useState` hook to manage state.  

**Syntax & Example:**
```jsx
function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

---

Perfect — let’s continue with the **next section (Topics 41–50)** in the same **Markdown (MD) format** with **detailed interview-style answers, syntax, and examples**.  

---

# 📘 React Interview Prep (Topics 41–50)

---

## 41. Render Method
**Interview Answer:**  
In class components, the `render()` method is required. It returns JSX that defines the UI. It should be pure (no side effects).  

**Syntax & Example:**
```jsx
class Demo extends React.Component {
  render() {
    return <h1>Hello from Render Method</h1>;
  }
}
```

---

## 42. Mounting Phase
**Interview Answer:**  
Mounting is the phase when a component is created and inserted into the DOM. Lifecycle methods:  
- `constructor()`  
- `render()`  
- `componentDidMount()`  

**Syntax & Example:**
```jsx
class Demo extends React.Component {
  componentDidMount() {
    console.log("Component Mounted");
  }
  render() {
    return <h1>Mounting Phase</h1>;
  }
}
```

---

## 43. Updating Phase
**Interview Answer:**  
Updating occurs when props or state change. Lifecycle methods:  
- `render()`  
- `componentDidUpdate()`  

**Syntax & Example:**
```jsx
class Demo extends React.Component {
  state = { count: 0 };

  componentDidUpdate() {
    console.log("Component Updated");
  }

  render() {
    return (
      <button onClick={() => this.setState({ count: this.state.count + 1 })}>
        {this.state.count}
      </button>
    );
  }
}
```

---

## 44. Unmounting Phase
**Interview Answer:**  
Unmounting is when a component is removed from the DOM. Lifecycle method: `componentWillUnmount()`.  

**Syntax & Example:**
```jsx
class Demo extends React.Component {
  componentWillUnmount() {
    console.log("Component Unmounted");
  }
  render() {
    return <h1>Unmounting Phase</h1>;
  }
}
```

---

## 45. React Routing
**Interview Answer:**  
React Router enables navigation between views in a single-page application. It uses `<BrowserRouter>`, `<Routes>`, and `<Route>`.  

**Syntax & Example:**
```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## 46. Single Page Application (SPA)
**Interview Answer:**  
SPA loads a single HTML page and dynamically updates content using JavaScript. React is commonly used to build SPAs. Benefits: faster navigation, better user experience.  

**Example:**  
React apps created with CRA are SPAs by default.

---

## 47. Unmounting Stage
**Interview Answer:**  
The unmounting stage is the final lifecycle phase when a component is destroyed. Cleanup tasks (like removing event listeners) should be done here.  

**Syntax & Example:**
```jsx
useEffect(() => {
  const timer = setInterval(() => console.log("Running..."), 1000);
  return () => clearInterval(timer); // cleanup on unmount
}, []);
```

---

## 48. Custom Hook
**Interview Answer:**  
Custom hooks are reusable functions that encapsulate logic using React hooks. They start with `use`.  

**Syntax & Example:**
```jsx
function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);
  const increment = () => setCount(count + 1);
  return { count, increment };
}

// Usage
function Demo() {
  const { count, increment } = useCounter();
  return <button onClick={increment}>{count}</button>;
}
```

---

## 49. Higher Order Components (HOC)
**Interview Answer:**  
HOCs are functions that take a component and return a new component with added functionality.  

**Syntax & Example:**
```jsx
function withLogger(WrappedComponent) {
  return function(props) {
    console.log("Props:", props);
    return <WrappedComponent {...props} />;
  };
}

const Demo = withLogger(() => <h1>Hello HOC</h1>);
```

---

## 50. Lazy Loading
**Interview Answer:**  
Lazy loading loads components only when needed, improving performance. React provides `React.lazy` and `Suspense`.  

**Syntax & Example:**
```jsx
import React, { Suspense, lazy } from "react";

const About = lazy(() => import("./About"));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <About />
    </Suspense>
  );
}
```

---

Perfect — let’s finish strong with the **last section (Topics 51–60)** in the same **Markdown (MD) format** with **detailed interview-style answers, syntax, and examples**. This will complete your full React interview prep handbook.  

---

# 📘 React Interview Prep (Topics 51–60)

---

## 51. useReducer vs reduce
**Interview Answer:**  
- **`reduce` (JavaScript):** Array method to reduce values into a single output.  
- **`useReducer` (React):** Hook for managing complex state logic, similar to Redux reducer pattern.  

**Syntax & Example:**
```jsx
// JavaScript reduce
const numbers = [1, 2, 3];
const sum = numbers.reduce((acc, val) => acc + val, 0); // 6

// React useReducer
function reducer(state, action) {
  switch (action.type) {
    case "increment": return { count: state.count + 1 };
    default: return state;
  }
}
const [state, dispatch] = useReducer(reducer, { count: 0 });
```

---

## 52. combineReducer
**Interview Answer:**  
In Redux, `combineReducers` merges multiple reducers into one root reducer, making state management modular.  

**Syntax & Example:**
```jsx
import { combineReducers } from "redux";

const userReducer = (state = {}, action) => state;
const productReducer = (state = [], action) => state;

const rootReducer = combineReducers({
  user: userReducer,
  products: productReducer,
});
```

---

## 53. Reducer Function
**Interview Answer:**  
A reducer is a pure function that takes the current state and an action, then returns the new state.  

**Syntax & Example:**
```jsx
function reducer(state, action) {
  switch (action.type) {
    case "add": return [...state, action.payload];
    case "remove": return state.filter(item => item !== action.payload);
    default: return state;
  }
}
```

---

## 54. useSelector
**Interview Answer:**  
`useSelector` is a React-Redux hook to access state from the Redux store inside a component.  

**Syntax & Example:**
```jsx
import { useSelector } from "react-redux";

function Demo() {
  const count = useSelector(state => state.counter.value);
  return <h1>Count: {count}</h1>;
}
```

---

## 55. useDispatch
**Interview Answer:**  
`useDispatch` is a React-Redux hook to dispatch actions to the store.  

**Syntax & Example:**
```jsx
import { useDispatch } from "react-redux";

function Demo() {
  const dispatch = useDispatch();
  return (
    <button onClick={() => dispatch({ type: "increment" })}>
      Increment
    </button>
  );
}
```

---

## 56. createStore
**Interview Answer:**  
`createStore` (Redux) creates a store that holds the application state.  

**Syntax & Example:**
```jsx
import { createStore } from "redux";

function reducer(state = { count: 0 }, action) {
  switch (action.type) {
    case "increment": return { count: state.count + 1 };
    default: return state;
  }
}

const store = createStore(reducer);
```

---

## 57. Axios
**Interview Answer:**  
Axios is a promise-based HTTP client for making API requests. It simplifies GET/POST requests compared to `fetch`.  

**Syntax & Example:**
```jsx
import axios from "axios";

useEffect(() => {
  axios.get("https://jsonplaceholder.typicode.com/posts")
    .then(res => console.log(res.data));
}, []);
```

---

## 58. useMemo
**Interview Answer:**  
`useMemo` memoizes expensive calculations so they don’t re-run unnecessarily.  

**Syntax & Example:**
```jsx
const expensiveValue = useMemo(() => {
  return computeExpensiveValue(count);
}, [count]);
```

---

## 59. useCallback
**Interview Answer:**  
`useCallback` memoizes functions to prevent re-creation on every render, useful when passing callbacks to child components.  

**Syntax & Example:**
```jsx
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

---

## 60. React.callback
**Interview Answer:**  
This usually refers to using callbacks in React — functions passed as props to child components so they can communicate with parents.  

**Syntax & Example:**
```jsx
function Child({ onAction }) {
  return <button onClick={onAction}>Trigger Action</button>;
}

function Parent() {
  const handleAction = () => alert("Action triggered!");
  return <Child onAction={handleAction} />;
}
```

---








