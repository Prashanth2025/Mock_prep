That's a massive list! I'll do my best to provide explanations and example code for each topic. Here's the first part:

1. JavaScript

JavaScript is a high-level, dynamic, and interpreted programming language used for client-side scripting on the web.

console.log("Hello, World!"); // Output: Hello, World!

2. Function Call

A function call is an expression that invokes a function.

function greet(name) {
console.log(`Hello, ${name}!`);
}

greet("John"); // Output: Hello, John!

3. Method Call

A method call is an expression that invokes a method on an object.

const person = {
name: "John",
greet: function() {
console.log(`Hello, my name is ${this.name}.`);
}
};

person.greet(); // Output: Hello, my name is John.

4. Identifiers

Identifiers are names given to variables, functions, and labels in JavaScript.

let x = 10; // x is an identifier

5. Variables

Variables are used to store and manipulate data.

let x = 10;
console.log(x); // Output: 10

x = 20;
console.log(x); // Output: 20

6. Why JS is Dynamic-Type Program Lang

JavaScript is dynamically typed because it does not require explicit type definitions for variables.

let x = 10; // x is a number
x = "hello"; // x is now a string

7. Redeclaration

Redeclaration occurs when a variable is declared multiple times in the same scope.

var x = 10;
var x = 20; // redeclaration
console.log(x); // Output: 20

8. Reinitialization

Reinitialization occurs when a variable's value is changed after it's declared.

let x = 10;
x = 20; // reinitialization
console.log(x); // Output: 20

9. Strict Mode

Strict mode is a way to opt-in to a restricted variant of JavaScript that provides more informative error messages and prevents certain types of errors.

"use strict";
x = 10; // ReferenceError: x is not defined

10. Datatypes

JavaScript has several datatypes: primitive types (number, string, boolean, null, undefined, symbol) and reference types (object, array, function).

let x = 10; // number
let y = "hello"; // string
let z = true; // boolean

11. Type Conversion

Type conversion is the process of converting a value from one type to another.

let x = "10";
let y = parseInt(x);
console.log(y); // Output: 10
console.log(typeof y); // Output: number

12. Type Coercion

Type coercion is the automatic conversion of a value from one type to another.

let x = 10;
let y = "hello";
console.log(x + y); // Output: "10hello"

13. Operators

Operators are symbols used to perform operations on values.

let x = 10;
let y = 5;
console.log(x + y); // Output: 15
console.log(x > y); // Output: true

14. Operations Performed Using +

The + operator can perform addition, concatenation, or both.

let x = 10;
let y = 20;
console.log(x + y); // Output: 30

let a = "hello";
let b = "world";
console.log(a + " " + b); // Output: "hello world"

15. Template String

Template strings are a way to create strings using backticks and ${} syntax.

let name = "John";
let age = 30;
console.log(`My name is ${name} and I am ${age} years old.`);
// Output: "My name is John and I am 30 years old."

16. Prompt

The prompt function displays a dialog box and returns the user's input.

let name = prompt("What is your name?");
console.log(`Hello, ${name}!`);

17. Truthy and Falsy Values

Truthy values are values that evaluate to true in a conditional statement. Falsy values are values that evaluate to false.

console.log(!!10); // Output: true
console.log(!!0); // Output: false
console.log(!!"hello"); // Output: true
console.log(!!""); // Output: false

18. Postfix / Prefix

Postfix and prefix operators are used to increment or decrement a value.

let x = 10;
x++; // postfix increment
console.log(x); // Output: 11

let y = 10;
++y; // prefix increment
console.log(y); // Output: 11

19. Short Circuit Evaluation

Short circuit evaluation is a behavior where the second operand of a logical operator is not evaluated if the first operand determines the result.

let x = 10;
let y = 20;
console.log(x > 5 || y > 30); // Output: true
// y > 30 is not evaluated because x > 5 is true

20. Conditional Statement

Conditional statements are used to execute different blocks of code based on conditions.

let x = 10;
if (x > 5) {
console.log("x is greater than 5");
} else {
console.log("x is less than or equal to 5");
}

