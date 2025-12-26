## 1. JavaScript

```js
console.log("Hello JavaScript!");
```

---

## 2. Function Call

```js
function greet() {
  console.log("Hello!");
}
greet();
```

---

## 3. Method Call

```js
const person = {
  name: "Prashanth",
  sayName() {
    console.log(this.name);
  },
};
person.sayName();
```

---

## 4. Identifiers (Rules)

```js
let myName = "Prashanth"; // ✅ valid
// let 123abc = "error"; ❌ invalid
```

---

## 5. Variables

```js
var a = 10; // function-scoped
let b = 20; // block-scoped
const c = 30; // constant
```

---

## 6. Dynamic Typing

```js
let x = 10; // number
x = "Hello"; // string
x = true; // boolean
```

---

## 7. Redeclaration

```js
var a = 5;
var a = 10; // ✅ allowed

let b = 20;
// let b = 30; ❌ Error
```

---

## 8. Reinitialization

```js
let x = 10;
x = 20; // ✅ allowed

const y = 30;
// y = 40; ❌ Error
```

---

## 9. Strict Mode

```js
"use strict";
x = 10; // ❌ Error: must declare
```

---

## 10. Datatypes

```js
let num = 10; // number
let str = "Hello"; // string
let bool = true; // boolean
let undef; // undefined
let n = null; // null
let sym = Symbol(); // symbol
let big = 123n; // bigint
```

---

## 11. Type Conversion

```js
let str = "123";
let num = Number(str); // 123
```

---

## 12. Type Coercion

```js
console.log("5" + 2); // "52"
console.log("5" - 2); // 3
```

---

## 13. Operators

```js
let a = 5,
  b = 2;
console.log(a + b); // 7
console.log(a * b); // 10
```

---

## 14. `+` Operator

```js
console.log(5 + "5"); // "55"
console.log(5 + true); // 6
```

---

## 15. Template String

```js
let name = "Prashanth";
console.log(`Hello, ${name}!`);
```

---

## 16. `prompt`

```js
let user = prompt("Enter your name:");
console.log(user);
```

---

## 17. Truthy / Falsy

```js
console.log(Boolean("")); // false
console.log(Boolean("Hi")); // true
```

---

## 18. Postfix / Prefix

```js
let x = 5;
console.log(x++); // 5
console.log(++x); // 7
```

---

## 19. Short Circuit

```js
console.log(false && "Hello"); // false
console.log(true || "Hi"); // true
```

---

## 20. Conditional Statement

```js
let age = 18;
if (age >= 18) console.log("Adult");
else console.log("Minor");
```

---

## 21. Loops

```js
for (let i = 0; i < 3; i++) console.log(i);
```

---

## 22. `break`

```js
for (let i = 0; i < 5; i++) {
  if (i === 3) break;
  console.log(i);
}
```

---

## 23. `continue`

```js
for (let i = 0; i < 5; i++) {
  if (i === 2) continue;
  console.log(i);
}
```

---

## 24. `return`

```js
function add(a, b) {
  return a + b;
}
console.log(add(2, 3));
```

---

## 25. Functions (Types)

```js
function normal() {
  return "Hi";
}
const arrow = () => "Hello";
```

---

## 26. IIFE

```js
(function () {
  console.log("IIFE runs immediately!");
})();
```

---

## 27. Unreachable Statement

```js
function test() {
  return;
  console.log("Never runs"); // unreachable
}
```

---

## 28. Function Parameters

```js
function greet(name = "Guest") {
  console.log("Hello " + name);
}
greet("Prashanth");
```

---

## 29. Higher Order Function

```js
function hof(fn) {
  return fn();
}
hof(() => console.log("HOF called"));
```

---

## 30. Callback Function

```js
function process(cb) {
  cb();
}
process(() => console.log("Callback executed"));
```

---

## 31. JS Runtime Environment

- Consists of **Call Stack + Heap + APIs + Event Loop**

---

## 32. Object

```js
let obj = { name: "Prashanth", age: 23 };
```

---

## 33. Create Object (2 Ways)

```js
let obj1 = {}; // literal
let obj2 = new Object(); // constructor
```

---

## 34. Bracket Notation

```js
let obj = { name: "JS" };
console.log(obj["name"]);
```

---

## 35. Dot Notation

```js
let obj = { name: "JS" };
console.log(obj.name);
```

---

## 36. Call Stack

- Functions pushed/popped during execution.

