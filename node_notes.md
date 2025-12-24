Node.js is an open-source, cross-platform JavaScript runtime environment that allows developers to run JavaScript outside the browser, typically on the server-side.

Key Features

1)Open Source

    Free to use and free to contribute to.

    Supported by a global developer community.

2)Cross-Platform

    Works on Windows, Linux, macOS, and other operating systems.

    Code runs the same way across all platforms.

3)Server-Side JavaScript

    Developers can use JavaScript for backend development.

    Eliminates the need to learn another language for server-side programming.

4)Built on V8 Engine

    Node.js uses the V8 JavaScript engine (from Google Chrome) to execute code.

    Provides high performance and fast execution.

5)Libuv Library

    Node.js uses libuv, a C library, to handle asynchronous, event-driven I/O operations.

    Enables non-blocking operations for better scalability.

Summary

Node.js = V8 Engine + Libuv library + JavaScript runtime environment

    Runs JS on the server

    Asynchronous and event-driven

    Cross-platform and open-source

Comparison between Node.js and Web Browser JavaScript
| **Feature** | **Web Browser JavaScript** | **Node.js** |
| ------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Environment** | Runs on the client-side (browser) | Runs on the server-side |
| **Purpose** | Mainly used for frontend development | Mainly used for backend/server-side development |
| **HTML/CSS Manipulation** | Can manipulate HTML, CSS, and DOM | Cannot manipulate HTML or CSS |
| **Module System** | Supports ES6 modules (`import` & `export`) | Uses CommonJS modules (`require()` & `module.exports`) |
| **Access to Web APIs** | Can access `window` object and browser Web APIs | Cannot access `window` or browser APIs; uses `global` object instead |
| **JavaScript Engine** | Different browsers use different engines: V8 (Chrome), SpiderMonkey (Firefox), Chakra (Edge) | Built on Chrome’s V8 engine + libuv library |
| **Use Case** | Interactive web pages, client-side logic | Server-side logic, APIs, databases, file system operations |

History of Node.js

2009 – Initial Development

Node.js was developed by Ryan Dahl in 2009.

Goal: Create an environment to run JavaScript on the server-side.

2010 – NPM (Node Package Manager) Release

NPM was introduced, allowing developers to install and manage JavaScript libraries and packages via the command-line interface (CLI).

2015 – Node.js Foundation Established

A non-profit organization called the Node.js Foundation was formed.

Purpose: Promote the growth, adoption, and development of Node.js globally.

Node.js has gained immense popularity among developers.

It efficiently and effectively handles server-side operations.

Built on Chrome's V8 JavaScript engine, Node.js provides high performance.

Designed for scalable and high-performance applications, making it ideal for real-time apps, APIs, and microservices.

Key Features of Node.js

1)Asynchronous I/O & Event-Driven Architecture

    Node.js operations are non-blocking and event-driven, allowing efficient handling of multiple tasks simultaneously.

2)Single-Threaded

    Uses a single thread (event loop) to execute code, but can handle many concurrent connections efficiently.

3)Scalability

    esigned for scalable applications and supports microservices architecture.

4)High Performance

    Built on Chrome’s V8 engine, providing fast execution of JavaScript code.

5)Real-Time Applications

    Ideal for chat apps, live updates, and collaborative tools.

6)Rich Ecosystem & NPM Libraries

    Access to a vast number of open-source packages via npm.

7)Community Support

    Strong developer community contributes to libraries, tools, and support.

8)Cross-Platform Compatibility

    Works on Windows, Linux, macOS, and other platforms.

9)RESTful APIs & Real-Time Communication

    Easily builds APIs and supports WebSockets for real-time interactions.

10. No Buffering

Node.js Architecture Components

1)V8 Engine

    Fundamental part of Node.js.

    Interprets JavaScript code and converts it to machine code that the computer can execute.

2)Libuv

    Open-source library focused on asynchronous I/O.

    Provides access to the operating system, file system, and networking.

    Manages the event loop and I/O operations efficiently.

3)Event Queue

    Stores incoming client requests.

    Passes them to the event loop sequentially for processing.

4)Event Loop

    Handles small tasks such as executing callback functions or network I/O.

    These are non-blocking tasks that do not block the main thread.

5)Thread Pool / Event Workers

    Consists of threads used for CPU-intensive or blocking operations.

    Helps Node.js fulfill client requests efficiently without blocking the main thread.

