Components

Function-Based Components
Function-based components are plain JavaScript functions that return JSX. They're the recommended way to create components in React.

Example:

import React from 'react';

function Greeting(props) {
return <h1>Hello, {props.name}!</h1>;
}

Class-Based Components
Class-based components are JavaScript classes that extend the React Component class. They're useful when you need to use lifecycle methods or handle state.

Example:

import React, { Component } from 'react';

class Greeting extends Component {
render() {
return <h1>Hello, {this.props.name}!</h1>;
}
}

State Management

useState
useState is a hook that allows you to add state to function-based components.

Example:

import React, { useState } from 'react';

function Counter() {
const [count, setCount] = useState(0);

return (
<div>
<p>Count: {count}</p>
<button onClick={() => setCount(count + 1)}>Increment</button>
</div>
);
}

useReducer
useReducer is a hook that allows you to manage complex state with a reducer function.

Example:

import React, { useReducer } from 'react';

const initialState = { count: 0 };

const reducer = (state, action) => {
switch (action.type) {
case 'INCREMENT':
return { count: state.count + 1 };
default:
return state;
}
};

function Counter() {
const [state, dispatch] = useReducer(reducer, initialState);

return (
<div>
<p>Count: {state.count}</p>
<button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
</div>
);
}

Redux
Redux is a state management library that helps you manage global state by providing a single source of truth.

Example:

import { createStore } from 'redux';

const store = createStore((state = 0, action) => {
switch (action.type) {
case 'INCREMENT':
return state + 1;
default:
return state;
}
});

Hooks

useEffect
useEffect is a hook that allows you to run side effects after rendering.

Example:

import React, { useState, useEffect } from 'react';

function FetchData() {
const [data, setData] = useState([]);

useEffect(() => {
fetch('https://api.example.com/data')
.then(response => response.json())
.then(data => setData(data));
}, []);

return <ul>{data.map(item => <li key={item.id}>{item.name}</li>)}</ul>;
}

useCallback
useCallback is a hook that memoizes a function so it's not recreated unnecessarily.

Example:

import React, { useState, useCallback } from 'react';

function SearchInput() {
const [searchTerm, setSearchTerm] = useState('');

const handleSearch = useCallback(() => {
console.log(`Searching for ${searchTerm}`);
}, [searchTerm]);

return (
<div>
<input type="search" value={searchTerm} onChange={e => setSearchTerm(e.target.value)} />
<button onClick={handleSearch}>Search</button>
</div>
);
}

useMemo
useMemo is a hook that memoizes a value so it's not recalculated unnecessarily.

Example:

import React, { useState, useMemo } from 'react';

function ShoppingList() {
const [items, setItems] = useState(['Apple', 'Banana', 'Orange']);

const totalCost = useMemo(() => {
return items.reduce((total, item) => total + 1, 0);
}, [items]);

return (
<div>
<ul>{items.map(item => <li key={item}>{item}</li>)}</ul>
<p>Total items: {totalCost}</p>
</div>
);
}

Let's continue with the rest of the topics.

Performance Optimization

Lazy Loading
Lazy loading is a technique that allows you to load components or modules only when they're needed. This can improve performance by reducing the initial payload size.

Example:

import React, { Suspense, lazy } from 'react';

const LazyComponent = lazy(() => import('./LazyComponent'));

function App() {
return (
<Suspense fallback={<div>Loading...</div>}>
<LazyComponent />
</Suspense>
);
}

Memoization
Memoization is a technique that allows you to cache the results of expensive function calls so they're not recalculated unnecessarily.

Example:

import React, { useMemo } from 'react';

function expensiveCalculation(n) {
// Simulate an expensive calculation
for (let i = 0; i < 100000000; i++) {}
return n \* 2;
}

function App() {
const result = useMemo(() => expensiveCalculation(10), []);

return <div>Result: {result}</div>;
}

React Routing

Client-Side Routing
Client-side routing allows you to navigate between different routes in your application without requiring a full page reload.

Example:

import React from 'react';
import { BrowserRouter, Route, Link } from 'react-router-dom';

function App() {
return (
<BrowserRouter>
<div>
<h1>Home</h1>
<p>
<Link to="/about">About</Link>
</p>
</div>
<Route path="/about">
<About />
</Route>
</BrowserRouter>
);
}

function About() {
return <h1>About</h1>;
}

Context API

Sharing Data Between Components
The Context API allows you to share data between components without passing props down manually.

Example:

import React, { createContext, useState } from 'react';

const ThemeContext = createContext();

function App() {
const [theme, setTheme] = useState('light');

return (
<ThemeContext.Provider value={{ theme, setTheme }}>
<Toolbar />
</ThemeContext.Provider>
);
}

function Toolbar() {
const { theme } = useContext(ThemeContext);

return <div>Toolbar theme: {theme}</div>;
}