21. Looping Statements

Looping statements are used to execute a block of code repeatedly.

for (let i = 0; i < 5; i++) {
console.log(i);
}

22. Break

The break statement is used to exit a loop or switch statement.

for (let i = 0; i < 5; i++) {
if (i === 3) {
break;
}
console.log(i);
}

23. Continue

The continue statement is used to skip to the next iteration of a loop.

for (let i = 0; i < 5; i++) {
if (i === 3) {
continue;
}
console.log(i);
}

24. Return

The return statement is used to exit a function and return a value.

function add(a, b) {
return a + b;
}

console.log(add(2, 3)); // Output: 5

25. Functions

Functions are blocks of code that can be executed multiple times.

function greet(name) {
console.log(`Hello, ${name}!`);
}

greet("John"); // Output: Hello, John!

26. IIFE

IIFE (Immediately Invoked Function Expression) is a function that is executed immediately after it's defined.

(function() {
console.log("Hello, World!");
})();

27. Unreachable Statement

An unreachable statement is a statement that cannot be executed.

function test() {
return;
console.log("This statement is unreachable");
}

28. Function with Parameters

Functions can take parameters, which are values passed to the function when it's called.

function greet(name) {
console.log(`Hello, ${name}!`);
}

greet("John"); // Output: Hello, John!

29. Higher Order Function

A higher-order function is a function that takes another function as an argument or returns a function.

function map(arr, fn) {
return arr.map(fn);
}

const double = x => x \* 2;
console.log(map([1, 2, 3], double)); // Output: [2, 4, 6]

30. Callback Function

A callback function is a function passed as an argument to another function.

function test(callback) {
callback();
}

test(function() {
console.log("Callback function called");
});

31. JS Runtime Environment

The JavaScript runtime environment is the environment in which JavaScript code is executed.

console.log("Hello, World!"); // executed in the browser or Node.js environment

32. Object

An object is a collection of key-value pairs.

const person = {
name: "John",
age: 30
};

console.log(person.name); // Output: John
console.log(person.age); // Output: 30

33. Two Ways to Create Object

Objects can be created using the Object constructor or the object literal syntax.

const obj1 = new Object();
const obj2 = {};

console.log(typeof obj1); // Output: object
console.log(typeof obj2); // Output: object

34. Bracket Notation

Bracket notation is a way to access properties of an object using square brackets.

const person = {
name: "John",
age: 30
};

console.log(person["name"]); // Output: John
console.log(person["age"]); // Output: 30

35. Dot Notation

Dot notation is a way to access properties of an object using a dot.

const person = {
name: "John",
age: 30
};

console.log(person.name); // Output: John
console.log(person.age); // Output: 30

36. Call Stack

The call stack is a data structure that keeps track of the functions that are currently being executed.

function test() {
console.log("Test function called");
}

test();

37. Global Execution Context

The global execution context is the top-level execution context in JavaScript.

console.log("Global execution context");

38. Variable Object

A variable object is an object that stores the variables declared in a scope.

let x = 10;
console.log(x); // Output: 10

39. Array

An array is a collection of values of the same type.

const colors = ["red", "green", "blue"];
console.log(colors[0]); // Output: red
console.log(colors.length); // Output: 3

40. JIT

JIT (Just-In-Time) compilation is a technique used by JavaScript engines to improve performance.

// JIT compilation happens behind the scenes
for (let i = 0; i < 1000000; i++) {
// do something
}

41. Lexical Environment

The lexical environment is the scope in which a function is defined.

function outer() {
let x = 10;
function inner() {
console.log(x); // Output: 10
}
inner();
}
outer();

42. Closure

A closure is a function that has access to its own scope and the scope of its outer functions.

function outer() {
let x = 10;
return function inner() {
console.log(x); // Output: 10
}
}
const innerFunc = outer();
innerFunc();

43. Hoisting

Hoisting is the behavior of JavaScript where variables and functions are moved to the top of their scope.

console.log(x); // Output: undefined
var x = 10;

