

### **1. JavaScript**
**Theory:** JavaScript is a single-threaded, prototype-based, multi-paradigm language with first-class functions. It uses just-in-time compilation and has a concurrency model based on an event loop.
```javascript
console.log("Hello World");
// JavaScript runs in browsers, servers (Node.js), mobile apps
```

### **2. Function Call**
**Theory:** When a function is called, a new execution context is created with its own variable environment, `this` binding, and reference to outer environment.
```javascript
function greet() { return "Hello"; }
greet(); // Call creates execution context
```

### **3. Method Call**
**Theory:** Methods are functions stored as object properties. When called, `this` is bound to the object.
```javascript
const obj = { name: "John", sayHi() { return this.name; } };
obj.sayHi(); // 'this' refers to obj
```

### **4. Identifiers, Rules**
**Theory:** Identifiers follow lexical grammar rules. Must start with Unicode letter, `$`, or `_`. Cannot be reserved words.
```javascript
let validName;   // ✓
let $variable;   // ✓
let _private;    // ✓
// let 123abc;   // ✗ (starts with number)
// let class;    // ✗ (reserved word)
```

### **5. Variables**
**Theory:** Variables are bindings between names and memory locations. JavaScript uses automatic memory management (garbage collection).
```javascript
let x = 10;      // Mutable, block-scoped
const y = 20;    // Immutable reference
var z = 30;      // Function-scoped (legacy)
```

### **6. Why JS is Dynamic-Type Programming Language**
**Theory:** Types are associated with values, not variables. Type checking happens at runtime, not compile time.
```javascript
let item = 42;      // Type: Number
item = "text";      // Type: String (reassigned)
item = true;        // Type: Boolean
// No compile-time type checking
```

### **7. Redeclaration, Rules**
**Theory:** Variable declarations are hoisted. `var` allows redeclaration in same scope; `let`/`const` don't (ES6 block scoping).
```javascript
var a = 1;
var a = 2;     // ✓ Allowed

let b = 1;
// let b = 2;  // ✗ SyntaxError

{
    let b = 3; // ✓ Different scope
}
```

### **8. Reinitialization, Rules**
**Theory:** Reassignment changes the value binding. `const` prevents reassignment but not mutation.
```javascript
let x = 10;
x = 20;        // ✓ Reassignment allowed

const y = 30;
// y = 40;     // ✗ TypeError

const obj = {};
obj.name = "John"; // ✓ Mutation allowed
// obj = {};       // ✗ Reassignment not allowed
```

### **9. Strict Mode**
**Theory:** Enables strict variant of JavaScript that eliminates silent errors and makes optimizations possible.
```javascript
"use strict";
x = 10;                     // ReferenceError (undeclared)
delete Object.prototype;    // TypeError
function dup(a, a) {}       // SyntaxError (duplicate params)
```

### **10. Datatypes, Types of Datatypes**
**Theory:** Primitive types are immutable and stored by value. Reference types are mutable and stored by reference.
```javascript
// PRIMITIVE (7 types)
let str = "text";     // String
let num = 42;         // Number
let bool = true;      // Boolean
let n = null;         // Null (intentional absence)
let u = undefined;    // Undefined (uninitialized)
let sym = Symbol();   // Symbol (unique)
let big = 123n;       // BigInt

// REFERENCE (Objects)
let obj = {x: 1};     // Object
let arr = [1, 2];     // Array
let func = () => {};  // Function
```

### **11. Type Conversion**
**Theory:** Explicit type conversion using built-in functions or operators.
```javascript
let str = "123";
Number(str);          // 123 (explicit)
parseInt(str);        // 123
+str;                 // 123 (unary plus)

let num = 456;
String(num);          // "456"
num.toString();       // "456"
num + "";             // "456"
```

### **12. Type Coercion**
**Theory:** Automatic/implicit conversion during operations. Follows Abstract Operations in ECMAScript spec.
```javascript
5 + "5"           // "55" (ToString)
"5" * 2           // 10 (ToNumber)
if ("hello") {}   // true (ToBoolean)
null == undefined // true (Special rule)
```

### **13. Operators, Types**
**Theory:** Operators are functions with special syntax. Follow precedence and associativity rules.
```javascript
// Arithmetic: + - * / % **
// Comparison: == === != !== > < >= <=
// Logical: && || ! ??
// Assignment: = += -= *= /=
// Bitwise: & | ^ ~ << >> >>>
// typeof, instanceof, in, delete

10 + 5 * 2      // 20 (precedence)
let x = y = 5;  // Right-to-left associativity
```

### **14. Operations Performed Using +**
**Theory:** `+` operator is overloaded. Performs addition or concatenation based on operand types.
```javascript
5 + 3           // 8 (numeric addition)
"Hello" + "World" // "HelloWorld" (concatenation)
5 + "5"         // "55" (coercion to string)
+ "10"          // 10 (unary: convert to number)
```

