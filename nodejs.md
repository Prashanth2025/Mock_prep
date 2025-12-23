1. Node.js

- Detailed Explanation:
  Node.js is a JavaScript runtime environment built on Google’s V8 engine. Unlike browsers, which only allow JS for client-side scripting, Node.js lets developers run JS on the server side. It uses an event-driven, non-blocking I/O model, which makes it lightweight and efficient for building scalable applications.
- Single-threaded: Node.js runs on a single thread but uses LibUV to handle asynchronous tasks in the background.
- Use cases: REST APIs, real-time apps (chat, streaming), microservices, CLI tools.
- Why interviewers ask: To test if you understand why Node.js is popular for modern web development.
- Syntax:
  node app.js

- Example:
  // app.js
  console.log("Hello from Node.js");

2. REPL (Read-Eval-Print Loop)

- Detailed Explanation:
  REPL is an interactive shell bundled with Node.js. It allows developers to test snippets of code quickly without creating a file.
- Read: Accepts user input.
- Eval: Evaluates the input.
- Print: Prints the result.
- Loop: Waits for the next input.
- Why interviewers ask: To check if you know how to debug/test code quickly in Node.
- Syntax:
  node

- Example:
  > let x = 5;
  > x \* 2
  > 10

3. LibUV

- Detailed Explanation:
  LibUV is a C library that powers Node.js’s asynchronous capabilities. It manages the event loop, thread pool, and non-blocking I/O.
- Handles file system operations, DNS lookups, networking.
- Provides cross-platform support (Windows, Linux, macOS).
- Why interviewers ask: To see if you understand what makes Node.js async and scalable.

4. Modules

- Detailed Explanation:
  Modules are reusable blocks of code in Node.js. They help organize code into smaller, manageable pieces.
- Types: Core modules, npm modules, custom modules.
- Why interviewers ask: To check if you can structure projects properly.
- Syntax:
  const fs = require('fs'); // importing core module

- Example:
  // math.js
  exports.add = (a,b) => a+b;

// app.js
const math = require('./math');
console.log(math.add(2,3));

5. CommonJS

- Detailed Explanation:
  CommonJS is the module system used in Node.js. It uses require() to import and module.exports to export.
- Why important: Before ES6 modules (import/export), CommonJS was the standard.
- Why interviewers ask: To test if you know the difference between CommonJS and ES Modules.
- Example:
  // utils.js
  module.exports = {
  greet: name => `Hello ${name}`
  };

// app.js
const utils = require('./utils');
console.log(utils.greet("Prashanth"));

6. Core Modules

- Detailed Explanation:
  Node.js ships with built-in modules (no need to install).
- Examples:
- fs → File system operations
- http → Create servers
- path → Handle file paths
- os → System info
- Why interviewers ask: To check if you can use built-in tools instead of reinventing the wheel.
- Example:
  const os = require('os');
  console.log("Platform:", os.platform());
  console.log("Free Memory:", os.freemem());

7. NPM Modules

- Detailed Explanation:
  NPM (Node Package Manager) is the default package manager for Node.js. It allows developers to install, share, and manage external libraries.
- Local vs Global: Local modules are installed inside a project (node_modules), while global modules are installed system-wide.
- Semantic Versioning: NPM uses major.minor.patch (e.g., 1.2.3) to track versions.
- Why interviewers ask: To check if you know how to manage dependencies in real-world projects.
- Syntax:
  npm install lodash
  npm install express --save
  npm install nodemon -g

- Example:
  const _ = require('lodash');
  console.log(_.capitalize("prashanth")); // Output: Prashanth

8. Custom Modules

- Detailed Explanation:
  Custom modules are user-defined modules that encapsulate logic for reuse. They help in code organization and maintainability.
- Exporting: Use module.exports to expose functionality.
- Importing: Use require() to load the module.
- Why interviewers ask: To test if you can structure large applications into smaller files.
- Example:
  // greet.js
  module.exports = function(name){
  return `Hello, ${name}`;
  };

// app.js
const greet = require('./greet');
console.log(greet("Prashanth"));