44. TDZ

TDZ (Temporal Dead Zone) is a region in the code where a variable is not accessible.

console.log(x); // ReferenceError: x is not defined
let x = 10;

45. Scopes

Scopes determine the accessibility of variables.

let x = 10; // global scope
function outer() {
let y = 20; // function scope
if (true) {
let z = 30; // block scope
}
}

46. Var

var is a keyword used to declare variables.

var x = 10;
console.log(x); // Output: 10

47. Let

let is a keyword used to declare block-scoped variables.

let x = 10;
if (true) {
let x = 20;
console.log(x); // Output: 20
}
console.log(x); // Output: 10

48. Const

const is a keyword used to declare constants.

const x = 10;
console.log(x); // Output: 10
x = 20; // TypeError: Assignment to constant variable.

49. First Class Function

First-class functions are functions that can be passed as arguments, returned from functions, and assigned to variables.

function greet(name) {
console.log(`Hello, ${name}!`);
}
const sayHello = greet;
sayHello("John"); // Output: Hello, John!

50. This Keyword

The this keyword refers to the current execution context.

const person = {
name: "John",
greet: function() {
console.log(`Hello, my name is ${this.name}.`);
}
};
person.greet(); // Output: Hello, my name is John.

51. Function Constructor

The Function constructor is a built-in constructor that creates new functions.

const greet = new Function("name", "console.log(`Hello, ${name}!`);");
greet("John"); // Output: Hello, John!

52. Prototype

A prototype is an object that is shared by all instances of a constructor function.

function Person(name) {
this.name = name;
}
Person.prototype.greet = function() {
console.log(`Hello, my name is ${this.name}.`);
};
const person = new Person("John");
person.greet(); // Output: Hello, my name is John.

53. Prototypal Chaining

Prototypal chaining is the mechanism by which objects inherit properties from their prototypes.

function Animal(name) {
this.name = name;
}
Animal.prototype.eat = function() {
console.log(`${this.name} is eating.`);
};
function Dog(name) {
Animal.call(this, name);
}
Dog.prototype = Object.create(Animal.prototype);
const dog = new Dog("Buddy");
dog.eat(); // Output: Buddy is eating.

54. Inheritance

Inheritance is the mechanism by which objects can inherit properties and behavior from other objects.

class Animal {
constructor(name) {
this.name = name;
}
eat() {
console.log(`${this.name} is eating.`);
}
}
class Dog extends Animal {
constructor(name) {
super(name);
}
}
const dog = new Dog("Buddy");
dog.eat(); // Output: Buddy is eating.

55. Scope Chaining

Scope chaining is the mechanism by which variables are resolved in nested scopes.

function outer() {
let x = 10;
function inner() {
console.log(x); // Output: 10
}
inner();
}
outer();

56. Function Methods

Function methods are methods that can be called on functions.

function greet(name) {
console.log(`Hello, ${name}!`);
}
greet.call(null, "John"); // Output: Hello, John!
greet.apply(null, ["John"]); // Output: Hello, John!
const boundGreet = greet.bind(null, "John");
boundGreet(); // Output: Hello, John!

57. Function Overloading

Function overloading is not directly supported in JavaScript, but can be achieved using optional parameters or variadic functions.

function greet(name = "World") {
console.log(`Hello, ${name}!`);
}
greet(); // Output: Hello, World!
greet("John"); // Output: Hello, John!

58. Ways to Write Array

Arrays can be written using the Array constructor or the array literal syntax.

const arr1 = new Array(1, 2, 3);
const arr2 = [1, 2, 3];
console.log(arr1); // Output: [1, 2, 3]
console.log(arr2); // Output: [1, 2, 3]

59. Recursion

Recursion is a technique where a function calls itself.

function factorial(n) {
if (n === 0) {
return 1;
}
return n \* factorial(n - 1);
}
console.log(factorial(5)); // Output: 120

60. Principles of OOPs

OOPs (Object-Oriented Programming) principles include encapsulation, abstraction, inheritance, and polymorphism.

