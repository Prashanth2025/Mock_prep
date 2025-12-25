# React Concepts Guide

## Components

### **1. Function-Based Components**
**Theory:** Simple JavaScript functions that return JSX. Stateless by default (until hooks). Pure functions that take props and return UI.

```jsx
// Simple functional component
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

// Arrow function syntax
const Button = ({ onClick, children }) => (
  <button onClick={onClick}>{children}</button>
);

// With TypeScript
interface UserProps {
  name: string;
  age: number;
}

const UserCard: React.FC<UserProps> = ({ name, age }) => (
  <div>
    <h2>{name}</h2>
    <p>Age: {age}</p>
  </div>
);
```

**Key Points:**
- No lifecycle methods (use hooks instead)
- No `this` keyword
- Easier to test and understand
- Recommended for most use cases

### **2. Class-Based Components**
**Theory:** ES6 classes extending `React.Component`. Have lifecycle methods and internal state.

```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState(prevState => ({
      count: prevState.count + 1
    }));
  }

  componentDidMount() {
    console.log('Component mounted');
  }

  componentDidUpdate() {
    console.log('Component updated');
  }

  componentWillUnmount() {
    console.log('Component will unmount');
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.handleClick}>
          Increment
        </button>
      </div>
    );
  }
}
```

**Key Points:**
- Have lifecycle methods
- Use `this.state` and `this.setState`
- `this` binding required for methods
- Legacy but still used

## State Management

### **3. useState Hook**
**Theory:** Hook for adding state to functional components. Returns state value and setter function.

```jsx
import React, { useState } from 'react';

function Counter() {
  // Basic state
  const [count, setCount] = useState(0);
  
  // Object state
  const [user, setUser] = useState({
    name: 'John',
    age: 30
  });
  
  // Function initial state (lazy initialization)
  const [data, setData] = useState(() => {
    const expensiveResult = calculateExpensiveValue();
    return expensiveResult;
  });
  
  const increment = () => {
    // Functional update
    setCount(prevCount => prevCount + 1);
  };
  
  const updateUser = () => {
    // Merge updates for objects
    setUser(prevUser => ({
      ...prevUser,
      age: prevUser.age + 1
    }));
  };
  
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <p>{user.name} is {user.age} years old</p>
      <button onClick={updateUser}>Make Older</button>
    </div>
  );
}
```

### **4. useReducer Hook**
**Theory:** For complex state logic with multiple sub-values or when next state depends on previous.

```jsx
import React, { useReducer } from 'react';

// Initial state
const initialState = {
  count: 0,
  history: []
};

// Reducer function
function counterReducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return {
        ...state,
        count: state.count + 1,
        history: [...state.history, 'INCREMENT']
      };
    case 'DECREMENT':
      return {
        ...state,
        count: state.count - 1,
        history: [...state.history, 'DECREMENT']
      };
    case 'RESET':
      return initialState;
    default:
      throw new Error('Unknown action type');
  }
}

function Counter() {
  const [state, dispatch] = useReducer(counterReducer, initialState);
  
  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>
        Increment
      </button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>
        Decrement
      </button>
      <button onClick={() => dispatch({ type: 'RESET' })}>
        Reset
      </button>
      <p>History: {state.history.join(', ')}</p>
    </div>
  );
}
```

### **5. Redux**
**Theory:** Predictable state container with single source of truth.

```jsx
// store.js
import { createStore, combineReducers } from 'redux';

// Action types
const INCREMENT = 'INCREMENT';
const DECREMENT = 'DECREMENT';

// Action creators
export const increment = () => ({ type: INCREMENT });
export const decrement = () => ({ type: DECREMENT });

// Reducer
const counterReducer = (state = 0, action) => {
  switch (action.type) {
    case INCREMENT:
      return state + 1;
    case DECREMENT:
      return state - 1;
    default:
      return state;
  }
};

// Combine reducers
const rootReducer = combineReducers({
  counter: counterReducer
});

// Create store
const store = createStore(rootReducer);

// Component
import React from 'react';
import { connect } from 'react-redux';
import { increment, decrement } from './store';

const Counter = ({ count, increment, decrement }) => (
  <div>
    <p>Count: {count}</p>
    <button onClick={increment}>Increment</button>
    <button onClick={decrement}>Decrement</button>
  </div>
);

const mapStateToProps = state => ({
  count: state.counter
});

const mapDispatchToProps = {
  increment,
  decrement
};

export default connect(mapStateToProps, mapDispatchToProps)(Counter);
```