Modules in Node.js

    Modules are pieces of code stored in separate files that help split a large program into manageable parts.

Purpose of Modules

    Increase code readability.

    Enable reusability across multiple files.

    Organize a complete program into smaller, maintainable components.

Node.js Module Types

    By default, Node.js supports CommonJS modules. Modules in Node.js are classified into three types:

Custom Modules (User-Defined)

    Created by the developer.

    Stored in separate files and imported wherever needed.

Core Modules (Built-in)

    Provided by Node.js out-of-the-box.

    Examples: fs, http, path, os.

Third-Party Modules (npm Packages)

    Installed via npm.

    Examples: express, mongoose, cors.

1. Custom Modules

   Custom modules are modules created by users to separate code and improve reusability and maintainability.

Purpose

    Helps in code organization.

    Makes code modular, readable, and easier to manage.

    Allows reusing functions, objects, or variables across different files.

Exporting

    Use module.exports to send a variable, function, or object from one file to another.

Importing

    Use require() to import the module into another file.

2. Core Modules

   Core modules are built-in libraries provided by Node.js that allow developers to work with various functionalities without installing additional packages.

Purpose

    Simplify common server-side tasks.

    Provide essential functionality for operating system, file handling, networking, paths, etc.

    Do not require installation via npm—they are available out-of-the-box.

Common Core Modules

| Module | Purpose                                                |
| ------ | ------------------------------------------------------ |
| `os`   | Provides information about the operating system        |
| `fs`   | File system operations (read, write, delete files)     |
| `path` | Work with file and directory paths                     |
| `http` | Create HTTP servers and handle HTTP requests/responses |

OS Module

    The OS module is a core module in Node.js used to get information about the operating system and the machine where the Node.js server is running.

Importing the OS Module
const os = require('os');

Common Methods
| Method | Description |
| ------------------------ | ----------------------------------------------------- |
| `os.arch()` | Returns the CPU architecture (e.g., 'x64') |
| `os.platform()` | Returns the operating system platform (e.g., 'win32') |
| `os.cpus()` | Returns an array with CPU information |
| `os.freemem()` | Returns the free system memory in bytes |
| `os.totalmem()` | Returns the total system memory in bytes |
| `os.hostname()` | Returns the hostname of the machine |

Path Module

    The Path module is a core module in Node.js used to work with file and directory paths.
    It provides utilities to handle and transform paths dynamically, making it easier to work with file system paths in a platform-independent way.

Importing the Path Module
const path = require('path');

Common Methods

| Method                    | Description                                            |
| ------------------------- | ------------------------------------------------------ |
| `path.dirname(filePath)`  | Returns the **directory name** of a file path          |
| `path.extname(filePath)`  | Returns the **file extension** (e.g., `.jpeg`)         |
| `path.basename(filePath)` | Returns the **file name** with extension               |
| `path.join(...paths)`     | Joins multiple paths into a **single normalized path** |

File System (fs) Module

    The File System (fs) module is a core module in Node.js used to interact with the file system.
    It allows you to read, write, update, delete, and manipulate files and directories within a Node.js application.

Importing the fs Module
const fs = require('fs');

Types of Methods

    The fs module provides both synchronous and asynchronous methods:

    Asynchronous methods: Non-blocking, execute in the background.

    Synchronous methods: Blocking, execution waits until the operation completes.

Common Methods

| Method                                    | Description                                        |
| ----------------------------------------- | -------------------------------------------------- |
| `fs.readFile()` / `fs.readFileSync()`     | Reads the content of a file                        |
| `fs.writeFile()` / `fs.writeFileSync()`   | Writes data to a file (creates if not exists)      |
| `fs.appendFile()` / `fs.appendFileSync()` | Appends data to a file                             |
| `fs.unlink()` / `fs.unlinkSync()`         | Deletes a file                                     |
| `fs.copyFile()` / `fs.copyFileSync()`     | Copies a file from source path to destination path |
| `fs.rename()` / `fs.renameSync()`         | Renames a file or moves it to a new location       |
| `fs.mkdir()` / `fs.mkdirSync()`           | Creates a new directory                            |
| `fs.rmdir()` / `fs.rmdirSync()`           | Deletes a directory                                |

HTTP Module in Node.js

The http module is an in-built Node.js core module used to create HTTP servers.
It allows the server to handle client requests and send responses back.
Node.js servers work with REST APIs and manage web applications.