class Animal {
constructor(name) {
this.name = name;
}
sound() {
console.log("The animal makes a sound.");
}
}
class Dog extends Animal {
constructor(name) {
super(name);
}
sound() {
console.log("The dog barks.");
}
}
const dog = new Dog("Buddy");
dog.sound(); // Output: The dog barks.

61. Pure and Impure Functions

Pure functions are functions that always return the same output given the same inputs. Impure functions are functions that can return different outputs given the same inputs.

function pureAdd(a, b) {
return a + b;
}
console.log(pureAdd(2, 3)); // Output: 5

let x = 10;
function impureAdd(a) {
return a + x;
}
console.log(impureAdd(2)); // Output: 12
x = 20;
console.log(impureAdd(2)); // Output: 22

62. DOM

The DOM (Document Object Model) is a representation of an HTML document as a tree-like structure.

const paragraph = document.createElement("p");
paragraph.textContent = "Hello, World!";
document.body.appendChild(paragraph);

63. DOM Methods

DOM methods are methods that can be used to manipulate the DOM.

const element = document.getElementById("myElement");
element.style.color = "red";

64. JavaScript Events

JavaScript events are used to respond to user interactions.

document.addEventListener("click", function() {
console.log("The document was clicked.");
});

65. Event Handling

Event handling is the process of responding to events.

const button = document.getElementById("myButton");
button.addEventListener("click", function() {
console.log("The button was clicked.");
});

66. Event Handler

An event handler is a function that is called in response to an event.

document.addEventListener("click", function(event) {
console.log("The document was clicked.");
});

67. Event Property

Event properties are properties of an event object that provide information about the event.

document.addEventListener("click", function(event) {
console.log(event.clientX); // Output: the x-coordinate of the click
});

68. Web Storage

Web storage is a mechanism for storing data in the browser.

localStorage.setItem("name", "John");
const name = localStorage.getItem("name");
console.log(name); // Output: John

69. addEventListener

addEventListener is a method that adds an event listener to an element.

document.addEventListener("click", function() {
console.log("The document was clicked.");
});

70. Text Content

textContent is a property that gets or sets the text content of an element.

const paragraph = document.createElement("p");
paragraph.textContent = "Hello, World!";
document.body.appendChild(paragraph);

71. InnerText

innerText is a property that gets or sets the text content of an element.

const paragraph = document.createElement("p");
paragraph.innerText = "Hello, World!";
document.body.appendChild(paragraph);

72. InnerHtml

innerHTML is a property that gets or sets the HTML content of an element.

const div = document.createElement("div");
div.innerHTML = "<p>Hello, World!</p>";
document.body.appendChild(div);

73. Attribute Methods

Attribute methods are methods that can be used to manipulate attributes of an element.

const link = document.createElement("a");
link.setAttribute("href", "https://www.example.com");
console.log(link.getAttribute("href")); // Output: https://www.example.com

74. Classlist

classList is a property that provides methods for manipulating the classes of an element.

const element = document.createElement("div");
element.classList.add("active");
console.log(element.classList.contains("active")); // Output: true

75. Filter Method

The filter method is an array method that creates a new array with elements that pass a test.

const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(number => number % 2 === 0);
console.log(evenNumbers); // Output: [2, 4]

76. JSON

JSON (JavaScript Object Notation) is a lightweight data interchange format.

const person = {
name: "John",
age: 30
};
const json = JSON.stringify(person);
console.log(json); // Output: {"name":"John","age":30}

77. Push

push is an array method that adds elements to the end of an array.

const numbers = [1, 2, 3];
numbers.push(4);
console.log(numbers); // Output: [1, 2, 3, 4]

78. Pop

pop is an array method that removes the last element of an array.

const numbers = [1, 2, 3, 4];
const lastNumber = numbers.pop();
console.log(lastNumber); // Output: 4
console.log(numbers); // Output: [1, 2, 3]

79. Unshift

unshift is an array method that adds elements to the beginning of an array.

const numbers = [1, 2, 3];
numbers.unshift(0);
console.log(numbers); // Output: [0, 1, 2, 3]