9. ReadLine

- Detailed Explanation:
  The readline module provides an interface for reading data from a readable stream (like process.stdin). Useful for CLI applications.
- Supports synchronous user input.
- Can be combined with async logic for interactive tools.
- Why interviewers ask: To see if you know how to build command-line utilities.
- Example:
  const readline = require('readline');
  const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
  });

rl.question("Enter your age: ", age => {
console.log(`You are ${age} years old`);
rl.close();
});

10. File System Module

- Detailed Explanation:
  The fs module allows interaction with the file system. It supports both synchronous and asynchronous methods.
- Common operations: Read, write, append, delete, rename.
- Why interviewers ask: To test if you can handle files in Node.js.
- Example:
  const fs = require('fs');

// Asynchronous read
fs.readFile('test.txt','utf8',(err,data)=>{
if(err) throw err;
console.log(data);
});

// Synchronous read
const content = fs.readFileSync('test.txt','utf8');
console.log(content);

11. Write

- Detailed Explanation:
  Writing files in Node.js can be done using fs.writeFile (async) or fs.writeFileSync (sync).
- If the file doesn’t exist, it creates one.
- If it exists, it overwrites content unless you use fs.appendFile.
- Why interviewers ask: To check if you understand persistence in Node.js.
- Example:
  const fs = require('fs');

// Asynchronous write
fs.writeFile('output.txt','Hello World',(err)=>{
if(err) throw err;
console.log("File written successfully!");
});

// Append
fs.appendFile('output.txt','\nNew Line',(err)=>{
if(err) throw err;
console.log("Line appended!");
});

12. Async

- Detailed Explanation:
  Asynchronous programming is the backbone of Node.js. Instead of blocking execution, async operations allow other tasks to run while waiting for I/O.
- Callbacks: Traditional way of handling async tasks.
- Promises: Cleaner way to handle async results.
- Async/Await: Modern syntax for writing async code that looks synchronous.
- Why interviewers ask: To test if you can handle concurrency and avoid callback hell.
- Example (Callback):
  fs.readFile('data.txt','utf8',(err,data)=>{
  if(err) throw err;
  console.log(data);
  });

- Example (Promise):
  const fetchData = () => Promise.resolve("Data loaded");
  fetchData().then(console.log);

- Example (Async/Await):
  async function getData(){
  return "Data loaded";
  }
  (async ()=>{
  const result = await getData();
  console.log(result);
  })();

13. Phases of Event Loop

- Detailed Explanation:
  The event loop is the mechanism that allows Node.js to perform non-blocking I/O operations. It continuously checks for tasks and executes them in phases.
- Phases:
- Timers → Executes callbacks scheduled by setTimeout and setInterval.
- Pending Callbacks → Executes I/O callbacks deferred from the previous cycle.
- Idle/Prepare → Internal use, prepares for the poll phase.
- Poll → Retrieves new I/O events, executes related callbacks.
- Check → Executes setImmediate() callbacks.
- Close Callbacks → Executes close events like socket.on('close').
- Why interviewers ask: To test if you understand Node’s async nature and scheduling.
- Example:
  setTimeout(()=>console.log("Timer phase"),0);
  setImmediate(()=>console.log("Check phase"));
  console.log("Main thread");

  14. Node Architecture

- Detailed Explanation:
  Node.js architecture is single-threaded, built on the event loop and LibUV.
- Components:
- V8 Engine → Executes JavaScript.
- LibUV → Handles async I/O and thread pool.
- Event Loop → Manages execution order.
- C++ Bindings → Bridge between JS and system calls.
- Why interviewers ask: To check if you understand why Node.js is scalable despite being single-threaded.
- Diagram (conceptual):
  JS Code → V8 Engine → Event Loop → LibUV → OS Resources

  15. ThreadPool

- Detailed Explanation:
  Node.js uses a thread pool (default size: 4) managed by LibUV for expensive operations.