| Feature                 | Description                           |
| ----------------------- | ------------------------------------- |
| Built-in module         | No need to install externally         |
| Creates server          | Using `http.createServer()`           |
| Handles Client Requests | Accepts incoming requests from client |
| Sends Responses         | Returns data back to client           |
| Supports REST APIs      | Useful for backend services           |

Syntax & Example
const http = require("http");

const server = http.createServer((req, res) => {
// server logic
res.write("Hello from Node HTTP Server");
res.end();
});

server.listen(3000, () => {
console.log("Server running on port 3000");
});

Express.js

    Express.js is a minimal and flexible Node.js web application framework that provides a robust set of features for building web and mobile applications.

    Express.js is an open-source framework that is developed and maintained by the Node.js Foundation.

    It is a tool that simplifies building web applications and APIs using JavaScript on the server side.

    It is a lightweight and flexible framework that provides different middleware options to help handle the request–response cycle and routes to create a scalable application.

Applications of Express.js

| **Feature**                        | **Description**                                                                     |
| ---------------------------------- | ----------------------------------------------------------------------------------- |
| **Routing**                        | Helps define routes and manage various HTTP requests (GET, POST, PUT, DELETE).      |
| **Middleware**                     | Provides middleware functions to handle request–response operations efficiently.    |
| **Static File Serving**            | Allows serving static files such as images, CSS, and JavaScript easily.             |
| **Template Engines**               | Supports template engines like EJS, Pug, and Handlebars to build dynamic web pages. |
| **Database Integration**           | Can easily integrate with databases like MongoDB, MySQL, PostgreSQL, etc.           |
| **Flexibility & Scalability**      | Enables development of scalable and flexible applications.                          |
| **Easy to Deploy**                 | Simple to deploy on cloud platforms like Render, AWS, Heroku, Vercel, etc.          |
| **Easy to Debug**                  | Provides useful debugging features and clean error messages.                        |
| **Large Community**                | Has big community support with plenty of packages available via npm.                |
| **RESTful APIs**                   | Ideal for building REST APIs for backend services and mobile apps.                  |
| **Security**                       | Provides security middleware such as Helmet, CORS, and Rate Limiter.                |
| **CORS Support**                   | Supports Cross-Origin Resource Sharing to allow resource sharing across origins.    |
| **Single Page Applications (SPA)** | Works well with SPAs built using React, Angular, and Vue.                           |

request object

In Express.js, the request object, often abbreviated as req, represents the incoming HTTP request made by a client to the server.
It is a fundamental component in handling requests and accessing information sent from the client. The req object is automatically
created by Express and passed as the first argument to route handler functions and middleware.

Here are some of the key properties of the req object and their uses:

req.params: Contains named route parameters as defined in the route path. For example, in a route app.get('/users/:id'), req.params.id would hold the value of id from the URL.
req.query: Contains key-value pairs of the query string parameters (GET parameters) found in the URL. For instance, in app.get('/search?name=john&age=30'), req.query.name would be 'john' and req.query.age would be '30'.
req.body: Contains key-value pairs of data submitted in the request body, typically used with POST and PUT requests. This property is usually populated when using body-parsing middleware like express.json() or express.urlencoded().
req.headers: An object containing the HTTP headers sent by the client. For example, req.headers['user-agent'] would provide information about the client's browser.
req.ip: The remote IP address of the client making the request.
req.path: The path part of the request URL.
req.method: The HTTP method of the request (e.g., 'GET', 'POST', 'PUT', 'DELETE').
req.cookies: Contains cookies sent by the request, populated when using middleware like cookie-parser.

response object

In Express.js, the response object, commonly referred to as res, represents the HTTP response that an Express application sends
back to the client after receiving an HTTP request. It is automatically created by the framework and passed as an argument to
route handler functions and middleware.

The res object provides a variety of methods and properties for controlling and sending the response. Key functionalities include:

Sending data:

res.send([body]): Sends various types of responses, including strings, objects, arrays, and Buffers. It automatically sets the Content-Type header based on the data type.
res.json([body]): Sends a JSON response. It automatically sets the Content-Type to application/json.
res.end([data] [, encoding]): Ends the response process quickly, with optional data and encoding.
res.download(path [, filename] [, fn]): Prompts the user to download a file at the specified path.
Setting HTTP Status Codes:
res.status(code): Sets the HTTP status code for the response (e.g., 200 for OK, 404 for Not Found, 500 for Internal Server Error).
res.sendStatus(statusCode): Sets the status code and sends the corresponding status message as the response body.
Setting Headers and Cookies:
res.set(field [, value]): Sets the value for an HTTP response header.
res.cookie(name, value [, options]): Sets a cookie with the given name and value.
Redirection and Rendering:
res.redirect([status,] path): Redirects the client to a different URL.
res.render(view [, locals] [, callback]): Renders a view template and sends the resulting HTML to the client.

HTTP

Hypertext Transfer Protocol (HTTP) is an application-layer protocol used for transferring hypermedia documents, such as HTML.
It is primarily designed for communication between web browsers and web servers.

It is the main way web browsers and servers communicate to store and retrieve information on the internet.

HTTP works on a request–response system, where the client (browser) requests information and the server responds with the required data.

URL (Uniform Resource Locator) :-
A URL is a unique identifier used to locate a resource on the internet.

API (Application Programming Interface)
An API is a set of rules and protocols that enables software applications to communicate with each other to exchange data, features, and functionality.

REST API
A REST API, also known as a RESTful API, is an Application Programming Interface that follows the design principles of the REST (Representational State Transfer) architectural style.
A REST API provides a flexible and lightweight way to integrate web applications and connect different components, especially in microservices architecture.

HTTP Headers
HTTP headers allow the client and the server to pass additional information along with an HTTP request or response.
An HTTP header consists of a case-insensitive name, followed by a colon (:), and then the header value.

Example: Content-Type: application/json

Types of HTTP Headers
HTTP headers are mainly divided into 4 types:

1. Request Headers – Sent by the client to the server, containing information like browser type, formats accepted, etc.
2. Response Headers – Sent by the server to the client with information like server details, caching policies, etc.
3. General Headers – Can be used in both request and response; include general instructions.
4. Entity Headers – Provide information about the body/content of the resource, like its type and length.

Content-Type (HTTP Header):-
The Content-Type header is used to indicate the media type (format) of the resource being sent to the client or server.
It tells the recipient what type of data is being transferred, so it knows how to process it.

Examples of Common Content-Type Values
Content-Type Description
text/plain Plain text file (no formatting)
text/html HTML file
text/css CSS file
text/javascript JavaScript file
application/json JSON data
application/xml XML data
application/pdf PDF file
application/x-www-form-urlencoded Form data submitted via HTML forms
image/png PNG image
video/mp4 MP4 video
video/webm WebM video
audio/mpeg MP3 audio

HTTP Methods
HTTP methods are typically associated with RESTful web development.
These methods are commonly used by REST API designers to perform different operations on resources.

Method Description / Use
GET Retrieve data from the server
POST Create a new resource
PUT Update an existing resource (replace fully)
PATCH Update part of a resource
DELETE Remove a resource

HTTP Status Codes

HTTP response status codes indicate whether a specific HTTP request has been successfully completed or not.
These are three-digit codes sent by the server to the client based on the request result.

Status Codes are divided into 5 classes:

Class Range Meaning
1xx – Informational 100 – 199 Request received and processing continues
2xx – Successful 200 – 299 Request successfully received, understood, and processed
3xx – Redirection 300 – 399 Further action or redirection needed
4xx – Client Error 400 – 499 Request contains bad syntax or cannot be fulfilled
5xx – Server Error 500 – 599 Server failed to fulfill a valid request

Code Meaning
100 Continue
101 Switching Protocols

Code Meaning
200 OK
201 Created
202 Accepted
204 No Content

Code Meaning
301 Moved Permanently
308 Permanent Redirect

Code Meaning
400 Bad Request
401 Unauthorized
402 Payment Required
403 Forbidden
404 Not Found
408 Request Timeout
409 Conflict (Occurs when a request conflicts with current state of server resource)

Code Meaning
500 Internal Server Error
502 Bad Gateway
503 Service Unavailable

Express Middleware
Express middleware refers to functions that are executed by the Express server during the request–response cycle, before the final response is sent.

Express middleware consists of functions that have access to the request object (req), the response object (res), and a special function called next().

These functions can:

- Modify the request and response objects
- Terminate the request–response cycle
- Or pass control to the next middleware in the stack using next()