### **15. Template String**
**Theory:** Template literals allow embedded expressions. They're syntactic sugar over string concatenation.
```javascript
let name = "John";
let age = 30;
`Hello ${name}, you are ${age} years old`;
// Equivalent to: "Hello " + name + ", you are " + age + " years old"
```

### **16. prompt**
**Theory:** Synchronous function that blocks execution. Returns string or null.
```javascript
let name = prompt("Enter name:");
// Execution stops until user responds
// Returns string or null if cancelled
```

### **17. Truthy and Falsy Values**
**Theory:** All values coerce to `true` or `false` in boolean contexts based on ToBoolean conversion.
```javascript
// FALSY: false, 0, -0, 0n, "", null, undefined, NaN
// TRUTHY: Everything else

if ("hello") {}      // true
if (0) {}           // false
if ([]) {}          // true (empty array)
if ({}) {}          // true (empty object)
```

### **18. Postfix / Prefix**
**Theory:** Both modify the variable. Difference is in when they return the value.
```javascript
let x = 5;
let a = x++;  // Postfix: return 5, then increment to 6
let b = ++x;  // Prefix: increment to 7, then return 7
// x is now 7
```

### **19. Short Circuit Evaluation**
**Theory:** Logical operators don't evaluate right operand if result is determined by left.
```javascript
false && anything()  // false (right never evaluated)
true || anything()   // true (right never evaluated)
null ?? defaultValue // Uses defaultValue (null/undefined only)
```

### **20. Conditional Statement**
**Theory:** Control flow based on boolean evaluation. Creates different execution paths.
```javascript
if (condition) {
    // Executes if true
} else if (condition2) {
    // Executes if condition2 true
} else {
    // Default case
}
```

### **21. Looping Statements**
**Theory:** Repeated execution based on condition. Each creates its own iteration scope.
```javascript
for (let i = 0; i < 5; i++) {}    // Known iterations
while (condition) {}              // Condition-based
do {} while (condition);          // Always runs once
for (let item of array) {}        // Iterable values
for (let key in object) {}        // Enumerable properties
```

### **22. break**
**Theory:** Terminates the current loop or switch statement. Transfers control to following statement.
```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) break;  // Exit loop completely
}
// Continues here after break
```

### **23. continue**
**Theory:** Skips the rest of current iteration and continues with next.
```javascript
for (let i = 0; i < 5; i++) {
    if (i === 2) continue; // Skip iteration when i is 2
    console.log(i);        // 0, 1, 3, 4
}
```

### **24. return**
**Theory:** Terminates function execution and returns value to caller.
```javascript
function add(a, b) {
    return a + b;  // Returns value, ends function
    console.log("Unreachable");
}
```

### **25. Functions, Types of Function**
**Theory:** Functions are first-class objects with internal `[[Call]]` property.
```javascript
function declaration() {}          // Hoisted
const expression = function() {};  // Not hoisted
const arrow = () => {};            // No 'this' binding
(function() {})();                 // IIFE
function* generator() { yield 1; } // Generator
async function asyncFunc() {}      // Async
```

### **26. IIFE**
**Theory:** Immediately creates and executes function. Creates private scope.
```javascript
(function() {
    // Private scope
    let private = "secret";
})();
// private not accessible here
```

### **27. Unreachable Statement**
**Theory:** Code that cannot be executed due to control flow. Considered dead code.
```javascript
function test() {
    return;
    console.log("Never runs"); // Unreachable
}

if (false) {
    console.log("Never runs"); // Unreachable
}
```

### **28. Function with Parameters, Types**
**Theory:** Parameters create local variables in function scope.
```javascript
function fn(a, b = "default") {}     // Default parameter
function sum(...numbers) {}           // Rest parameters
function destr({x, y}) {}             // Destructuring
function old() { arguments[0]; }      // Arguments object
```

### **29. Higher Order Function**
**Theory:** Functions that operate on other functions (take as arguments or return them).
```javascript
function higherOrder(fn) {
    return function(...args) {
        return fn(...args);
    };
}
```

### **30. Callback Function**
**Theory:** Function passed as argument to be called later (synchronously or asynchronously).
```javascript
function process(data, callback) {
    // Do work
    callback(result);
}
```

### **31. JS Runtime Environment**
**Theory:** Includes engine, Web APIs, callback queue, event loop. Manages execution.
```javascript
// Engine: V8 (Chrome), SpiderMonkey (Firefox)
// APIs: DOM, setTimeout, fetch
// Event Loop: Manages async operations
```

### **32. Object**
**Theory:** Collection of properties (key-value pairs). Based on prototype inheritance.
```javascript
const obj = {
    key: "value",
    method() { return this.key; }
};
```

### **33. Two Ways to Create Object**
**Theory:** Object literal syntax and constructor function/Object.create.
```javascript
const literal = {};                  // Direct
const constructed = new Object();    // Via constructor
const fromPrototype = Object.create(proto);
```