## Hooks

### **6. useEffect Hook**
**Theory:** Handle side effects in functional components.

```jsx
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  // ComponentDidMount equivalent
  useEffect(() => {
    console.log('Component mounted');
    return () => {
      console.log('Component will unmount');
    };
  }, []);
  
  // ComponentDidUpdate equivalent (when id changes)
  const [id, setId] = useState(1);
  useEffect(() => {
    if (!id) return;
    
    setLoading(true);
    fetch(`https://api.example.com/data/${id}`)
      .then(response => response.json())
      .then(data => {
        setData(data);
        setLoading(false);
      })
      .catch(error => {
        setError(error);
        setLoading(false);
      });
  }, [id]); // Dependency array
  
  // Cleanup function
  useEffect(() => {
    const intervalId = setInterval(() => {
      console.log('Tick');
    }, 1000);
    
    return () => {
      clearInterval(intervalId); // Cleanup
    };
  }, []);
  
  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;
  
  return (
    <div>
      <button onClick={() => setId(id + 1)}>Next</button>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}
```

### **7. useCallback Hook**
**Theory:** Memoize functions to prevent unnecessary re-renders.

```jsx
import React, { useState, useCallback } from 'react';

function ParentComponent() {
  const [count, setCount] = useState(0);
  const [value, setValue] = useState('');
  
  // Without useCallback - recreated on every render
  const handleClick = () => {
    console.log('Clicked');
  };
  
  // With useCallback - only recreated when dependencies change
  const memoizedHandleClick = useCallback(() => {
    console.log('Memoized click', count);
  }, [count]); // Only recreate when count changes
  
  // Common use case: passing callback to child
  const ChildComponent = React.memo(({ onClick }) => {
    console.log('Child rendered');
    return <button onClick={onClick}>Click me</button>;
  });
  
  return (
    <div>
      <input
        value={value}
        onChange={e => setValue(e.target.value)}
      />
      <button onClick={() => setCount(count + 1)}>
        Increment: {count}
      </button>
      
      {/* Child will re-render if handleClick changes */}
      <ChildComponent onClick={memoizedHandleClick} />
    </div>
  );
}
```

### **8. useMemo Hook**
**Theory:** Memoize expensive computations.

```jsx
import React, { useState, useMemo } from 'react';

function ExpensiveComponent() {
  const [count, setCount] = useState(0);
  const [items, setItems] = useState([1, 2, 3, 4, 5]);
  
  // Expensive calculation
  const expensiveCalculation = (numbers) => {
    console.log('Calculating...');
    // Simulate expensive operation
    return numbers.reduce((sum, num) => {
      for (let i = 0; i < 1000000; i++) {} // Slow loop
      return sum + num;
    }, 0);
  };
  
  // Without useMemo - recalculates on every render
  const totalBad = expensiveCalculation(items);
  
  // With useMemo - only recalculates when items change
  const totalGood = useMemo(() => 
    expensiveCalculation(items), 
    [items]
  );
  
  // Another example: memoizing derived data
  const filteredItems = useMemo(() => 
    items.filter(item => item > 2), 
    [items]
  );
  
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Re-render
      </button>
      <p>Total: {totalGood}</p>
      <p>Filtered: {filteredItems.join(', ')}</p>
    </div>
  );
}
```

## Performance Optimization

### **9. Lazy Loading**
**Theory:** Load components only when needed.

```jsx
import React, { Suspense, lazy } from 'react';

// Regular import (eager loading)
// import HeavyComponent from './HeavyComponent';

// Lazy import (code splitting)
const HeavyComponent = lazy(() => import('./HeavyComponent'));
const AnotherComponent = lazy(() => 
  import('./AnotherComponent').then(module => ({
    default: module.AnotherComponent
  }))
);

function App() {
  const [showHeavy, setShowHeavy] = useState(false);
  
  return (
    <div>
      <button onClick={() => setShowHeavy(true)}>
        Load Heavy Component
      </button>
      
      {showHeavy && (
        <Suspense 
          fallback={
            <div style={{ padding: '20px' }}>
              Loading heavy component...
            </div>
          }
        >
          <HeavyComponent />
          {/* Nested suspense for individual components */}
          <Suspense fallback={<div>Loading another...</div>}>
            <AnotherComponent />
          </Suspense>
        </Suspense>
      )}
    </div>
  );
}
```

### **10. Memoization with React.memo**
**Theory:** Prevent unnecessary re-renders of components.

```jsx
import React, { memo, useState } from 'react';