As the name suggests, middleware functions execute between the initial request and the final response.
In Express, middleware functions run in the order they are declared in the program.

Example Code:-
app.use((req, res, next) => {
console.log("Middleware executed");
next();
});

Advantages of Middleware Functions

1. Modularity
   Middleware allows developers to organize code by breaking down application logic into smaller, manageable functions.
2. Request–Response Processing
   Middleware functions can intercept and modify incoming requests and outgoing responses, enabling tasks such as authentication, logging, and data validation.
3. Extensibility
   Developers can easily extend or enhance the functionality of an application by adding or removing middleware functions.
4. Reusability
   Middleware functions are reusable components that can be applied to different routes or across multiple applications, promoting code reuse.
5. Error Handling
   Middleware can handle errors globally or for specific routes, improving the overall robustness of the application.

Middleware Chaining
Middleware functions in Express can be chained together, creating a sequence of functions that are executed in order.

- Each middleware function can process the request and modify the request or response objects.
- The last function in the chain usually sends the final response back to the browser.
- Intermediate middleware can perform tasks like authentication, logging, or data validation before the final response is sent.

Types of Middleware in Express

1.Application-level Middleware

- Applied to the entire application using app.use() or app.METHOD()
- Example: Logging, authentication

  2.Router-level Middleware

- Applied to specific routers using express.Router()
- Helps organize middleware for specific route groups

  3.Error-handling Middleware

- Handles errors globally or for specific routes
- Signature: (err, req, res, next)

  4.Built-in Middleware

- Middleware provided by Express itself
- Examples: express.json(), express.urlencoded(),express,static()

  A) Express static Middleware
  The express.static middleware is used to serve static files such as HTML, CSS, JavaScript, images, etc., from a directory to the browser.

Syntax:- app.use(express.static('folder_path'));

B) Express express.json() Middleware
The express.json() middleware is used to parse incoming JSON requests.
It converts the JSON data in the request body into a JavaScript object and makes it available via req.body.

Syntax
app.use(express.json());

C) Express express.urlencoded() Middleware
The express.urlencoded() middleware is used to parse incoming URL-encoded form data.
It makes the form data available in the req.body object.

Syntax
app.use(express.urlencoded({ extended: true }));

- extended: true allows parsing of nested objects.
- extended: false parses simple key-value pairs.

  5.Third-party Middleware in Express
  Third-party middleware allows an Express server to use external libraries or packages from npm to extend server functionality.

Benefits of Third-party Middleware
1.Improving Performance
2.Secure Data Communication
3.Database and Network Connections

Some Popular Third-party Middleware

1. body-parser

- Purpose: Parses the body of incoming requests with payloads and makes it available in req.body.
- Installation:

npm i body-parser

2. cookie-parser

- Purpose: Parses Cookie headers and populates req.cookies with an object keyed by cookie names.
- Installation:

npm i cookie-parser

- Usage:

const cookieParser = require("cookie-parser");

// Use cookie-parser middleware
app.use(cookieParser());

3. CORS (Cross-Origin Resource Sharing)

- Purpose: Solves CORS policy errors by allowing or restricting requests from other origins.
- Installation:

npm i cors

- Usage:

const cors = require("cors");

// Enable CORS for all routes
app.use(cors());

Template Engines in Express
One of the key features of Express is its ability to integrate with template engines, allowing developers to dynamically generate HTML pages with data from their server.
A template engine enables you to use static template files in your application. At runtime, it replaces variables in a template file with actual values and transforms the template into an HTML file that is sent to the client.
This allows you to separate your presentation (HTML) from your application logic (JavaScript/Node.js), making your code cleaner and easier to maintain.

Using EJS Template Engine in Express
EJS stands for Embedded JavaScript. It allows you to embed JavaScript code in your HTML pages.

Installation
npm i ejs

Setting Up EJS in Express

const express = require('express');
const app = express();
const path = require('path');

// Set the template engine to EJS
app.set('view engine', 'ejs');

// Set the directory where template files are located (optional, default is 'views')
app.set('views', path.join(\_\_dirname, 'views'));

MVC (Model-View-Controller)
MVC stands for Model, View, Controller.
It is an architectural pattern that separates an application into three main logical components:

1. Model
   - Represents the data and the business logic of the application.
   - Handles database interactions, data validation, and data manipulation.
2. View
   - Represents the presentation layer or the UI.
   - Displays data to the user and sends user input to the controller.