### **34. Bracket Notation**
**Theory:** Allows dynamic/computed property access. Evaluates expression inside brackets.
```javascript
obj["property"];          // Static key
obj[variable];            // Dynamic key
obj["property name"];     // With spaces
```

### **35. Dot Notation**
**Theory:** Static property access. Identifier must be valid.
```javascript
obj.property;    // Simple access
obj.method();    // Method call
// obj.property name // Invalid (space)
```

### **36. Call Stack**
**Theory:** LIFO structure tracking execution contexts. Limited size.
```javascript
function a() { b(); }
function b() { c(); }
function c() { console.trace(); }
a(); // Shows call stack: c <- b <- a <- global
```

### **37. Global Execution Context**
**Theory:** Base context created when script starts. Contains global object binding.
```javascript
// In browser:
console.log(this === window);  // true
var globalVar = 1;
console.log(window.globalVar); // 1
```

### **38. JavaScript Runtime Environment**
**Theory:** Complete system: Heap (memory), Stack (execution), Web APIs, Event Loop.
```javascript
// Execution flow:
// 1. Call stack executes synchronous code
// 2. Web APIs handle async operations
// 3. Callback queue holds completed async tasks
// 4. Event loop pushes callbacks to stack
```

### **39. Variable Object**
**Theory:** In ES3, stores variables in execution context. In ES5+, replaced by lexical environment.
```javascript
function test() {
    var a = 1;      // Stored in variable object
    function b() {} // Also stored
    // During creation: a = undefined, b = function
    // During execution: a = 1
}
```

### **40. Array**
**Theory:** Object with integer keys and special length property. Inherits from Array.prototype.
```javascript
const arr = [1, 2, 3];
console.log(arr.length);      // 3
console.log(arr[0]);          // 1
console.log(Array.isArray(arr)); // true
```

### **41. JIT (Just-In-Time Compilation)**
**Theory:** Modern JS engines compile hot code to machine code for optimization.
```javascript
// V8 engine:
// 1. Interpreter (Ignition) executes code
// 2. Profiler identifies hot functions
// 3. Compiler (TurboFan) optimizes hot code
// 4. Deoptimizes if assumptions fail
```

### **42. Lexical Environment**
**Theory:** Data structure holding identifier-variable mapping. Determined by code structure.
```javascript
function outer() {
    let x = 10;           // Outer lexical environment
    function inner() {
        console.log(x);   // Inner can access outer's environment
    }
    return inner;
}
```

### **43. Closure**
**Theory:** Function + reference to its lexical environment. Allows function to access outer scope after outer function returns.
```javascript
function createCounter() {
    let count = 0;        // Captured in closure
    return function() {
        return ++count;
    };
}
const counter = createCounter();
counter(); // 1 (accesses count)
counter(); // 2
```

### **44. Hoisting**
**Theory:** During compilation, declarations are moved to top of scope. Variables initialized to `undefined`.
```javascript
console.log(x); // undefined (not error)
var x = 5;

// Actually processed as:
// var x;
// console.log(x);
// x = 5;
```

### **45. TDZ (Temporal Dead Zone)**
**Theory:** Area from start of block to `let`/`const` declaration where variable cannot be accessed.
```javascript
{
    // Start of TDZ for x
    console.log(x); // ReferenceError (TDZ)
    let x = 10;     // End of TDZ
    console.log(x); // 10
}
```

### **46. Scopes – Types of Scope**
**Theory:** Scope determines visibility of variables. Created by functions, blocks, or modules.
```javascript
// 1. Global Scope
let global = 1;

function outer() {
    // 2. Function Scope
    let outerVar = 2;
    
    if (true) {
        // 3. Block Scope (ES6)
        let blockVar = 3;
    }
    
    // 4. Module Scope (ES6 modules)
    // export/import create module scope
}

// 5. Lexical Scope: Determined by where code is written
// 6. Dynamic Scope: this binding (determined by how called)
```

### **47. var**
**Theory:** Function-scoped or globally-scoped. Hoisted and initialized with `undefined`.
```javascript
function test() {
    console.log(x); // undefined (hoisted)
    var x = 10;
    if (true) {
        var y = 20; // Same variable (no block scope)
    }
    console.log(y); // 20 (accessible)
}
```

### **48. let**
**Theory:** Block-scoped. Hoisted but not initialized (TDZ). Cannot be redeclared in same scope.
```javascript
{
    console.log(x); // ReferenceError (TDZ)
    let x = 10;
    
    if (true) {
        let y = 20; // Different variable
    }
    console.log(y); // ReferenceError (block-scoped)
}
```

### **49. const**
**Theory:** Block-scoped constant. Must be initialized. Reference cannot change, but object properties can.
```javascript
const PI = 3.14;
// PI = 3.1415; // TypeError

const obj = { name: "John" };
obj.name = "Jane"; // ✓ Allowed (mutation)
// obj = {};     // ✗ Not allowed (reassignment)
```