// Regular component (re-renders when parent re-renders)
const RegularButton = ({ onClick, children }) => {
  console.log('RegularButton rendered');
  return <button onClick={onClick}>{children}</button>;
};

// Memoized component (only re-renders when props change)
const MemoizedButton = memo(({ onClick, children }) => {
  console.log('MemoizedButton rendered');
  return <button onClick={onClick}>{children}</button>;
});

// Custom comparison function
const DeepCompareButton = memo(
  ({ config, children }) => {
    console.log('DeepCompareButton rendered');
    return (
      <button style={config.style}>
        {children}
      </button>
    );
  },
  (prevProps, nextProps) => {
    // Return true if props are equal (don't re-render)
    return (
      prevProps.config.color === nextProps.config.color &&
      prevProps.config.size === nextProps.config.size &&
      prevProps.children === nextProps.children
    );
  }
);

function Parent() {
  const [count, setCount] = useState(0);
  const [theme, setTheme] = useState('light');
  
  const handleClick = () => {
    console.log('Clicked');
  };
  
  const config = {
    color: theme === 'light' ? '#000' : '#fff',
    size: 'medium'
  };
  
  return (
    <div>
      <button onClick={() => setCount(count + 1)}>
        Re-render Parent ({count})
      </button>
      <button onClick={() => setTheme(
        theme === 'light' ? 'dark' : 'light'
      )}>
        Toggle Theme
      </button>
      
      {/* Re-renders every time */}
      <RegularButton onClick={handleClick}>
        Regular
      </RegularButton>
      
      {/* Only re-renders when onClick changes */}
      <MemoizedButton onClick={handleClick}>
        Memoized
      </MemoizedButton>
      
      {/* Only re-renders when config deeply changes */}
      <DeepCompareButton config={config}>
        Deep Compare
      </DeepCompareButton>
    </div>
  );
}
```

## React Routing

### **11. Client-Side Routing with React Router**
**Theory:** Handle navigation without page reloads.

```jsx
import React from 'react';
import {
  BrowserRouter as Router,
  Switch,
  Route,
  Link,
  useParams,
  useHistory,
  useLocation,
  Redirect
} from 'react-router-dom';

function App() {
  return (
    <Router>
      <nav>
        <ul>
          <li><Link to="/">Home</Link></li>
          <li><Link to="/about">About</Link></li>
          <li><Link to="/users">Users</Link></li>
          <li><Link to="/dashboard">Dashboard</Link></li>
        </ul>
      </nav>
      
      <Switch>
        <Route exact path="/">
          <Home />
        </Route>
        
        <Route path="/about">
          <About />
        </Route>
        
        <Route path="/users/:id">
          <UserDetail />
        </Route>
        
        <Route path="/users">
          <Users />
        </Route>
        
        {/* Protected route */}
        <PrivateRoute path="/dashboard">
          <Dashboard />
        </PrivateRoute>
        
        {/* 404 page */}
        <Route path="*">
          <NotFound />
        </Route>
      </Switch>
    </Router>
  );
}

function Home() {
  return <h1>Home Page</h1>;
}

function About() {
  return <h1>About Page</h1>;
}