3. Controller
   _ Acts as an intermediary between the Model and the View.
   _ Processes user input, updates the model, and selects which view to display.
   Purpose:

- Helps separate concerns in an application, making it easier to manage, scale, and maintain.

Advantages of Using MVC Architecture

1. Easy to Test and Debug
   - Each component (Model, View, Controller) is separated, making it easier to identify and fix issues.
2. Clean and Organized Code
   - Separation of concerns ensures code is structured and readable.
3. Separation of Server Logic and Presentation
   - The business logic (Model) is separate from the user interface (View), reducing code clutter.
4. Improves Scalability
   - New features can be added or existing ones modified without affecting other components.
5. Enhances Productivity and Collaboration
   - Developers can work on different components simultaneously (e.g., frontend and backend teams).
6. Easy to Maintain and Update Server Functionalities
   - Changes in one component (e.g., updating the database structure) usually don’t impact other parts of the application.

Authentication vs Authorization

1. Authentication

- Definition: The process of verifying the identity of a user or system before granting access.
- Purpose: To ensure that the user is who they claim to be.
- When it happens: Before authorization.
- How it works:
  - Users provide credentials such as username and password.
  - Can also use multi-factor authentication (MFA) methods like fingerprint, retina scan, or OTP.

2. Authorization

- Definition: The process of checking whether an authenticated user has permission to access a specific resource.
- Purpose: To control what an authenticated user can or cannot do in the system.
- When it happens: After authentication.
- How it works:
  - User privileges, roles, or access rights are verified.
  - Access may be restricted to certain pages, data, or functions./

MongoDB

MongoDB is an open-source, cross-platform, document-oriented database program designed to store a large scale of data and work efficiently with it.
It is a NoSQL database, which means that the data in MongoDB is not stored in the form of tables (like relational databases such as MySQL or PostgreSQL).

MongoDB uses a document storage format called BSON (Binary JSON), which is a binary representation of JSON documents.
BSON documents make MongoDB well-suited for handling large volumes of unstructured and semi-structured data.

| Feature     | Description                             |
| ----------- | --------------------------------------- |
| Type        | NoSQL, Document-oriented                |
| Format      | BSON (Binary JSON)                      |
| Structure   | Stores data as documents in collections |
| Flexibility | No fixed schema                         |
| Scale       | Handles large-scale data efficiently    |

Advantages

1)Highly flexible and scalable

2)Stores JSON-like documents

3)Fast read and write operations

4)Great for real-time applications

5)Works well with modern applications like MERN stack

| **SQL**                                              | **NoSQL**                                                         |
| ---------------------------------------------------- | ----------------------------------------------------------------- | --- |
| Relational database (table-based)                    | Non-relational database (JSON/document, key-value, graph, column) |
| Fixed schema                                         | Flexible / dynamic schema                                         |
| Vertically scalable (increase RAM/CPU of one server) | Horizontally scalable (add more servers)                          |
| Best for structured data                             | Best for unstructured or semi-structured data                     |     |
| Examples: MySQL, PostgreSQL, Oracle                  | Examples: MongoDB, Cassandra, Firebase, Redis                     |

| **JSON**                                     | **BSON**                                                          |
| -------------------------------------------- | ----------------------------------------------------------------- |
| JSON stands for _JavaScript Object Notation_ | BSON stands for _Binary JSON (Binary JavaScript Object Notation)_ |
| Stored in **text-based** format              | Stored in **binary** format                                       |
| **Indexes cannot be built** efficiently      | **Indexes can be built** efficiently                              |
| **Slower** in data retrieval & parsing       | **Faster** in data retrieval & parsing                            |
| Uses **less space** compared to BSON         | Uses **more space** compared to JSON                              |
| Supports **basic data types only**           | Supports **additional data types** (e.g., Date, Binary, ObjectId) |

Short explanation
JSON is human-readable and used mostly for APIs and configurations.

BSON is optimized for performance and used in MongoDB to store documents efficiently.

MongoDB Commands in PowerShell