### **50. First Class Function**
**Theory:** Functions can be assigned to variables, passed as arguments, returned from functions.
```javascript
const add = function(a, b) { return a + b; }; // Assign
function operate(fn, a, b) { return fn(a, b); } // Pass
function createMultiplier(n) { // Return
    return function(x) { return x * n; };
}
```

### **51. this Keyword**
**Theory:** Determined by how function is called: global, method, constructor, explicit binding, arrow functions.
```javascript
console.log(this);            // global/window

const obj = {
    name: "John",
    greet() {
        console.log(this.name); // obj (method call)
    }
};

function Person(name) {
    this.name = name;        // new object (constructor)
}

const arrow = () => {
    console.log(this);       // Lexical this (from outer scope)
};
```

### **52. Function Constructor**
**Theory:** Creates function from string code. Similar to `eval()` but creates function in global scope.
```javascript
const add = new Function('a', 'b', 'return a + b');
console.log(add(2, 3)); // 5
// Creates function with given parameters and body
```

### **53. Prototype**
**Theory:** Object shared by all instances. Used for property/method inheritance.
```javascript
function Person(name) {
    this.name = name;
}
Person.prototype.greet = function() {
    return `Hello, ${this.name}`;
};

const john = new Person("John");
john.greet(); // Looks up prototype chain
```

### **54. Prototypal Chaining**
**Theory:** Mechanism where objects inherit from other objects via prototype chain.
```javascript
const parent = { x: 1 };
const child = Object.create(parent);
child.y = 2;

console.log(child.x); // 1 (from prototype)
console.log(child.y); // 2 (own property)

// Chain: child -> parent -> Object.prototype -> null
```

### **55. Inheritance**
**Theory:** ES5 used constructor functions + prototypes. ES6 added `class` syntax (syntactic sugar).
```javascript
// ES5 Inheritance
function Animal(name) {
    this.name = name;
}
Animal.prototype.speak = function() {
    console.log(`${this.name} makes a sound`);
};

function Dog(name) {
    Animal.call(this, name);
}
Dog.prototype = Object.create(Animal.prototype);

// ES6 Inheritance
class Animal {
    constructor(name) { this.name = name; }
    speak() { console.log(`${this.name} makes a sound`); }
}
class Dog extends Animal {
    bark() { console.log("Woof!"); }
}
```

### **56. Scope Chaining**
**Theory:** When variable is referenced, JavaScript looks up chain of lexical environments.
```javascript
let global = "global";

function outer() {
    let outerVar = "outer";
    
    function inner() {
        let innerVar = "inner";
        console.log(innerVar);  // inner (current scope)
        console.log(outerVar);  // outer (parent scope)
        console.log(global);    // global (global scope)
    }
    
    inner();
}
```

### **57. Function Methods, Types**
**Theory:** Functions are objects with methods: `call`, `apply`, `bind` for `this` binding.
```javascript
function greet(greeting) {
    return `${greeting}, ${this.name}`;
}

const person = { name: "John" };

greet.call(person, "Hello");    // Hello, John
greet.apply(person, ["Hi"]);    // Hi, John
const bound = greet.bind(person, "Hey");
bound();                        // Hey, John
```

### **58. Function Overloading**
**Theory:** JavaScript doesn't support overloading natively. Simulated with argument checking.
```javascript
function process() {
    if (arguments.length === 1) {
        // Handle one argument
    } else if (arguments.length === 2) {
        // Handle two arguments
    }
}

// Modern approach
function process(data, options = {}) {
    // Default options handle different cases
}
```

### **59. Ways to Write Array**
**Theory:** Multiple constructors for creating arrays.
```javascript
const arr1 = [1, 2, 3];                 // Literal
const arr2 = new Array(1, 2, 3);        // Constructor
const arr3 = Array.of(1, 2, 3);         // ES6
const arr4 = Array.from("123");         // From iterable
const arr5 = new Array(5);              // Length 5
const arr6 = Array.from({length: 5}, (_, i) => i);
```

### **60. Recursion**
**Theory:** Function calls itself with modified parameters until base case is reached.
```javascript
function factorial(n) {
    if (n <= 1) return 1;       // Base case
    return n * factorial(n - 1); // Recursive case
}
// Stack: factorial(3) -> factorial(2) -> factorial(1)
// Returns: 1 -> 2 -> 6
```

### **61. Principles of OOPs**
**Theory:** Four pillars of object-oriented programming.
```javascript
// 1. ENCAPSULATION: Bundling data and methods
class BankAccount {
    #balance = 0;               // Private field
    deposit(amount) {
        this.#balance += amount;
    }
}

// 2. ABSTRACTION: Hide complexity
class Car {
    start() { /* Complex ignition process */ }
    // User just calls car.start()
}

// 3. INHERITANCE: Reuse code
class Animal {}
class Dog extends Animal {}

// 4. POLYMORPHISM: Same interface, different implementation
class Shape {
    area() { throw new Error("Abstract"); }
}
class Circle extends Shape {
    area() { return Math.PI * this.radius ** 2; }
}
class Square extends Shape {
    area() { return this.side ** 2; }
}
```