function Users() {
  const users = [
    { id: 1, name: 'John' },
    { id: 2, name: 'Jane' }
  ];
  
  return (
    <div>
      <h1>Users</h1>
      <ul>
        {users.map(user => (
          <li key={user.id}>
            <Link to={`/users/${user.id}`}>
              {user.name}
            </Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

function UserDetail() {
  // Get route parameters
  const { id } = useParams();
  // Get history object for navigation
  const history = useHistory();
  // Get current location
  const location = useLocation();
  
  return (
    <div>
      <h1>User ID: {id}</h1>
      <button onClick={() => history.push('/users')}>
        Back to Users
      </button>
      <button onClick={() => history.goBack()}>
        Go Back
      </button>
      <p>Current path: {location.pathname}</p>
    </div>
  );
}

// Protected route component
function PrivateRoute({ children, ...rest }) {
  const isAuthenticated = true; // Check auth here
  
  return (
    <Route {...rest}
      render={({ location }) =>
        isAuthenticated ? (
          children
        ) : (
          <Redirect
            to={{
              pathname: "/login",
              state: { from: location }
            }}
          />
        )
      }
    />
  );
}

function NotFound() {
  return <h1>404 - Page Not Found</h1>;
}
```

### **12. Route Parameters & Query Parameters**
**Theory:** Extract data from URLs.

```jsx
import React from 'react';
import { useParams, useLocation } from 'react-router-dom';

// Route parameters
function ProductPage() {
  const { category, id } = useParams();
  // URL: /products/electronics/123
  // category = 'electronics', id = '123'
  
  return (
    <div>
      <h1>Category: {category}</h1>
      <p>Product ID: {id}</p>
    </div>
  );
}

// Query parameters
function SearchResults() {
  const location = useLocation();
  const queryParams = new URLSearchParams(location.search);
  
  const query = queryParams.get('q');
  const sort = queryParams.get('sort') || 'relevance';
  const page = parseInt(queryParams.get('page') || '1');
  
  // URL: /search?q=react&sort=date&page=2
  // query = 'react', sort = 'date', page = 2
  
  return (
    <div>
      <h1>Search Results for: {query}</h1>
      <p>Sorted by: {sort}</p>
      <p>Page: {page}</p>
    </div>
  );
}

// Programmatic navigation with query params
function SearchForm() {
  const history = useHistory();
  const [searchTerm, setSearchTerm] = useState('');
  
  const handleSearch = (e) => {
    e.preventDefault();
    history.push(`/search?q=${searchTerm}&sort=date`);
  };
  
  return (
    <form onSubmit={handleSearch}>
      <input
        type="text"
        value={searchTerm}
        onChange={e => setSearchTerm(e.target.value)}
        placeholder="Search..."
      />
      <button type="submit">Search</button>
    </form>
  );
}
```

## Context API

### **13. Sharing Data Between Components**
**Theory:** Global state management without prop drilling.

```jsx
import React, { createContext, useContext, useState } from 'react';

// 1. Create Context
const ThemeContext = createContext();
const UserContext = createContext();

// 2. Create Provider Component
function AppProvider({ children }) {
  const [theme, setTheme] = useState('light');
  const [user, setUser] = useState(null);
  
  const toggleTheme = () => {
    setTheme(prev => prev === 'light' ? 'dark' : 'light');
  };
  
  const login = (userData) => {
    setUser(userData);
  };
  
  const logout = () => {
    setUser(null);
  };
  
  const themeValue = { theme, toggleTheme };
  const userValue = { user, login, logout };
  
  return (
    <ThemeContext.Provider value={themeValue}>
      <UserContext.Provider value={userValue}>
        {children}
      </UserContext.Provider>
    </ThemeContext.Provider>
  );
}

// 3. Custom Hook for easier consumption
function useTheme() {
  const context = useContext(ThemeContext);
  if (!context) {
    throw new Error('useTheme must be used within ThemeProvider');
  }
  return context;
}

function useUser() {
  const context = useContext(UserContext);
  if (!context) {
    throw new Error('useUser must be used within UserProvider');
  }
  return context;
}

// 4. Components using Context
function ThemeToggle() {
  const { theme, toggleTheme } = useTheme();
  
  return (
    <button onClick={toggleTheme}>
      Switch to {theme === 'light' ? 'Dark' : 'Light'} Mode
    </button>
  );
}

function UserProfile() {
  const { user, logout } = useUser();
  
  if (!user) {
    return <div>Please log in</div>;
  }
  
  return (
    <div>
      <h2>Welcome, {user.name}!</h2>
      <p>Email: {user.email}</p>
      <button onClick={logout}>Logout</button>
    </div>
  );
}

function Navbar() {
  const { theme } = useTheme();
  const { user } = useUser();
  
  return (
    <nav style={{
      background: theme === 'light' ? '#fff' : '#333',
      color: theme === 'light' ? '#000' : '#fff'
    }}>
      <h1>My App</h1>
      <ThemeToggle />
      {user && <span>Logged in as {user.name}</span>}
    </nav>
  );
}

// 5. App component
function App() {
  return (
    <AppProvider>
      <Navbar />
      <UserProfile />
      {/* All children have access to context */}
    </AppProvider>
  );
}
```

## Higher-Order Components (HOCs)

### **14. What are HOCs?**
**Theory:** Functions that take a component and return an enhanced component.

```jsx
import React from 'react';

// 1. Basic HOC - adds props
const withUser = (WrappedComponent) => {
  const user = { name: 'John', role: 'admin' };
  
  return function EnhancedComponent(props) {
    return <WrappedComponent {...props} user={user} />;
  };
};

// 2. HOC with state
const withToggle = (WrappedComponent) => {
  return class WithToggle extends React.Component {
    state = { isOn: false };
    
    toggle = () => {
      this.setState(prevState => ({ isOn: !prevState.isOn }));
    };
    
    render() {
      return (
        <WrappedComponent
          {...this.props}
          isOn={this.state.isOn}
          toggle={this.toggle}
        />
      );
    }
  };
};

// 3. HOC for logging
const withLogging = (WrappedComponent) => {
  return class WithLogging extends React.Component {
    componentDidMount() {
      console.log(`Component ${WrappedComponent.name} mounted`);
    }
    
    componentWillUnmount() {
      console.log(`Component ${WrappedComponent.name} will unmount`);
    }
    
    render() {
      return <WrappedComponent {...this.props} />;
    }
  };
};

// 4. Composing multiple HOCs
const compose = (...hocs) => (Component) =>
  hocs.reduceRight((acc, hoc) => hoc(acc), Component);

// 5. Using HOCs
function MyComponent({ user, isOn, toggle, message }) {
  return (
    <div>
      <h2>Hello, {user?.name}</h2>
      <p>Toggle is {isOn ? 'ON' : 'OFF'}</p>
      <button onClick={toggle}>Toggle</button>
      <p>{message}</p>
    </div>
  );
}

// Apply HOCs
const EnhancedComponent = compose(
  withUser,
  withToggle,
  withLogging
)(MyComponent);

// Or apply individually
// const WithUser = withUser(MyComponent);
// const WithToggle = withToggle(WithUser);

// Usage
function App() {
  return <EnhancedComponent message="Hello from HOC" />;
}
```

## Custom Hooks

### **15. What are Custom Hooks?**
**Theory:** Reusable logic extracted from components.

```jsx
import { useState, useEffect, useCallback } from 'react';

// 1. Custom hook for form handling
function useForm(initialValues = {}, onSubmit) {
  const [values, setValues] = useState(initialValues);
  const [errors, setErrors] = useState({});
  const [isSubmitting, setIsSubmitting] = useState(false);
  
  const handleChange = useCallback((e) => {
    const { name, value, type, checked } = e.target;
    setValues(prev => ({
      ...prev,
      [name]: type === 'checkbox' ? checked : value
    }));
    
    // Clear error when user starts typing
    if (errors[name]) {
      setErrors(prev => ({ ...prev, [name]: '' }));
    }
  }, [errors]);
  
  const handleSubmit = async (e) => {
    e.preventDefault();
    setIsSubmitting(true);
    
    try {
      await onSubmit(values);
    } catch (error) {
      setErrors({ submit: error.message });
    } finally {
      setIsSubmitting(false);
    }
  };
  
  const resetForm = useCallback(() => {
    setValues(initialValues);
    setErrors({});
  }, [initialValues]);
  
  return {
    values,
    errors,
    isSubmitting,
    handleChange,
    handleSubmit,
    resetForm,
    setValues,
    setErrors
  };
}

// 2. Custom hook for API fetching
function useFetch(url, options = {}) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
  
  const fetchData = useCallback(async () => {
    try {
      setLoading(true);
      const response = await fetch(url, options);
      
      if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
      }
      
      const result = await response.json();
      setData(result);
      setError(null);
    } catch (err) {
      setError(err.message);
    } finally {
      setLoading(false);
    }
  }, [url, options]);
  
  useEffect(() => {
    fetchData();
  }, [fetchData]);
  
  const refetch = () => {
    fetchData();
  };
  
  return { data, loading, error, refetch };
}

// 3. Custom hook for localStorage
function useLocalStorage(key, initialValue) {
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error(error);
      return initialValue;
    }
  });
  
  const setValue = (value) => {
    try {
      const valueToStore = value instanceof Function 
        ? value(storedValue) 
        : value;
      
      setStoredValue(valueToStore);
      window.localStorage.setItem(key, JSON.stringify(valueToStore));
    } catch (error) {
      console.error(error);
    }
  };
  
  return [storedValue, setValue];
}