| **Command**                             | **Description**                                |
| --------------------------------------- | ---------------------------------------------- |
| `mongod --version`                      | Shows MongoDB server version                   |
| `mongosh --version`                     | Shows MongoDB Shell version                    |
| `mongosh`                               | Opens the MongoDB shell environment            |
| `show dbs`                              | Displays all available databases               |
| `use databaseName`                      | Creates or switches to a database              |
| `show collections`                      | Shows collections inside the selected database |
| `db.createCollection("collectionName")` | Creates a new collection                       |
| `db.collectionName.drop()`              | Deletes a specific collection                  |
| `db.dropDatabase()`                     | Deletes the current database                   |
| `cls`                                   | Clears the PowerShell terminal                 |

CRUD Operations in MongoDB

| **Operation**       | **Command**                                                            | **Description**                 |
| ------------------- | ---------------------------------------------------------------------- | ------------------------------- |
| **Create (Insert)** | `db.collectionName.insertOne({ })`                                     | Inserts a single document       |
|                     | `db.collectionName.insertMany([{ }, { }])`                             | Inserts multiple documents      |
| **Read (Find)**     | `db.collectionName.findOne({ key: value })`                            | Finds one matching document     |
|                     | `db.collectionName.find({ key: value })`                               | Finds all matching documents    |
| **Update**          | `db.collectionName.updateOne({ filter }, { $set: { field: value } })`  | Updates first matching document |
|                     | `db.collectionName.updateMany({ filter }, { $set: { field: value } })` | Updates all matching documents  |
| **Delete**          | `db.collectionName.deleteOne({ filter })`                              | Deletes first matching document |
|                     | `db.collectionName.deleteMany({ filter })`                             | Deletes all matching documents  |

Other Operations in MongoDB

| **Operation**        | **Command**                                                                  | **Description**                                                        |
| -------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Replace**          | `db.collectionName.replaceOne({ filter }, { newDocument })`                  | Replaces the entire existing document with a new one                   |
| **Find and Delete**  | `db.collectionName.findOneAndDelete({ filter })`                             | Finds a matching document and deletes it                               |
| **Find and Update**  | `db.collectionName.findOneAndUpdate({ filter }, { $set: { field: value } })` | Finds a document and updates it, returning the old document by default |
| **Find and Replace** | `db.collectionName.findOneAndReplace({ filter }, { newDocument })`           | Finds a document and replaces it with a new one                        |

Query Methods in MongoDB

| **Method**      | **Syntax**                                   | **Description**                                      |
| --------------- | -------------------------------------------- | ---------------------------------------------------- |
| **limit()**     | `db.collection.find().limit(number)`         | Limits the number of documents returned              |
| **skip()**      | `db.collection.find().skip(number)`          | Skips the given number of documents                  |
| **sort()**      | `db.collection.find().sort({ field: 1/-1 })` | Sorts the result: `1 = Ascending`, `-1 = Descending` |
| ** projection** | `db.collection.find({}, { field: 1/0 })`     | Includes or excludes specific fields                 |
| **count()**     | `db.collection.find().count()`               | Returns the number of matching documents             |

MongoDB Comparison Operators

| **Operator** | **Meaning / Description**                                 | **Example Query**                                        |
| ------------ | --------------------------------------------------------- | -------------------------------------------------------- |
| **$eq**      | Matches values equal to a specified value                 | `db.users.find({ field: { $eq: 25 } })`                  |
| **$ne**      | Matches values not equal to a specified value             | `db.users.find({ field: { $ne: "active" } })`            |
| **$gt**      | Matches values greater than a specified value             | `db.users.find({ field: { $gt: 18 } })`                  |
| **$gte**     | Matches values greater than or equal to a specified value | `db.users.find({ field: { $gte: 18 } })`                 |
| **$lt**      | Matches values less than a specified value                | `db.users.find({ field: { $lt: 500 } })`                 |
| **$lte**     | Matches values less than or equal to a specified value    | `db.users.find({ field: { $lte: 500 } })`                |
| **$in**      | Matches any value from a given array                      | `db.users.find({ field: { $in: ["Mumbai", "Delhi"] } })` |

Logical Operators in MongoDB

| **Operator** | **Meaning / Description**                               | **Example Query**                                                          |
| ------------ | ------------------------------------------------------- | -------------------------------------------------------------------------- |
| **$and**     | Returns documents only when **all conditions** are true | `db.users.find({ $and: [ { field: { $gt: 18 } }, { field: "Mumbai" } ] })` |
| **$or**      | Returns documents when **any one condition** is true    | `db.users.find({ $or: [ { field: "admin" }, { field: "manager" } ] })`     |
| **$nor**     | Returns documents when **all conditions are false**     | `db.users.find({ $nor: [ { field: "active" }, { field: "Delhi" } ] })`     |
| **$not**     | Returns documents where the condition is **not true**   | `db.users.find({ field: { $not: { $gt: 18 } } })`                          |