- Tasks handled: File system I/O, DNS lookups, crypto operations.
- Configurable: Can be increased using UV_THREADPOOL_SIZE.
- Why interviewers ask: To see if you know how Node handles heavy tasks without blocking the main thread.
- Example:
  UV_THREADPOOL_SIZE=8 node app.js

  16. Express.js

- Detailed Explanation:
  Express.js is a minimal and flexible web framework for Node.js. It simplifies server creation and routing.
- Features: Middleware support, routing, template engines, REST API support.
- Why interviewers ask: To check if you can build scalable web apps using Express.
- Syntax:
  const express = require('express');
  const app = express();

app.get('/', (req,res)=>res.send("Hello Express"));
app.listen(3000, ()=>console.log("Server running"));

17. Applications of Express

- Detailed Explanation:
  Express is widely used for:
- Building REST APIs.
- Serving static files.
- Integrating with template engines (EJS, Pug).
- Handling middleware (logging, authentication).
- Why interviewers ask: To check if you know practical use cases of Express.
- Example:
  // REST API with Express
  app.get('/users',(req,res)=>{
  res.json([{id:1,name:"Prashanth"}]);
  });

18. Request Object in Express

- Detailed Explanation:
  The req object represents the HTTP request. It contains details about the client’s request.
- Common properties:
- req.query → Query parameters (?name=Prashanth).
- req.params → Route parameters (/user/:id).
- req.body → Request body (POST data).
- req.headers → Request headers.
- Why interviewers ask: To test if you can extract client data properly

- Example:
  app.get('/user/:id',(req,res)=>{
  console.log("Params:", req.params.id);
  console.log("Query:", req.query.name);
  res.send("Request received");
  });

19. Properties of Request Object

- Detailed Explanation:
  The req object in Express represents the incoming HTTP request. It contains all the information sent by the client.
- Key Properties:
- req.query → Holds query string parameters (/search?name=Prashanth).
- req.params → Holds route parameters (/user/:id).
- req.body → Holds POST request body (requires middleware like express.json()).
- req.headers → Contains request headers (like Content-Type, Authorization).
- req.method → HTTP method used (GET, POST, etc.).
- req.url → The full URL of the request.
- Why interviewers ask: To check if you can extract client data properly in APIs.
- Example:
  app.get('/user/:id',(req,res)=>{
  console.log("Params:", req.params.id);
  console.log("Query:", req.query.name);
  console.log("Headers:", req.headers);
  res.send("Request processed");
  });

20. Response Object in Express

- Detailed Explanation:
  The res object represents the HTTP response that the server sends back to the client.
- Key Methods:
- res.send() → Sends a response (string, object, buffer).
- res.json() → Sends JSON data.
- res.status() → Sets HTTP status code.
- res.redirect() → Redirects to another URL.
- res.sendFile() → Sends a file as response.
- Why interviewers ask: To test if you know how to send different types of responses.
- Example:
  app.get('/info',(req,res)=>{
  res.status(200).json({message:"Success", user:"Prashanth"});
  });

21. Properties of Response Object

- Detailed Explanation:
  The res object has properties and methods to control the response.
- res.headersSent → Boolean indicating if headers are already sent.
- res.locals → Stores local variables scoped to the request.
- res.app → Reference to the Express app instance.
- Why interviewers ask: To check if you understand response lifecycle.
- Example:
  app.use((req,res,next)=>{
  res.locals.user = "Prashanth";
  next();
  });

app.get('/',(req,res)=>{
res.send(`Hello ${res.locals.user}`);
});

22. HTTP

- Detailed Explanation:
  HTTP (HyperText Transfer Protocol) is the foundation of communication on the web.
- Request: Sent by client (browser, app).
- Response: Sent by server.
- Stateless: Each request is independent.
- Why interviewers ask: To check if you understand the protocol behind APIs.
- Example (basic HTTP request):
  GET /home HTTP/1.1
  Host: localhost:3000

23. URL

- Detailed Explanation:
  A URL (Uniform Resource Locator) identifies resources on the web.
- Components:
- Scheme → http or https.
- Host → Domain name (example.com).
- Port → Optional (:3000).
- Path → Resource location (/users).
- Query String → Extra parameters (?id=10).
- Why interviewers ask: To check if you can break down and use URLs in routing.
- Example:
  https://example.com:3000/users?id=10