// 4. Using custom hooks
function LoginForm() {
  const { values, errors, isSubmitting, handleChange, handleSubmit } = useForm(
    { email: '', password: '' },
    async (formValues) => {
      // API call
      await loginUser(formValues);
    }
  );
  
  return (
    <form onSubmit={handleSubmit}>
      <input
        name="email"
        type="email"
        value={values.email}
        onChange={handleChange}
        placeholder="Email"
      />
      {errors.email && <span>{errors.email}</span>}
      
      <input
        name="password"
        type="password"
        value={values.password}
        onChange={handleChange}
        placeholder="Password"
      />
      {errors.password && <span>{errors.password}</span>}
      
      <button type="submit" disabled={isSubmitting}>
        {isSubmitting ? 'Logging in...' : 'Login'}
      </button>
    </form>
  );
}

function UserProfile() {
  const { data: user, loading, error } = useFetch('/api/user');
  const [theme, setTheme] = useLocalStorage('theme', 'light');
  
  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;
  
  return (
    <div className={`theme-${theme}`}>
      <h1>{user.name}</h1>
      <button onClick={() => setTheme('dark')}>
        Set Dark Theme
      </button>
    </div>
  );
}
```

## React Lifecycle Methods

### **16. Class Component Lifecycle**
**Theory:** Methods called at different stages of component lifecycle.

```jsx
class LifecycleDemo extends React.Component {
  // 1. Mounting Phase
  constructor(props) {
    super(props);
    console.log('1. Constructor');
    this.state = { count: 0 };
  }
  