### **62. Pure and Impure Functions**
**Theory:** Pure functions don't cause side effects and return same output for same input.
```javascript
// PURE: No side effects, deterministic
function add(a, b) {
    return a + b;               // Same result always
}

// IMPURE: Side effects or non-deterministic
let counter = 0;
function increment() {
    counter++;                  // Side effect
    return Math.random();       // Non-deterministic
}

function impureAdd(a, b) {
    console.log(a + b);         // Side effect (logging)
    return a + b;
}
```

### **63. DOM (Document Object Model)**
**Theory:** Tree representation of HTML document. Provides API for manipulation.
```javascript
document;                      // Root of DOM tree
document.documentElement;      // <html> element
document.body;                 // <body> element
document.head;                 // <head> element
```

### **64. DOM Methods**
**Theory:** Methods for traversing and manipulating DOM tree.
```javascript
document.getElementById('id');
document.querySelector('.class');
document.querySelectorAll('p');
document.createElement('div');
element.appendChild(child);
element.removeChild(child);
element.replaceChild(new, old);
```

### **65. JavaScript Events**
**Theory:** Event-driven programming model. Events bubble up from target to root.
```javascript
// Event types: click, submit, keydown, load, etc.
// Event phases: Capture -> Target -> Bubbling
// Event object contains event details
```

### **66. Event Handling**
**Theory:** Registering functions to respond to events.
```javascript
// Three methods:
element.onclick = handler;           // Property
element.addEventListener('click', handler); // Modern
<button onclick="handler()">Click</button> // Inline
```

### **67. Event Handler**
**Theory:** Function executed when event occurs. Receives event object parameter.
```javascript
function handleClick(event) {
    console.log(event.type);        // "click"
    console.log(event.target);      // Element clicked
    console.log(event.currentTarget); // Element with handler
}
```

### **68. Event Property**
**Theory:** Properties on event object provide event details.
```javascript
event.preventDefault();     // Cancel default action
event.stopPropagation();    // Stop bubbling
event.stopImmediatePropagation(); // Stop other handlers
event.target;               // Element that triggered
event.currentTarget;        // Element with handler
event.type;                 // Event type
event.clientX, event.clientY; // Mouse position
event.key;                  // Key pressed
```

### **69. Web Storage**
**Theory:** Key-value storage in browser. `localStorage` persists, `sessionStorage` clears on tab close.
```javascript
localStorage.setItem('key', 'value');
const value = localStorage.getItem('key');
localStorage.removeItem('key');
localStorage.clear();

// Stores strings only
localStorage.setItem('obj', JSON.stringify({x: 1}));
JSON.parse(localStorage.getItem('obj'));
```

### **70. addEventListener**
**Theory:** Modern way to attach event handlers. Allows multiple handlers per event.
```javascript
element.addEventListener('click', handler, options);
// options: {capture, once, passive}

// Can add multiple handlers
element.addEventListener('click', handler1);
element.addEventListener('click', handler2);

// Remove with removeEventListener
element.removeEventListener('click', handler1);
```

### **71. textContent**
**Theory:** Gets/sets text content of element and descendants. More performant than `innerText`.
```javascript
element.textContent = "New text";
// Sets raw text (escapes HTML)
// Includes hidden elements
// Faster than innerText
```

### **72. innerText**
**Theory:** Gets/sets rendered text content. Respects CSS styling.
```javascript
element.innerText = "Text";
// Gets only visible text
// Respects CSS (excludes hidden)
// Triggers reflow (slower)
// Not standard originally (IE)
```

### **73. innerHTML**
**Theory:** Gets/sets HTML content. Parses HTML string into DOM elements.
```javascript
element.innerHTML = "<strong>Bold</strong>";
// Parses HTML
// Security risk with user input
// Use textContent for plain text
```

### **74. Attribute Methods**
**Theory:** DOM elements have attributes (HTML) and properties (JavaScript object).
```javascript
element.setAttribute('id', 'myId');
element.getAttribute('id');
element.removeAttribute('id');
element.hasAttribute('id');

// HTML attributes vs DOM properties
element.setAttribute('disabled', ''); // HTML attribute
element.disabled = true;              // DOM property
```

### **75. classList**
**Theory`: `DOMTokenList` object for manipulating CSS classes.
```javascript
element.classList.add('active');
element.classList.remove('active');
element.classList.toggle('active');
element.classList.contains('active');
element.classList.replace('old', 'new');
```

### **76. filter Method**
**Theory:** Creates new array with elements that pass test. Doesn't mutate original.
```javascript
const numbers = [1, 2, 3, 4, 5];
const evens = numbers.filter(n => n % 2 === 0);
// evens = [2, 4]
// numbers unchanged
```

### **77. JSON**
**Theory:** Text-based data format. `JSON.stringify()` converts to string, `JSON.parse()` converts from string.
```javascript
const obj = { name: "John", age: 30 };
const json = JSON.stringify(obj);    // '{"name":"John","age":30}'
const parsed = JSON.parse(json);     // {name: "John", age: 30}