---

## 37. Global Execution Context

- Created when JS starts, contains global object + `this`.

---

## 38. Runtime Environment

- Includes **Heap, Stack, APIs, Event Loop**.

---

## 39. Variable Object

- Stores variables/functions in execution context.

---

## 40. Array

```js
let arr = [1, 2, 3];
```

---

## 41. JIT

- Just-In-Time compilation for faster execution.

---

## 42. Lexical Environment

- Scope + reference to outer scope.

---

## 43. Closure

```js
function outer() {
  let count = 0;
  return () => ++count;
}
const counter = outer();
console.log(counter()); // 1
```

---

## 44. Hoisting

```js
console.log(a); // undefined
var a = 10;
```

---

## 45. TDZ

```js
// console.log(x); ❌ ReferenceError
let x = 5;
```

---

## 46. Scopes

- Global, Function, Block

---

## 47. `var`

```js
var a = 10;
```

---

## 48. `let`

```js
let b = 20;
```

---

## 49. `const`

```js
const c = 30;
```

---

## 50. First-Class Function

- Functions can be passed/returned.

---

## 51. `this`

```js
console.log(this); // global object
```

---

## 52. Function Constructor

```js
function Person(name) {
  this.name = name;
}
const p = new Person("Prashanth");
```

---

## 53. Prototype

```js
Person.prototype.greet = function () {
  console.log("Hello " + this.name);
};
```

---

## 54. Prototypal Chaining

- Objects inherit via prototype chain.

---

## 55. Inheritance

```js
class A {}
class B extends A {}
```

---

## 56. Scope Chaining

- Inner scopes access outer variables.

---

## 57. Function Methods

```js
function greet(msg) {
  console.log(msg + " " + this.name);
}
greet.call({ name: "JS" }, "Hi");
```

---

## 58. Function Overloading

- Not natively supported, can simulate with arguments.

---

## 59. Ways to Write Array

```js
let arr1 = [1, 2];
let arr2 = new Array(3, 4);
```

---

## 60. Recursion

```js
function fact(n) {
  return n === 0 ? 1 : n * fact(n - 1);
}
console.log(fact(5));
```

---

## 61. OOP Principles

- Encapsulation, Abstraction, Inheritance, Polymorphism

---

## 62. Pure vs Impure

```js
function pure(a, b) {
  return a + b;
}
let x = 10;
function impure() {
  x++;
}
```

---

## 63. DOM

```js
document.getElementById("id");
```

---

## 64. DOM Methods

```js
document.querySelector(".class");
```

---

## 65. JavaScript Events

```js
// Example: click event
document.getElementById("btn").onclick = () => {
  console.log("Button clicked!");
};
```

---

## 66. Event Handling

```js
function handleClick() {
  console.log("Handled!");
}
document.getElementById("btn").addEventListener("click", handleClick);
```

---

## 67. Event Handler

```js
document.getElementById("btn").onclick = function () {
  console.log("Event handler executed");
};
```

---

## 68. Event Property

```js
document.getElementById("btn").addEventListener("click", (e) => {
  console.log(e.type); // "click"
});
```

---

## 69. Web Storage

```js
localStorage.setItem("name", "Prashanth");
console.log(localStorage.getItem("name"));
```

---

## 70. `addEventListener`

```js
document.getElementById("btn").addEventListener("mouseover", () => {
  console.log("Mouse over!");
});
```

---

## 71. `textContent`

```js
document.getElementById("demo").textContent = "Hello!";
```

---

## 72. `innerText`

```js
document.getElementById("demo").innerText = "Visible text only";
```

---

## 73. `innerHTML`

```js
document.getElementById("demo").innerHTML = "<b>Bold Text</b>";
```

---

## 74. Attribute Methods

```js
let el = document.getElementById("demo");
el.setAttribute("class", "highlight");
console.log(el.getAttribute("class"));
```

---

## 75. `classList`

```js
el.classList.add("active");
el.classList.remove("highlight");
```

---

## 76. `filter` Method

```js
let arr = [1, 2, 3, 4];
let even = arr.filter((n) => n % 2 === 0);
console.log(even); // [2,4]
```

---

## 77. JSON

```js
let obj = { name: "Prashanth" };
let str = JSON.stringify(obj);
console.log(JSON.parse(str));
```

---

## 78. `push`

```js
let arr = [1, 2];
arr.push(3);
console.log(arr); // [1,2,3]
```