  static getDerivedStateFromProps(nextProps, prevState) {
    console.log('2. getDerivedStateFromProps');
    // Return new state based on props
    return null;
  }
  
  componentDidMount() {
    console.log('4. componentDidMount');
    // Good for:
    // - API calls
    // - Setting up subscriptions
    // - Initializing third-party libraries
    this.timer = setInterval(() => {
      console.log('Timer tick');
    }, 1000);
  }
  
  // 2. Updating Phase
  shouldComponentUpdate(nextProps, nextState) {
    console.log('shouldComponentUpdate');
    // Return false to prevent re-render
    return nextState.count !== this.state.count;
  }
  
  getSnapshotBeforeUpdate(prevProps, prevState) {
    console.log('getSnapshotBeforeUpdate');
    // Capture some DOM info before update
    return { scrollPosition: window.scrollY };
  }
  
  componentDidUpdate(prevProps, prevState, snapshot) {
    console.log('componentDidUpdate');
    console.log('Snapshot:', snapshot);
    // Good for:
    // - DOM operations after update
    // - Network requests based on prop changes
  }
  
  // 3. Unmounting Phase
  componentWillUnmount() {
    console.log('componentWillUnmount');
    // Cleanup:
    clearInterval(this.timer);
  }
  
  // 4. Error Handling
  static getDerivedStateFromError(error) {
    console.log('getDerivedStateFromError');
    return { hasError: true };
  }
  
  componentDidCatch(error, info) {
    console.log('componentDidCatch', error, info);
    // Log error to service
  }
  
  render() {
    console.log('3. Render');
    if (this.state.hasError) {
      return <h1>Something went wrong.</h1>;
    }
    
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => 
          this.setState({ count: this.state.count + 1 })
        }>
          Increment
        </button>
      </div>
    );
  }
}
```

### **17. Functional Component Lifecycle with Hooks**
**Theory:** Equivalent lifecycle behavior using hooks.

```jsx
import React, { useState, useEffect, useLayoutEffect } from 'react';

function HookLifecycleDemo() {
  const [count, setCount] = useState(0);
  const [data, setData] = useState(null);
  
  // componentDidMount equivalent
  useEffect(() => {
    console.log('Component mounted');
    
    // Cleanup function (componentWillUnmount equivalent)
    return () => {
      console.log('Component will unmount');
    };
  }, []); // Empty dependency array = run once on mount
  
  // componentDidUpdate equivalent for count
  useEffect(() => {
    console.log('Count updated:', count);
    
    // Cleanup for previous effect
    return () => {
      console.log('Cleanup before count update');
    };
  }, [count]); // Run when count changes
  
  // componentDidUpdate equivalent for all updates
  useEffect(() => {
    console.log('Component updated');
  }); // No dependency array = run on every render
  
  // getSnapshotBeforeUpdate equivalent
  useLayoutEffect(() => {
    // Runs synchronously after DOM mutations
    console.log('DOM updated, before browser paint');
    
    return () => {
      console.log('Cleanup before DOM update');
    };
  });
  
  // Error handling
  const [hasError, setHasError] = useState(false);
  
  if (hasError) {
    return <h1>Something went wrong.</h1>;
  }
  
  // Simulate render error
  const handleClick = () => {
    try {
      // Some operation that might fail
      throw new Error('Test error');
    } catch (error) {
      setHasError(true);
    }
  };
  
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
      <button onClick={handleClick}>
        Trigger Error
      </button>
    </div>
  );
}
```

## State in Components

### **18. State in Class-Based Components**
**Theory:** Internal component state using `this.state` and `this.setState`.

```jsx
class ClassState extends React.Component {
  constructor(props) {
    super(props);
    // Initialize state
    this.state = {
      count: 0,
      user: { name: 'John', age: 30 },
      items: [],
      loading: false
    };
    
    // Bind methods
    this.handleClick = this.handleClick.bind(this);
    this.updateUser = this.updateUser.bind(this);
  }
  