// Replacer/reviver functions
JSON.stringify(obj, (key, value) => {
    return key === 'age' ? undefined : value;
});

// Space parameter for formatting
JSON.stringify(obj, null, 2);
```

### **78. push**
**Theory:** Adds elements to end of array. Mutates original array.
```javascript
const arr = [1, 2];
arr.push(3, 4);      // Returns new length (4)
// arr = [1, 2, 3, 4]
```

### **79. pop**
**Theory:** Removes last element from array. Mutates original array.
```javascript
const arr = [1, 2, 3];
const last = arr.pop(); // Returns 3
// arr = [1, 2]
```

### **80. unshift**
**Theory:** Adds elements to beginning of array. Mutates original array.
```javascript
const arr = [2, 3];
arr.unshift(1);      // Returns new length (3)
// arr = [1, 2, 3]
```

### **81. shift**
**Theory:** Removes first element from array. Mutates original array.
```javascript
const arr = [1, 2, 3];
const first = arr.shift(); // Returns 1
// arr = [2, 3]
```

### **82. find**
**Theory:** Returns first element that satisfies condition. Returns `undefined` if none found.
```javascript
const users = [
    { id: 1, name: "John" },
    { id: 2, name: "Jane" }
];
const user = users.find(u => u.id === 2);
// user = { id: 2, name: "Jane" }
```

### **83. sort**
**Theory:** Sorts array in place. Default converts elements to strings and compares UTF-16 code units.
```javascript
const numbers = [3, 1, 2];
numbers.sort();                // [1, 2, 3] (as strings)
numbers.sort((a, b) => a - b); // [1, 2, 3] (numeric)

// Returns reference to same array
```

### **84. search**
**Theory:** String method that searches for regex match. Returns index or -1.
```javascript
const str = "Hello World";
str.search("World");        // 6
str.search(/world/i);       // 6 (case-insensitive)
str.search("Not found");    // -1
```

### **85. category**
**Theory:** Not a standard JavaScript concept. May refer to data classification or grouping.

### **86. Shallow Copy**
**Theory:** Copies top-level properties only. Nested objects are shared references.
```javascript
const original = { a: 1, b: { c: 2 } };
const shallow = { ...original }; // Spread operator
// or Object.assign({}, original)

shallow.b.c = 99;
console.log(original.b.c); // 99 (shared reference)
```

### **87. Deep Copy**
**Theory:** Copies all nested objects recursively. No shared references.
```javascript
const original = { a: 1, b: { c: 2 } };
const deep = JSON.parse(JSON.stringify(original));

deep.b.c = 99;
console.log(original.b.c); // 2 (unchanged)

// Limitations:
// - Doesn't copy functions, undefined, symbols
// - Circular references cause error
// - Loses object prototypes
```

### **88. Rest Parameter/Operator**
**Theory:** Collects remaining arguments into array. Must be last parameter.
```javascript
function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3, 4); // 10

function fn(first, second, ...rest) {
    // rest collects remaining arguments
}
```

### **89. Spread**
**Theory:** Expands iterable into individual elements.
```javascript
const arr1 = [1, 2];
const arr2 = [3, 4];
const combined = [...arr1, ...arr2]; // [1, 2, 3, 4]

const obj1 = { a: 1 };
const obj2 = { b: 2 };
const merged = { ...obj1, ...obj2 }; // { a: 1, b: 2 }

fn(...args); // Spread arguments
```

### **90. Synchronous**
**Theory:** Code executes sequentially, line by line.
```javascript
console.log("First");
console.log("Second"); // Waits for First
console.log("Third");  // Waits for Second
```

### **91. Asynchronous**
**Theory:** Code doesn't wait for operations to complete. Uses callbacks, promises, async/await.
```javascript
console.log("Start");
setTimeout(() => console.log("Timeout"), 0);
Promise.resolve().then(() => console.log("Promise"));
console.log("End");
// Output: Start, End, Promise, Timeout
```

### **92. setTimeout**
**Theory:** Schedules function to run after delay (minimum time, not guaranteed).
```javascript
setTimeout(() => {
    console.log("Runs after at least 1000ms");
}, 1000);

const id = setTimeout(handler, delay);
clearTimeout(id); // Cancel before execution
```

### **93. setInterval**
**Theory:** Repeatedly executes function at specified intervals.
```javascript
const id = setInterval(() => {
    console.log("Runs every 1000ms");
}, 1000);