Update Query Operators in MongoDB

| **Operator** | **Meaning / Description**            | **Example Usage**                                                           |
| ------------ | ------------------------------------ | --------------------------------------------------------------------------- |
| **$rename**  | Renames a field                      | `db.users.updateOne({ name: "Rahul" }, { $rename: { "mobile": "phone" } })` |
| **$set**     | Sets or updates the value of a field | `db.users.updateOne({ name: "Rahul" }, { $set: { city: "Mumbai" } })`       |
| **$unset**   | Removes a field from a document      | `db.users.updateOne({ name: "Rahul" }, { $unset: { address: "" } })`        |

Indexing in MongoDB

Indexing in MongoDB improves the performance of queries by allowing the database to quickly locate the required data without scanning every document in a collection.

| **Point**                   | **Description**                                                            |
| --------------------------- | -------------------------------------------------------------------------- |
| Faster Querying             | Indexes help MongoDB search and retrieve data faster                       |
| Stores Sorted Data          | Indexes store a small portion of the collection data in a sorted structure |
| Efficient Search            | MongoDB finds matching documents easily instead of scanning all records    |
| Uses Special Data Structure | Indexes store ordered information separately for quick access              |
| Without Index               | MongoDB must scan every document (called **Collection Scan**)              |

Why Indexing is Needed?

Without indexing, MongoDB checks every single document in a collection to find the required result, which is slow for large datasets.

With indexing, MongoDB directly jumps to the matching records, improving search speed and performance.

Syntax:-
db.collection.createIndex({ fieldName: 1 }) // ascending order
db.collection.createIndex({ fieldName: -1 }) // descending order

Example
db.users.createIndex({ age: 1 }) // Index on 'age' in ascending order
db.users.createIndex({ name: -1 }) // Index on 'name' in descending order

Get Index in MongoDB

The getIndexes() method in MongoDB provides a description of all indexes that exist in a given collection.
It helps you check which fields have indexes and their properties.

Syntax
db.collectionName.getIndexes();

Example
db.users.getIndexes();

Drop an Index in MongoDB

MongoDB provides the dropIndex() method to remove an existing index from a collection.
This is useful when an index is no longer needed or affects write performance.

Syntax
db.collection.dropIndex({ fieldName: 1 }) // Drop index on a specific field

Example
// Drop index on 'age' field
db.users.dropIndex({ age: 1 })

MongoDB Connectivity

MongoDB can connect to a server locally or remotely using different methods, including database drivers.

What is a Database Driver?

A database driver is a software component that allows applications to interact with a specific Database Management System (DBMS).
It acts as a bridge between your application and the database, enabling:

Communication between the app and database

Data exchange in a standardized and easier way

What is ODM?

ODM stands for Object Document Mapper.

It is a tool that allows developers to interact with MongoDB databases using programming language objects, typically in JavaScript.

ODM maps objects in an application to documents in a MongoDB collection.

It works similarly to ORM (Object-Relational Mapping) but for NoSQL/document databases.

Purpose of ODM

Abstracts the MongoDB query language.

Allows developers to work with native objects instead of raw database commands.

Handles CRUD operations and schema management efficiently.

Mongoose ODM

Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js.

It helps to:

Manage relationships between data

Provide Schema validation

Translate JavaScript objects into MongoDB documents

1. What is a Schema in Mongoose?

A Schema in Mongoose defines the structure and properties of documents in a MongoDB collection.

It specifies: Expected fields ,Data types ,Default values ,Validators ,Indexes

A Schema is like a blueprint for your collection.

Example of a Schema
const mongoose = require('mongoose');
const userSchema = new mongoose.Schema({
name: { type: String, required: true },
age: { type: Number, default: 18 },
email: { type: String, unique: true },
password: { type: String}
});

2. What is a Model in Mongoose?

A Model is a wrapper around a Schema that provides an interface to interact with the database.

While Schema defines the structure, a Model allows you to: Create documents ,Query documents ,Update documents,Delete documents

Schema → Blueprint
Model → Working interface to perform database operations

Example of a Model
const USER = mongoose.model('User', userSchema);

by using this USER we can perform atabase operations