  // State update methods
  handleClick() {
    // 1. Direct update (wrong - doesn't merge)
    // this.state.count = this.state.count + 1;
    
    // 2. Using setState with object
    this.setState({ count: this.state.count + 1 });
    
    // 3. Using setState with function (when based on previous state)
    this.setState(prevState => ({
      count: prevState.count + 1
    }));
    
    // 4. Multiple state updates batched together
    this.setState({ loading: true });
    this.setState({ count: 10 });
    // React batches these and does single re-render
  }
  
  updateUser() {
    // Updating nested objects
    this.setState(prevState => ({
      user: {
        ...prevState.user, // Spread old properties
        age: prevState.user.age + 1 // Update specific property
      }
    }));
  }
  
  addItem() {
    // Updating arrays
    this.setState(prevState => ({
      items: [...prevState.items, 'New Item']
    }));
  }
  
  // Async setState callback
  incrementTwice() {
    this.setState(
      { count: this.state.count + 1 },
      () => {
        // Callback runs after state is updated
        console.log('State updated:', this.state.count);
        this.setState({ count: this.state.count + 1 });
      }
    );
  }
  
  render() {
    const { count, user, items, loading } = this.state;
    
    return (
      <div>
        <p>Count: {count}</p>
        <p>User: {user.name}, Age: {user.age}</p>
        <p>Items: {items.length}</p>
        <p>Loading: {loading.toString()}</p>
        
        <button onClick={this.handleClick}>
          Increment Count
        </button>
        <button onClick={this.updateUser}>
          Make Older
        </button>
        <button onClick={() => this.addItem()}>
          Add Item
        </button>
        <button onClick={() => this.incrementTwice()}>
          Increment Twice
        </button>
      </div>
    );
  }
}
```

### **19. State in Function-Based Components**
**Theory:** State using `useState` hook.

```jsx
import React, { useState } from 'react';

function FunctionState() {
  // Multiple state variables
  const [count, setCount] = useState(0);
  const [user, setUser] = useState({ name: 'John', age: 30 });
  const [items, setItems] = useState([]);
  const [loading, setLoading] = useState(false);
  
  // State update functions
  const handleClick = () => {
    // Direct update
    setCount(count + 1);
    
    // Functional update (when based on previous state)
    setCount(prevCount => prevCount + 1);
    
    // Multiple updates (not batched in React 17 without ReactDOM.unstable_batchedUpdates)
    setLoading(true);
    setCount(10);
  };
  
  const updateUser = () => {
    // Update nested object
    setUser(prevUser => ({
      ...prevUser,
      age: prevUser.age + 1
    }));
  };
  
  const addItem = () => {
    // Update array
    setItems(prevItems => [...prevItems, 'New Item']);
  };
  
  // Complex state (object with multiple properties)
  const [form, setForm] = useState({
    username: '',
    email: '',
    password: ''
  });
  
  const handleFormChange = (e) => {
    const { name, value } = e.target;
    setForm(prevForm => ({
      ...prevForm,
      [name]: value
    }));
  };
  
  // Lazy initial state
  const [expensiveState, setExpensiveState] = useState(() => {
    // This function runs only on initial render
    const expensiveValue = calculateExpensiveValue();
    return expensiveValue;
  });
  
  return (
    <div>
      <p>Count: {count}</p>
      <p>User: {user.name}, Age: {user.age}</p>
      <p>Items: {items.length}</p>
      <p>Loading: {loading.toString()}</p>
      
      <form>
        <input
          name="username"
          value={form.username}
          onChange={handleFormChange}
          placeholder="Username"
        />
        <input
          name="email"
          value={form.email}
          onChange={handleFormChange}
          placeholder="Email"
        />
      </form>
      
      <button onClick={handleClick}>
        Increment Count
      </button>
      <button onClick={updateUser}>
        Make Older
      </button>
      <button onClick={addItem}>
        Add Item
      </button>
    </div>
  );
}