24. API

- Detailed Explanation:
  API (Application Programming Interface) is a set of rules that allows software components to communicate.
- Types: REST, SOAP, GraphQL.
- Why interviewers ask: To check if you understand how systems interact.
- In Node.js/Express: APIs are built using routes and middleware.
- Example:
  app.get('/api/products',(req,res)=>{
  res.json([{id:1,name:"Laptop"},{id:2,name:"Phone"}]);
  });

25. REST API

- Detailed Explanation:
  REST (Representational State Transfer) is an architectural style for designing APIs. It uses HTTP methods to perform CRUD operations on resources.
- Principles:
- Stateless → Each request is independent.
- Resource-based → Everything is treated as a resource (users, products).
- Uniform Interface → Consistent use of HTTP methods.
- Client-Server Separation → Client handles UI, server handles data.
- Why interviewers ask: To check if you understand modern API design.
- Example:
  // REST API with Express
  app.get('/users',(req,res)=>res.json([{id:1,name:"Prashanth"}]));
  app.post('/users',(req,res)=>res.status(201).send("User created"));
  app.put('/users/:id',(req,res)=>res.send("User updated"));
  app.delete('/users/:id',(req,res)=>res.send("User deleted"));

26. HTTP Headers

- Detailed Explanation:
  HTTP headers are metadata sent with requests and responses. They provide additional information about the request/response.
- Types: General, Request, Response, Entity headers.
- Examples:
- Content-Type → Specifies format of body.
- Authorization → Used for authentication.
- Cache-Control → Controls caching behavior.
- Why interviewers ask: To test if you know how to control communication between client and server.
- Example:
  app.get('/data',(req,res)=>{
  res.set('Content-Type','application/json');
  res.send({msg:"Hello"});
  });

27. Types of HTTP Headers

- Detailed Explanation:
- General Headers → Apply to both request and response (Date, Connection).
- Request Headers → Sent by client (Accept, Authorization).
- Response Headers → Sent by server (Server, Set-Cookie).
- Entity Headers → Describe body content (Content-Type, Content-Length).
- Why interviewers ask: To check if you can categorize headers correctly.

28. Content-Type

- Detailed Explanation:
  The Content-Type header specifies the media type of the resource. It tells the client how to interpret the body.
- Examples:
- application/json → JSON data.
- text/html → HTML document.
- multipart/form-data → File uploads.
- Why interviewers ask: To test if you know how to send/receive correct data formats.
- Example:
  app.post('/submit',(req,res)=>{
  res.setHeader('Content-Type','application/json');
  res.send(JSON.stringify({status:"ok"}));
  });

29. Common Content-Type Values

- Detailed Explanation:
- application/json → JSON data.
- text/html → HTML content.
- text/plain → Plain text.
- multipart/form-data → Used for file uploads.
- application/x-www-form-urlencoded → Form submissions.
- Why interviewers ask: To check if you know which content type to use in APIs.

30. HTTP Methods

- Detailed Explanation:
  HTTP methods define the type of operation performed on a resource.
- GET → Retrieve data.
- POST → Create new resource.
- PUT → Update existing resource (replace).
- PATCH → Update partially.
- DELETE → Remove resource.
- HEAD → Retrieve headers only.
- OPTIONS → Check supported methods.
- Why interviewers ask: To test if you can map CRUD operations to HTTP methods.
- Example:
  app.get('/products',(req,res)=>res.send("Fetch products"));
  app.post('/products',(req,res)=>res.send("Create product"));
  app.put('/products/:id',(req,res)=>res.send("Update product"));
  app.delete('/products/:id',(req,res)=>res.send("Delete product"));

31. HTTP Status Codes

- Detailed Explanation:
  HTTP status codes are 3-digit numbers returned by the server to indicate the result of a request. They are grouped into categories:
- 1xx (Informational) → Request received, continuing process.
- 2xx (Success) → Request successfully processed.
- 200 OK → Successful GET.
- 201 Created → Resource created (POST).
- 3xx (Redirection) → Further action needed.
- 301 Moved Permanently, 302 Found.
- 4xx (Client Error) → Problem with client request.
- 400 Bad Request, 401 Unauthorized, 404 Not Found.
- 5xx (Server Error) → Problem with server.
- 500 Internal Server Error, 503 Service Unavailable.
- Why interviewers ask: To check if you can handle errors gracefully in APIs.
- Example:
  app.get('/data',(req,res)=>{
  res.status(200).send("Success");
  });

app.post('/data',(req,res)=>{
res.status(201).send("Resource created");
});

app.get('/error',(req,res)=>{
res.status(404).send("Not Found");
});

32. Express Middleware

- Detailed Explanation:
  Middleware are functions that execute during the request-response cycle. They can modify req and res, perform logging, authentication, or error handling.
- Types: Application-level, built-in, third-party, error-handling.
- Execution order: Middleware runs in the order they are defined.
- Why interviewers ask: To test if you can structure Express apps with reusable logic.
- Syntax:
  app.use((req,res,next)=>{
  console.log("Middleware executed");
  next(); // pass control to next middleware
  });

33. Advantages of Middleware Functions

- Detailed Explanation:
  Middleware provides:
- Code reusability → Common logic reused across routes.
- Separation of concerns → Keeps routes clean.
- Flexibility → Can modify request/response objects.
- Error handling → Centralized error management.
- Security → Authentication and authorization checks.
- Why interviewers ask: To check if you understand why middleware is essential in Express.

34. Application-Level Middleware

- Detailed Explanation:
  Middleware bound to the entire application or specific routes.
- Global middleware → Runs for all routes.
- Route-specific middleware → Runs only for certain routes.
- Why interviewers ask: To see if you can apply middleware selectively.
- Example:
  // Global middleware
  app.use((req,res,next)=>{
  console.log("Global middleware");
  next();
  });

// Route-specific middleware
app.use('/user',(req,res,next)=>{
console.log("User route middleware");
next();
});

35. Built-in Middleware

- Detailed Explanation:
  Express provides built-in middleware for common tasks:
- express.json() → Parse JSON bodies.
- express.urlencoded() → Parse URL-encoded bodies.
- express.static() → Serve static files.
- Why interviewers ask: To check if you know how to use built-in tools instead of external packages.

36. express.static Middleware

- Detailed Explanation:
  Used to serve static files (HTML, CSS, JS, images) from a directory.
- Default behavior: Serves files relative to the directory specified.
- Why interviewers ask: To test if you can serve frontend assets with Express.
- Example:
  // Serve files from "public" folder
  app.use(express.static('public'));

// Now /public/style.css can be accessed at http://localhost:3000/style.css

37. express.json Middleware

- Detailed Explanation:
  express.json() is a built-in middleware in Express that parses incoming requests with JSON payloads. It populates req.body with the parsed object.
- Use case: Handling API requests where the client sends JSON data.
- Why interviewers ask: To check if you know how to handle request bodies in REST APIs.
- Example:
  const express = require('express');
  const app = express();

app.use(express.json()); // enables JSON parsing

app.post('/user',(req,res)=>{
console.log(req.body); // parsed JSON
res.send("User data received");
});

38. express.urlencoded() Middleware

- Detailed Explanation:
  express.urlencoded() parses incoming requests with URL-encoded payloads (like form submissions).
- Options:
- extended: true → Uses qs library for rich objects.
- extended: false → Uses querystring library (simpler).
- Why interviewers ask: To check if you can handle form data properly.
- Example:
  app.use(express.urlencoded({extended:true}));

app.post('/form',(req,res)=>{
console.log(req.body); // parsed form data
res.send("Form submitted");
});

39. Third-Party Middleware

- Detailed Explanation:
  Middleware created by the community and installed via npm. They extend Express functionality.
- Examples:
- morgan → Logging requests.
- helmet → Security headers.
- compression → Gzip compression.
- Why interviewers ask: To check if you know how to enhance Express apps with external tools.
- Example:
  const morgan = require('morgan');
  app.use(morgan('dev')); // logs requests