---

## 79. `pop`

```js
let arr = [1, 2, 3];
arr.pop();
console.log(arr); // [1,2]
```

---

## 80. `unshift`

```js
let arr = [2, 3];
arr.unshift(1);
console.log(arr); // [1,2,3]
```

---

## 81. `shift`

```js
let arr = [1, 2, 3];
arr.shift();
console.log(arr); // [2,3]
```

---

## 82. `find`

```js
let arr = [10, 20, 30];
console.log(arr.find((n) => n > 15)); // 20
```

---

## 83. `sort`

```js
let arr = [3, 1, 2];
arr.sort();
console.log(arr); // [1,2,3]
```

---

## 84. `search` (String)

```js
let str = "Hello World";
console.log(str.search("World")); // 6
```

---

## 85. Category (Conceptual)

- Used in classification/grouping of data.

---

## 86. Shallow Copy

```js
let arr = [1, 2];
let copy = arr.slice();
```

---

## 87. Deep Copy

```js
let obj = { a: 1, b: { c: 2 } };
let deep = JSON.parse(JSON.stringify(obj));
```

---

## 88. Rest Parameter

```js
function sum(...nums) {
  return nums.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3));
```

---

## 89. Spread Operator

```js
let arr = [1, 2];
let newArr = [...arr, 3];
```

---

## 90. Synchronous

```js
console.log("First");
console.log("Second");
```

---

## 91. Asynchronous

```js
setTimeout(() => console.log("Async"), 1000);
console.log("Sync");
```

---

## 92. `setTimeout`

```js
setTimeout(() => console.log("Runs after 1s"), 1000);
```

---

## 93. `setInterval`

```js
setInterval(() => console.log("Repeats every 2s"), 2000);
```

---

## 94. AJAX (basic)

```js
let xhr = new XMLHttpRequest();
xhr.open("GET", "data.json");
xhr.onload = () => console.log(xhr.responseText);
xhr.send();
```

---

## 95. Promise Methods

```js
Promise.all([Promise.resolve(1), Promise.resolve(2)]).then((res) =>
  console.log(res)
);
```

---

## 96. Destructuring

```js
let [a, b] = [1, 2];
```

---

## 97. Object Destructuring

```js
let { name, age } = { name: "Prashanth", age: 23 };
```

---

## 98. Array Destructuring

```js
let [x, y] = [10, 20];
```

---

## 99. Promise vs setTimeout

- Promise → **microtask**
- setTimeout → **macrotask**

---

## 100. Fetch API

```js
fetch("data.json")
  .then((res) => res.json())
  .then((data) => console.log(data));
```

---

## 101. Babel

- JS compiler/transpiler for backward compatibility.

---

## 102. Async/Await

```js
async function getData() {
  return await Promise.resolve("Done");
}
getData().then(console.log);
```

---

## 103. `Map`

```js
let map = new Map();
map.set("a", 1);
console.log(map.get("a"));
```

---

## 104. `Set`

```js
let set = new Set([1, 2, 2]);
console.log(set); // {1,2}
```

---

## 105. `for...of`

```js
for (let val of [1, 2, 3]) console.log(val);
```

---

## 106. `for...in`

```js
let obj = { a: 1, b: 2 };
for (let key in obj) console.log(key);
```

---

## 107. `forEach`

```js
[1, 2, 3].forEach((n) => console.log(n));
```

---

## 108. `try...catch...finally`

```js
try {
  throw new Error("Oops");
} catch (e) {
  console.log(e.message);
} finally {
  console.log("Always runs");
}
```

---

## 109. `splice`

```js
let arr = [1, 2, 3];
arr.splice(1, 1); // remove index 1
console.log(arr); // [1,3]
```

---

## 110. `slice`

```js
let arr = [1, 2, 3];
console.log(arr.slice(0, 2)); // [1,2]
```

---

## 111. `join`

```js
let arr = ["a", "b"];
console.log(arr.join("-")); // "a-b"
```

---

## 112. `Array.isArray()`

```js
console.log(Array.isArray([1, 2])); // true
```

---

## 113. `reduce`

```js
let arr = [1, 2, 3];
let sum = arr.reduce((a, b) => a + b, 0);
console.log(sum); // 6
```

---

## 114. `reduceRight`

```js
let arr = ["a", "b", "c"];
let result = arr.reduceRight((acc, val) => acc + val);
console.log(result); // "cba"
```

---