// Helper function for lazy initialization
function calculateExpensiveValue() {
  console.log('Calculating expensive value...');
  // Simulate expensive calculation
  return Math.random();
}
```

## Redux Concepts

### **20. Redux Actions & Reducers**
**Theory:** Predictable state management pattern.

```jsx
// actionTypes.js
export const ADD_TODO = 'ADD_TODO';
export const TOGGLE_TODO = 'TOGGLE_TODO';
export const SET_FILTER = 'SET_FILTER';

// actions.js
export const addTodo = (text) => ({
  type: ADD_TODO,
  payload: { text }
});

export const toggleTodo = (id) => ({
  type: TOGGLE_TODO,
  payload: { id }
});

export const setFilter = (filter) => ({
  type: SET_FILTER,
  payload: { filter }
});

// Thunk action (async)
export const fetchTodos = () => {
  return async (dispatch) => {
    dispatch({ type: 'FETCH_TODOS_REQUEST' });
    
    try {
      const response = await fetch('/api/todos');
      const todos = await response.json();
      dispatch({ type: 'FETCH_TODOS_SUCCESS', payload: todos });
    } catch (error) {
      dispatch({ type: 'FETCH_TODOS_FAILURE', payload: error.message });
    }
  };
};

// reducers.js
const initialState = {
  todos: [],
  filter: 'ALL',
  loading: false,
  error: null
};

function todoReducer(state = initialState, action) {
  switch (action.type) {
    case 'ADD_TODO':
      return {
        ...state,
        todos: [
          ...state.todos,
          {
            id: Date.now(),
            text: action.payload.text,
            completed: false
          }
        ]
      };
      
    case 'TOGGLE_TODO':
      return {
        ...state,
        todos: state.todos.map(todo =>
          todo.id === action.payload.id
            ? { ...todo, completed: !todo.completed }
            : todo
        )
      };
      
    case 'SET_FILTER':
      return {
        ...state,
        filter: action.payload.filter
      };
      
    case 'FETCH_TODOS_REQUEST':
      return { ...state, loading: true, error: null };
      
    case 'FETCH_TODOS_SUCCESS':
      return { ...state, loading: false, todos: action.payload };
      
    case 'FETCH_TODOS_FAILURE':
      return { ...state, loading: false, error: action.payload };
      
    default:
      return state;
  }
}

// store.js
import { createStore, applyMiddleware, combineReducers } from 'redux';
import { composeWithDevTools } from 'redux-devtools-extension';
import thunk from 'redux-thunk';

const rootReducer = combineReducers({
  todos: todoReducer,
  // other reducers...
});

const store = createStore(
  rootReducer,
  composeWithDevTools(applyMiddleware(thunk))
);

// Component with Redux
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { addTodo, toggleTodo } from './actions';

function TodoApp() {
  const todos = useSelector(state => state.todos.todos);
  const filter = useSelector(state => state.todos.filter);
  const dispatch = useDispatch();
  
  const [input, setInput] = React.useState('');
  
  const handleSubmit = (e) => {
    e.preventDefault();
    if (input.trim()) {
      dispatch(addTodo(input));
      setInput('');
    }
  };
  
  const filteredTodos = todos.filter(todo => {
    if (filter === 'COMPLETED') return todo.completed;
    if (filter === 'ACTIVE') return !todo.completed;
    return true;
  });
  
  return (
    <div>
      <form onSubmit={handleSubmit}>
        <input
          value={input}
          onChange={e => setInput(e.target.value)}
          placeholder="Add todo..."
        />
        <button type="submit">Add</button>
      </form>
      
      <ul>
        {filteredTodos.map(todo => (
          <li
            key={todo.id}
            style={{
              textDecoration: todo.completed ? 'line-through' : 'none'
            }}
            onClick={() => dispatch(toggleTodo(todo.id))}
          >
            {todo.text}
          </li>
        ))}
      </ul>
    </div>
  );
}
```