40. Body Parser

- Detailed Explanation:
  Before Express v4.16, body-parser was used to parse request bodies. Now, express.json() and express.urlencoded() replace it.
- Still used in legacy projects.
- Why interviewers ask: To see if you know the evolution of Express middleware.
- Example:
  const bodyParser = require('body-parser');
  app.use(bodyParser.json());
  app.use(bodyParser.urlencoded({extended:true}));

41. Cookie Parser

- Detailed Explanation:
  cookie-parser middleware parses cookies attached to client requests. It populates req.cookies.
- Useful for authentication, sessions, personalization.
- Why interviewers ask: To check if you can handle cookies in web apps.
- Example:
  const cookieParser = require('cookie-parser');
  app.use(cookieParser());

app.get('/cookies',(req,res)=>{
console.log(req.cookies);
res.send("Cookies parsed");
});

42. CORS (Cross-Origin Resource Sharing)

- Detailed Explanation:
  CORS is a mechanism that allows servers to specify which origins (domains) can access their resources.
- Problem solved: Browsers block requests from different origins by default (same-origin policy).
- Why interviewers ask: To check if you know how to enable cross-domain communication in APIs.
- Example:
  const cors = require('cors');
  app.use(cors()); // allows all origins

// Restrict to specific origin
app.use(cors({origin:'http://example.com'}));

43. MVC (Model-View-Controller)

- Detailed Explanation:
  MVC is a design pattern used to structure applications into three interconnected components:
- Model → Represents the data and business logic. Handles database operations.
- View → Represents the UI (HTML, templates). Displays data to the user.
- Controller → Handles requests, processes input, and decides which view/model to use.
- Advantages: Separation of concerns, easier maintenance, scalability.
- Why interviewers ask: To check if you can design applications with clean architecture.
- Example (Express MVC structure):
  project/
  ├── models/user.js
  ├── views/index.ejs
  ├── controllers/userController.js
  └── app.js

// controllers/userController.js
exports.getUser = (req,res)=>{
res.render('index',{name:"Prashanth"});
};

44. Template Engine in Express

- Detailed Explanation:
  Template engines allow rendering dynamic HTML by embedding JS logic inside templates.
- Popular engines: EJS, Pug, Handlebars.
- Use case: Server-side rendering of HTML pages with dynamic data.
- Why interviewers ask: To check if you know how to integrate frontend with backend.
- Example (setup):
  app.set('view engine','ejs');
  app.get('/',(req,res)=>res.render('index',{title:"Home Page"}));

45. EJS in Express

- Detailed Explanation:
  EJS (Embedded JavaScript) is a template engine that lets you embed JS code inside HTML.
- Syntax:
- <%= variable %> → Outputs value.
- <% code %> → Executes JS code without output.
- Why interviewers ask: To test if you can render dynamic content in views.
- Example:
  <!-- views/index.ejs -->
  <html>
    <body>
      <h1>Hello <%= name %></h1>
    </body>
  </html>

// app.js
app.set('view engine','ejs');
app.get('/',(req,res)=>res.render('index',{name:"Prashanth"}));

46. Authentication vs Authorization

- Detailed Explanation:
- Authentication → Process of verifying who a user is.
- Example: Login with username/password, biometrics, OAuth.
- Authorization → Process of verifying what a user can access.
- Example: Admin vs regular user permissions.
- Key Difference: Authentication = identity, Authorization = access rights.
- Why interviewers ask: To test if you understand security fundamentals in web apps.
- Example:
  // Authentication (login)
  app.post('/login',(req,res)=>{
  if(req.body.username==="admin" && req.body.password==="123"){
  res.send("Authenticated");
  } else {
  res.status(401).send("Unauthorized");
  }
  });

// Authorization (role check)
app.get('/admin',(req,res)=>{
const role = "user"; // example role
if(role==="admin"){
res.send("Welcome Admin");
} else {
res.status(403).send("Forbidden");
}
});