clearInterval(id); // Stop execution
```

### **94. AJAX**
**Theory:** Asynchronous JavaScript and XML. Technique for async HTTP requests.
```javascript
const xhr = new XMLHttpRequest();
xhr.open('GET', '/api/data', true);
xhr.onload = function() {
    if (xhr.status === 200) {
        console.log(xhr.responseText);
    }
};
xhr.send();
```

### **95. Promise Methods**
**Theory:** Promise is object representing eventual completion/failure of async operation.
```javascript
// Creation
const promise = new Promise((resolve, reject) => {
    // Async operation
    if (success) resolve(value);
    else reject(error);
});

// Consumption
promise
    .then(value => { /* handle success */ })
    .catch(error => { /* handle error */ })
    .finally(() => { /* always runs */ });

// Static methods
Promise.all([p1, p2]);       // Wait for all
Promise.race([p1, p2]);      // First to settle
Promise.allSettled([p1, p2]);// All settled
Promise.any([p1, p2]);       // First to fulfill
```

### **96. Destructuring**
**Theory:** Extract values from arrays or properties from objects into distinct variables.
```javascript
// Array destructuring
const [a, b] = [1, 2];       // a=1, b=2
const [first, ...rest] = [1, 2, 3]; // first=1, rest=[2,3]

// Object destructuring
const { name, age } = { name: "John", age: 30 };
const { name: userName } = obj; // Renaming
```

### **97. Object Destructuring**
**Theory:** Extract object properties into variables.
```javascript
const user = { id: 1, name: "John", age: 30 };

const { name, age } = user;          // name="John", age=30
const { name: userName } = user;     // userName="John"
const { city = "NYC" } = user;       // Default value

// Nested destructuring
const { address: { city } } = user;
```

### **98. Array Destructuring**
**Theory:** Extract array elements into variables.
```javascript
const colors = ["red", "green", "blue"];

const [first, second] = colors;      // first="red", second="green"
const [primary, , tertiary] = colors;// primary="red", tertiary="blue"
const [firstColor, ...others] = colors; // firstColor="red", others=["green","blue"]

// Swapping variables
let a = 1, b = 2;
[a, b] = [b, a]; // a=2, b=1
```

### **99. Promise vs setTimeout (Microtask vs Macrotask)**
**Theory:** Event loop prioritizes microtasks (promises) over macrotasks (setTimeout).
```javascript
console.log("Script start");

setTimeout(() => {
    console.log("setTimeout"); // Macrotask
}, 0);

Promise.resolve().then(() => {
    console.log("Promise 1");  // Microtask
}).then(() => {
    console.log("Promise 2");  // Microtask
});

console.log("Script end");

// Output order:
// Script start
// Script end
// Promise 1
// Promise 2
// setTimeout
```

### **100. Fetch API**
**Theory:** Modern replacement for XMLHttpRequest. Returns Promise.
```javascript
fetch('https://api.example.com/data')
    .then(response => {
        if (!response.ok) throw new Error('Network error');
        return response.json(); // Parse JSON
    })
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));

// With async/await
async function getData() {
    try {
        const response = await fetch(url);
        const data = await response.json();
        return data;
    } catch (error) {
        console.error(error);
    }
}
```

### **101. Babel (JS Compiler/Transpiler)**
**Theory:** Transpiles modern JavaScript to older versions for browser compatibility.
```javascript
// Input (ES2020)
const obj = { a: 1 };
const { a } = obj;
const spread = { ...obj };

// Output (ES5) after Babel
"use strict";
var obj = { a: 1 };
var a = obj.a;
var spread = Object.assign({}, obj);
```

### **102. Async/Await**
**Theory:** Syntactic sugar over promises. Makes async code look synchronous.
```javascript
async function getUserData(userId) {
    try {
        const user = await fetchUser(userId);
        const posts = await fetchPosts(user.id);
        return { user, posts };
    } catch (error) {
        console.error("Failed:", error);
        throw error;
    }
}

// Async function always returns Promise
// await can only be used in async functions
// Error handling with try/catch
```

### **103. Map**
**Theory:** Collection of key-value pairs. Keys can be any value (objects, functions).
```javascript
const map = new Map();
map.set('key', 'value');
map.set({}, 'object key');
map.set(() => {}, 'function key');

console.log(map.get('key')); // 'value'
console.log(map.size);       // 3

for (let [key, value] of map) {
    console.log(key, value);
}
```

### **104. Set**
**Theory:** Collection of unique values. No duplicates allowed.
```javascript
const set = new Set([1, 2, 3, 3, 2]);
console.log(set.size); // 3 (duplicates removed)

set.add(4);
set.add(4); // No effect (already exists)
set.has(3); // true
set.delete(2);

for (let value of set) {
    console.log(value); // 1, 3, 4
}
```

### **105. for...of**
**Theory:** Iterates over iterable objects (arrays, strings, maps, sets, etc.).
```javascript
const arr = [1, 2, 3];
for (let value of arr) {
    console.log(value); // 1, 2, 3
}