Higher-Order Components (HOCs)

What are HOCs?
Higher-Order Components are functions that take a component as an argument and return a new component with additional props or behavior.

Example:

import React from 'react';

const withLogging = (WrappedComponent) => {
const logger = () => {
console.log('Component rendered');
};

return function EnhancedComponent(props) {
logger();
return <WrappedComponent {...props} />;
};
};

const MyComponent = () => {
return <div>Hello World!</div>;
};

const MyComponentWithLogging = withLogging(MyComponent);

Custom Hooks

What are Custom Hooks?
Custom Hooks are reusable functions that use React Hooks to manage state and side effects.

Example:

import React, { useState, useEffect } from 'react';

const useFetchData = (url) => {
const [data, setData] = useState([]);
const [error, setError] = useState(null);

useEffect(() => {
fetch(url)
.then(response => response.json())
.then(data => setData(data))
.catch(error => setError(error));
}, [url]);

return { data, error };
};

const MyComponent = () => {
const { data, error } = useFetchData('https://api.example.com/data');

if (error) {
return <div>Error: {error.message}</div>;
}

return <div>Data: {data}</div>;
};

React Lifecycle Methods

What are Lifecycle Methods?
Lifecycle Methods are methods that are called at different points in a component's life cycle, such as when it's mounted or unmounted.

Example:

import React, { Component } from 'react';

class MyComponent extends Component {
componentDidMount() {
console.log('Component mounted');
}

componentWillUnmount() {
console.log('Component will unmount');
}

render() {
return <div>Hello World!</div>;
}
}

State in Class-Based Components

What is State?
State is an object that determines the behavior and rendering of a component.

Example:

import React, { Component } from 'react';

class Counter extends Component {
constructor(props) {
super(props);
this.state = { count: 0 };
}

render() {
return (
<div>
<p>Count: {this.state.count}</p>
<button onClick={() => this.setState({ count: this.state.count + 1 })}>
Increment
</button>
</div>
);
}
}

State in Function-Based Components

What is State?
State is an object that determines the behavior and rendering of a component.

Example:

import React, { useState } from 'react';

const Counter = () => {
const [count, setCount] = useState(0);

return (
<div>
<p>Count: {count}</p>
<button onClick={() => setCount(count + 1)}>Increment</button>
</div>
);
};

Let's continue with the rest of the topics.

React Routing

Route Parameters
Route parameters allow you to capture values from the URL and use them in your component.

Example:

import React from 'react';
import { BrowserRouter, Route } from 'react-router-dom';

const User = ({ match }) => {
return <div>User ID: {match.params.id}</div>;
};

const App = () => {
return (
<BrowserRouter>
<Route path="/users/:id" component={User} />
</BrowserRouter>
);
};

Query Parameters
Query parameters allow you to pass data from one route to another using the URL.

Example:

import React from 'react';
import { useLocation } from 'react-router-dom';

const SearchResults = () => {
const location = useLocation();
const query = new URLSearchParams(location.search).get('query');

return <div>Search results for: {query}</div>;
};

Redux

Actions
Actions are payloads that are sent to the store to trigger state changes.

Example:

import { createStore } from 'redux';

const incrementCounter = () => {
return { type: 'INCREMENT_COUNTER' };
};

const store = createStore((state = 0, action) => {
switch (action.type) {
case 'INCREMENT_COUNTER':
return state + 1;
default:
return state;
}
});

Reducers
Reducers are pure functions that take the current state and an action, and return a new state.

Example:

import { createStore } from 'redux';

const counterReducer = (state = 0, action) => {
switch (action.type) {
case 'INCREMENT_COUNTER':
return state + 1;
default:
return state;
}
};

const store = createStore(counterReducer);

useCallback and useMemo

useCallback
useCallback is a hook that memoizes a function so it's not recreated unnecessarily.

Example:

import React, { useState, useCallback } from 'react';

const SearchInput = () => {
const [searchTerm, setSearchTerm] = useState('');

const handleSearch = useCallback(() => {
console.log(`Searching for ${searchTerm}`);
}, [searchTerm]);

return (
<div>
<input type="search" value={searchTerm} onChange={(e) => setSearchTerm(e.target.value)} />
<button onClick={handleSearch}>Search</button>
</div>
);
};

useMemo
useMemo is a hook that memoizes a value so it's not recalculated unnecessarily.

Example:

import React, { useState, useMemo } from 'react';

const ShoppingList = () => {
const [items, setItems] = useState(['Apple', 'Banana', 'Orange']);

const totalCost = useMemo(() => {
return items.reduce((total, item) => total + 1, 0);
}, [items]);

return (
<div>
<ul>{items.map((item) => <li key={item}>{item}</li>)}</ul>
<p>Total items: {totalCost}</p>
</div>
);
};