80. Shift

shift is an array method that removes the first element of an array.

const numbers = [1, 2, 3, 4];
const firstNumber = numbers.shift();
console.log(firstNumber); // Output: 1
console.log(numbers); // Output: [2, 3, 4]

81. Find

The find method is an array method that returns the first element that satisfies a condition.

const numbers = [1, 2, 3, 4, 5];
const evenNumber = numbers.find(number => number % 2 === 0);
console.log(evenNumber); // Output: 2

82. Sort

The sort method is an array method that sorts the elements of an array.

const numbers = [4, 2, 7, 1, 3];
numbers.sort((a, b) => a - b);
console.log(numbers); // Output: [1, 2, 3, 4, 7]

83. Search

The search method is a string method that searches for a pattern in a string.

const str = "Hello, World!";
const index = str.search("World");
console.log(index); // Output: 7

84. Shallow Copy

A shallow copy is a way to create a copy of an object by copying its properties.

const obj = { a: 1, b: 2 };
const shallowCopy = Object.assign({}, obj);
console.log(shallowCopy); // Output: { a: 1, b: 2 }

85. Deep Copy

A deep copy is a way to create a copy of an object by recursively copying all its properties.

const obj = { a: 1, b: { c: 2 } };
const deepCopy = JSON.parse(JSON.stringify(obj));
console.log(deepCopy); // Output: { a: 1, b: { c: 2 } }

86. Rest Parameter/Operator

The rest parameter/operator is a syntax that allows a function to accept a variable number of arguments.

function sum(...numbers) {
return numbers.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3, 4, 5)); // Output: 15

87. Spread

The spread operator is a syntax that allows an iterable to be expanded into individual elements.

const numbers = [1, 2, 3];
console.log(...numbers); // Output: 1 2 3

88. Synchronous

Synchronous code is executed one line at a time, in sequence.

console.log("Hello");
console.log("World");

89. Asynchronous

Asynchronous code is executed in parallel, allowing other code to run while waiting for a task to complete.

setTimeout(() => {
console.log("Hello");
}, 2000);
console.log("World");

90. Set Timeout

setTimeout is a function that executes a block of code after a specified delay.

setTimeout(() => {
console.log("Hello");
}, 2000);

91. Set Interval

setInterval is a function that executes a block of code repeatedly at a specified interval.

setInterval(() => {
console.log("Hello");
}, 1000);

92. Ajax

Ajax (Asynchronous JavaScript and XML) is a technique used to send HTTP requests and receive responses without reloading the page.

const xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data", true);
xhr.onload = function() {
if (xhr.status === 200) {
console.log(xhr.responseText);
}
};
xhr.send();

93. Promise

A promise is an object that represents the eventual completion (or failure) of an asynchronous operation.

const promise = new Promise((resolve, reject) => {
setTimeout(() => {
resolve("Hello");
}, 2000);
});
promise.then((message) => {
console.log(message); // Output: Hello
});

94. Promise Methods

Promise methods are methods that can be used to handle promises.

const promise = new Promise((resolve, reject) => {
setTimeout(() => {
resolve("Hello");
}, 2000);
});
promise.then((message) => {
console.log(message); // Output: Hello
}).catch((error) => {
console.error(error);
});

95. Destructuring

Destructuring is a syntax that allows you to extract values from objects or arrays into individual variables.

const person = { name: "John", age: 30 };
const { name, age } = person;
console.log(name); // Output: John
console.log(age); // Output: 30

96. Object Destructuring

Object destructuring is a syntax that allows you to extract values from objects into individual variables.

const person = { name: "John", age: 30 };
const { name: personName, age: personAge } = person;
console.log(personName); // Output: John
console.log(personAge); // Output: 30

97. Array Destructuring

Array destructuring is a syntax that allows you to extract values from arrays into individual variables.

const numbers = [1, 2, 3];
const [one, two, three] = numbers;
console.log(one); // Output: 1
console.log(two); // Output: 2
console.log(three); // Output: 3