const str = "hello";
for (let char of str) {
    console.log(char); // h, e, l, l, o
}

// Works with any object implementing [Symbol.iterator]
```

### **106. for...in**
**Theory:** Iterates over enumerable properties of an object (including inherited ones).
```javascript
const obj = { a: 1, b: 2, c: 3 };
for (let key in obj) {
    console.log(key, obj[key]); // a 1, b 2, c 3
}

// Includes inherited enumerable properties
Array.prototype.custom = function() {};
const arr = [1, 2, 3];
for (let index in arr) {
    console.log(index); // 0, 1, 2, "custom" (inherited!)
}
```

### **107. forEach**
**Theory:** Array method that executes callback for each element. Cannot break/return.
```javascript
const arr = [1, 2, 3];
arr.forEach((value, index, array) => {
    console.log(value, index);
});

// No way to break early
// Returns undefined (not chainable)
// Generally use for...of for more control
```

### **108. try...catch...finally**
**Theory:** Error handling mechanism. `finally` always executes.
```javascript
try {
    // Code that might throw
    riskyOperation();
    console.log("Success");
} catch (error) {
    // Handle error
    console.error("Caught:", error.message);
} finally {
    // Always executes
    console.log("Cleanup");
    // Even if return/throw in try/catch
}
```

### **109. splice Method**
**Theory:** Changes array by removing/replacing elements and/or adding new elements.
```javascript
const arr = [1, 2, 3, 4, 5];

// Remove 2 elements starting from index 1
const removed = arr.splice(1, 2); // arr = [1, 4, 5], removed = [2, 3]

// Insert at index 1
arr.splice(1, 0, 'a', 'b'); // arr = [1, 'a', 'b', 4, 5]

// Replace 1 element at index 3 with 3 elements
arr.splice(3, 1, 'x', 'y', 'z'); // arr = [1, 'a', 'b', 'x', 'y', 'z', 5]
```

### **110. slice Method**
**Theory:** Returns shallow copy of portion of array. Doesn't modify original.
```javascript
const arr = [1, 2, 3, 4, 5];

arr.slice(2);      // [3, 4, 5] (from index 2 to end)
arr.slice(1, 4);   // [2, 3, 4] (index 1 to 3)
arr.slice(-2);     // [4, 5] (last 2 elements)
arr.slice(1, -1);  // [2, 3, 4] (index 1 to second-last)

// Original unchanged: [1, 2, 3, 4, 5]
```

### **111. join Method**
**Theory:** Creates string by concatenating all array elements with separator.
```javascript
const arr = ['Hello', 'World', '!'];

arr.join();      // "Hello,World,!" (default comma)
arr.join(' ');   // "Hello World !"
arr.join('-');   // "Hello-World-!"
arr.join('');    // "HelloWorld!"

// With non-array values
[1, null, undefined, 2].join(); // "1,,,2"
```

### **112. Array.isArray()**
**Theory:** Determines if value is an array. More reliable than `typeof` or `instanceof`.
```javascript
Array.isArray([]);           // true
Array.isArray([1, 2, 3]);    // true
Array.isArray(new Array());  // true
Array.isArray(Array.prototype); // true

Array.isArray({});           // false
Array.isArray(null);         // false
Array.isArray(undefined);    // false
Array.isArray('array');      // false

// Why not typeof?
typeof []; // "object" (not helpful)
```

### **113. reduce Method**
**Theory:** Executes reducer function on each element, resulting in single output value.
```javascript
const numbers = [1, 2, 3, 4];

// Sum of array
const sum = numbers.reduce((accumulator, currentValue) => {
    return accumulator + currentValue;
}, 0); // Start with 0
// sum = 10

// Flatten array
const nested = [[1, 2], [3, 4], [5]];
const flat = nested.reduce((acc, curr) => acc.concat(curr), []);
// flat = [1, 2, 3, 4, 5]

// Group by property
const people = [
    { name: 'Alice', age: 21 },
    { name: 'Bob', age: 21 },
    { name: 'Charlie', age: 25 }
];
const grouped = people.reduce((acc, person) => {
    const age = person.age;
    if (!acc[age]) acc[age] = [];
    acc[age].push(person);
    return acc;
}, {});
// grouped = {21: [{...}, {...}], 25: [{...}]}
```

### **114. reduceRight Method**
**Theory:** Same as `reduce()` but processes array from right to left.
```javascript
const arr = ['H', 'e', 'l', 'l', 'o'];

// Reverse string
const reversed = arr.reduceRight((acc, char) => acc + char, '');
// reversed = "olleH"

// Compare with reduce (left to right)
const normal = arr.reduce((acc, char) => acc + char, '');
// normal = "Hello"

// Useful for right-associative operations
const operations = [
    (x) => x + 1,
    (x) => x * 2,
    (x) => x - 3
];
const result = operations.reduceRight((acc, fn) => fn(acc), 5);
// Executes: ((5 - 3) * 2) + 1 = 5
```
