## **1. Node.js**
**Interview Question:** "What is Node.js and why is it popular?"

**Deep Explanation:** Node.js is a **JavaScript runtime** built on Chrome's V8 engine. It lets you run JavaScript outside browsers on servers. It uses an **event-driven, non-blocking I/O model** which makes it perfect for I/O-heavy applications (APIs, real-time apps, microservices).

**Key Points:**
- Single-threaded but handles concurrency through event loop
- Uses libuv for async operations
- NPM has 2+ million packages
- Perfect for real-time applications

**Simple Example:**
```javascript
// Create a simple HTTP server
const http = require('http');

const server = http.createServer((req, res) => {
    res.writeHead(200, {'Content-Type': 'text/plain'});
    res.end('Hello from Node.js!');
});

server.listen(3000, () => {
    console.log('Server running on port 3000');
});
```

---

## **2. REPL (Read-Eval-Print Loop)**
**Interview Question:** "What is REPL in Node.js?"

**Deep Explanation:** REPL is an interactive shell where you can execute JavaScript code without creating files. It's useful for testing, debugging, and learning.

**Simple Example:**
```bash
$ node
> 2 + 2
4
> const name = "John"
> console.log(`Hello ${name}`)
Hello John
> .exit
```

---

## **3. LibUV**
**Interview Question:** "What is libuv and why is it important?"

**Deep Explanation:** LibUV is a C library that provides Node.js with:
- Event loop implementation
- Thread pool for expensive operations
- Asynchronous I/O operations
- Cross-platform compatibility

**Key Points:**
- Handles file operations, DNS, networking
- Manages thread pool (default 4 threads)
- Makes Node.js non-blocking

**Simple Example:**
```javascript
// File operations use libuv's thread pool
const fs = require('fs');

// This async operation uses libuv
fs.readFile('file.txt', 'utf8', (err, data) => {
    console.log(data);
});
```

---

## **4. Modules**
**Interview Question:** "How do modules work in Node.js?"

**Deep Explanation:** Modules are reusable code blocks. Node.js uses CommonJS module system (require/module.exports). Each file is treated as a separate module.

**Simple Example:**
```javascript
// math.js
exports.add = (a, b) => a + b;
exports.multiply = (a, b) => a * b;

// app.js
const math = require('./math');
console.log(math.add(5, 3));      // 8
console.log(math.multiply(5, 3)); // 15
```

---

## **5. CommonJS**
**Interview Question:** "Explain CommonJS module system"

**Deep Explanation:** CommonJS is the module system Node.js uses. It's synchronous (loads modules when require() is called). Modules are cached after first load.

**Simple Example:**
```javascript
// Exporting
module.exports = function greet(name) {
    return `Hello ${name}`;
};

// or
exports.sayHello = function(name) {
    return `Hello ${name}`;
};

// Importing
const greet = require('./greet');
const { sayHello } = require('./greet');
```

---

## **6. Core Modules**
**Interview Question:** "Name some Node.js core modules"

**Deep Explanation:** Built-in modules that come with Node.js installation. No need to install via npm.

**Simple Examples:**
```javascript
// fs - File System
const fs = require('fs');
fs.readFile('file.txt', 'utf8', (err, data) => {
    console.log(data);
});

// path - Path manipulation
const path = require('path');
console.log(path.join('/users', 'john', 'file.txt'));

// http - HTTP server
const http = require('http');

// os - System info
const os = require('os');
console.log('CPU Cores:', os.cpus().length);
```

---

## **7. NPM Modules**
**Interview Question:** "What is NPM and how does it work?"

**Deep Explanation:** Node Package Manager - tool for installing and managing third-party packages.

**Simple Examples:**
```bash
# Basic commands
npm init                    # Create package.json
npm install express         # Install package
npm install express --save  # Install + save to dependencies
npm install nodemon --save-dev # Install as dev dependency
npm update express          # Update package
npm uninstall express       # Remove package
```

```json
// package.json structure
{
  "name": "my-app",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.18.0"
  },
  "devDependencies": {
    "nodemon": "^2.0.0"
  }
}
```

---

## **8. Custom Modules**
**Interview Question:** "How to create custom modules?"

**Deep Explanation:** Create your own modules to organize code. Export using module.exports, import using require().

**Simple Example:**
```javascript
// database.js
const users = [];

module.exports = {
    addUser: (name) => {
        users.push(name);
        return users;
    },
    getUsers: () => users
};

// app.js
const db = require('./database');
db.addUser('John');
console.log(db.getUsers()); // ['John']
```

---

## **9. ReadLine**
**Interview Question:** "How to take user input in Node.js?"

**Deep Explanation:** The readline module provides interface for reading from readable streams (like terminal).

**Simple Example:**
```javascript
const readline = require('readline');

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

rl.question('What is your name? ', (name) => {
    console.log(`Hello, ${name}!`);
    rl.close();
});
```

---

## **10. File System Module**
**Interview Question:** "How to read/write files in Node.js?"

**Deep Explanation:** fs module handles file operations. Has both synchronous and asynchronous methods.

**Simple Examples:**
```javascript
const fs = require('fs');

// Read file
fs.readFile('file.txt', 'utf8', (err, data) => {
    if (err) throw err;
    console.log(data);
});

// Write file
fs.writeFile('output.txt', 'Hello World', (err) => {
    if (err) throw err;
    console.log('File written');
});

// Append to file
fs.appendFile('log.txt', '\nNew entry', (err) => {
    if (err) throw err;
});
```

---

## **11. Write Operations**
**Interview Question:** "Different ways to write files?"

**Simple Examples:**
```javascript
const fs = require('fs');

// 1. Overwrite entire file
fs.writeFile('data.txt', 'New content', (err) => {});

// 2. Append to file
fs.appendFile('log.txt', '\nNew line', (err) => {});

// 3. Write synchronously
fs.writeFileSync('sync.txt', 'Content');

// 4. Stream for large files
const writeStream = fs.createWriteStream('large.txt');
writeStream.write('Line 1\n');
writeStream.write('Line 2\n');
writeStream.end();
```

---

## **12. Async Programming**
**Interview Question:** "Explain async programming in Node.js"

**Deep Explanation:** Node.js is non-blocking. Uses callbacks, promises, async/await for async operations.

**Simple Examples:**
```javascript
// Callback
fs.readFile('file.txt', 'utf8', (err, data) => {
    console.log(data);
});

// Promise
const readFilePromise = (path) => {
    return new Promise((resolve, reject) => {
        fs.readFile(path, 'utf8', (err, data) => {
            if (err) reject(err);
            else resolve(data);
        });
    });
};

// Async/Await
async function readData() {
    try {
        const data = await readFilePromise('file.txt');
        console.log(data);
    } catch (err) {
        console.error(err);
    }
}
```

---

## **13. Phases of Event Loop**
**Interview Question:** "Explain Node.js event loop phases"

**Deep Explanation:** Event loop has 6 phases that execute in order:
1. Timers (setTimeout, setInterval)
2. Pending callbacks
3. Idle, prepare
4. Poll (I/O operations)
5. Check (setImmediate)
6. Close callbacks

**Simple Example:**
```javascript
console.log('Start');

setTimeout(() => console.log('Timer'), 0);
setImmediate(() => console.log('Immediate'));
Promise.resolve().then(() => console.log('Promise'));
process.nextTick(() => console.log('Next Tick'));

console.log('End');

// Output order:
// Start
// End
// Next Tick
// Promise
// Timer
// Immediate
```

---

## **14. Node Architecture**
**Interview Question:** "Explain Node.js architecture"

**Deep Explanation:**
```
Your Code → V8 Engine → Event Loop → LibUV → OS
```

**Key Components:**
- V8: Executes JavaScript
- LibUV: Handles async operations
- Event Loop: Manages execution order
- Thread Pool: For expensive operations

---

## **15. ThreadPool**
**Interview Question:** "Does Node.js use threads?"

**Deep Explanation:** Yes! Node.js has a thread pool (default 4 threads) managed by libuv. Used for:
- File system operations
- DNS lookups
- Crypto operations
- Zlib compression

**Simple Example:**
```javascript
// Increase thread pool size
process.env.UV_THREADPOOL_SIZE = 8;

// Crypto operations use thread pool
const crypto = require('crypto');
crypto.pbkdf2('password', 'salt', 100000, 64, 'sha512', (err, key) => {
    console.log('Done');
});
```

---

## **16. Express.js**
**Interview Question:** "What is Express.js?"

**Deep Explanation:** Minimal web framework for Node.js. Simplifies server creation, routing, middleware.

**Simple Example:**
```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
    res.send('Hello Express!');
});

app.listen(3000, () => {
    console.log('Server started on port 3000');
});
```

---

## **17. Applications of Express**
**Interview Question:** "What can you build with Express?"

**Deep Explanation:**
- REST APIs
- Web applications
- Real-time applications
- Microservices
- Static file servers
- Proxy servers

**Simple Examples:**
```javascript
// REST API
app.get('/api/users', (req, res) => {
    res.json([{id: 1, name: 'John'}]);
});

// Static files
app.use(express.static('public'));

// Template engine
app.set('view engine', 'ejs');
app.get('/profile', (req, res) => {
    res.render('profile', {user: 'John'});
});
```

---

## **18. Request Object in Express**
**Interview Question:** "What is req object in Express?"

**Deep Explanation:** Contains client request information.

**Simple Example:**
```javascript
app.get('/user/:id', (req, res) => {
    console.log(req.params.id);   // Route parameter
    console.log(req.query.name);  // Query parameter
    console.log(req.body);        // Request body (needs middleware)
    console.log(req.headers);     // Request headers
    console.log(req.ip);          // Client IP
});
```

---

## **19. Properties of Request Object**
**Interview Question:** "Name some req properties"

**Simple Examples:**
```javascript
req.method      // HTTP method (GET, POST, etc.)
req.url         // Request URL
req.path        // URL path
req.query       // Query parameters
req.params      // Route parameters
req.body        // Request body
req.headers     // Request headers
req.cookies     // Cookies
req.ip          // Client IP
req.protocol    // HTTP or HTTPS
req.hostname    // Host name
```

---

## **20. Response Object in Express**
**Interview Question:** "What is res object in Express?"

**Deep Explanation:** Used to send response to client.

**Simple Examples:**
```javascript
app.get('/', (req, res) => {
    res.send('Hello');              // Send text
    res.json({message: 'Hello'});   // Send JSON
    res.status(201).send('Created'); // Set status
    res.redirect('/new-path');      // Redirect
    res.sendFile('file.html');      // Send file
    res.cookie('token', 'abc123');  // Set cookie
    res.clearCookie('token');       // Clear cookie
});
```

---

## **21. Properties of Response Object**
**Interview Question:** "Name some res properties"

**Simple Examples:**
```javascript
res.status(code)      // Set status code
res.set(field, value) // Set response header
res.get(field)        // Get response header
res.cookie(name, value) // Set cookie
res.clearCookie(name)   // Clear cookie
res.type(type)        // Set Content-Type
res.send(body)        // Send response
res.json(body)        // Send JSON
res.redirect(url)     // Redirect
```

---

## **22. HTTP**
**Interview Question:** "What is HTTP?"

**Deep Explanation:** HyperText Transfer Protocol - foundation of web communication. Request-Response protocol.

**Simple Example:**
```javascript
// HTTP Request Structure:
// GET /index.html HTTP/1.1
// Host: example.com
// User-Agent: browser

// HTTP Response Structure:
// HTTP/1.1 200 OK
// Content-Type: text/html
// 
// <html>...</html>
```

---

## **23. URL**
**Interview Question:** "What is URL structure?"

**Deep Explanation:** Uniform Resource Locator - address of resource on web.

**Simple Example:**
```
https://user:pass@example.com:8080/path?query=string#fragment
└─┬─┘ └─┬──┘└─┬──┘└──┬──┘└─┬┘└──┬──┘└─┬────┘ └──┬───┘
Scheme  User Pass   Host  Port Path   Query   Fragment
```

```javascript
const url = new URL('https://example.com/path?name=John');
console.log(url.hostname);  // example.com
console.log(url.pathname);  // /path
console.log(url.searchParams.get('name')); // John
```

---

## **24. API**
**Interview Question:** "What is an API?"

**Deep Explanation:** Application Programming Interface - set of rules for software communication.

**Simple Example:**
```javascript
// REST API endpoints
app.get('/api/users', (req, res) => {
    // Get all users
});

app.post('/api/users', (req, res) => {
    // Create user
});

app.get('/api/users/:id', (req, res) => {
    // Get user by ID
});
```

---

## **25. REST API**
**Interview Question:** "What is REST API?"

**Deep Explanation:** Representational State Transfer - architectural style for APIs. Uses HTTP methods for CRUD operations.

**Simple Example:**
```javascript
// CRUD Operations:
// CREATE  - POST   /users
// READ    - GET    /users or /users/:id
// UPDATE  - PUT    /users/:id
// DELETE  - DELETE /users/:id

app.get('/users', getUsers);           // Read all
app.get('/users/:id', getUser);        // Read one
app.post('/users', createUser);        // Create
app.put('/users/:id', updateUser);     // Update
app.delete('/users/:id', deleteUser);  // Delete
```

---

## **26. HTTP Headers**
**Interview Question:** "What are HTTP headers?"

**Deep Explanation:** Metadata sent with requests/responses. Provide additional information.

**Simple Examples:**
```javascript
// Common headers
req.headers['user-agent']    // Client browser
req.headers['content-type']  // Request format
req.headers['authorization'] // Auth token

// Setting headers
res.set('Content-Type', 'application/json');
res.set('Cache-Control', 'no-cache');
```

---

## **27. Types of HTTP Headers**
**Interview Question:** "Types of HTTP headers?"

**Deep Explanation:**
1. **General**: Apply to both request/response (Date, Connection)
2. **Request**: Sent by client (Accept, Authorization)
3. **Response**: Sent by server (Server, Set-Cookie)
4. **Entity**: Describe body (Content-Type, Content-Length)

---

## **28. Content-Type**
**Interview Question:** "What is Content-Type header?"

**Deep Explanation:** Specifies media type of the content.

**Simple Examples:**
```javascript
// Common Content-Types
'text/html'                     // HTML
'application/json'              // JSON
'application/xml'               // XML
'text/plain'                    // Plain text
'multipart/form-data'           // File upload
'application/x-www-form-urlencoded' // Form data

// Setting Content-Type
res.set('Content-Type', 'application/json');
```

---

## **29. Common Content-Type Values**
**Interview Question:** "Name common Content-Type values"

**Simple List:**
- `application/json` - JSON data
- `text/html` - HTML content
- `text/plain` - Plain text
- `application/xml` - XML data
- `multipart/form-data` - File uploads
- `application/pdf` - PDF files
- `image/jpeg` - JPEG images

---

## **30. HTTP Methods**
**Interview Question:** "Explain HTTP methods"

**Deep Explanation:**
- **GET**: Retrieve data (Safe, Idempotent)
- **POST**: Create data (Not safe, Not idempotent)
- **PUT**: Update/replace data (Idempotent)
- **PATCH**: Partial update (Not idempotent)
- **DELETE**: Remove data (Idempotent)
- **HEAD**: Get headers only
- **OPTIONS**: Get allowed methods

**Simple Example:**
```javascript
app.get('/users', getUsers);
app.post('/users', createUser);
app.put('/users/:id', updateUser);
app.patch('/users/:id', updatePartial);
app.delete('/users/:id', deleteUser);
```

---

## **31. HTTP Status Codes**
**Interview Question:** "Explain HTTP status codes"

**Deep Explanation:**
- **1xx**: Informational (100 Continue)
- **2xx**: Success (200 OK, 201 Created)
- **3xx**: Redirection (301 Moved, 304 Not Modified)
- **4xx**: Client Error (400 Bad Request, 404 Not Found)
- **5xx**: Server Error (500 Internal Server Error)

**Simple Examples:**
```javascript
res.status(200).send('Success');
res.status(201).send('Created');
res.status(400).send('Bad Request');
res.status(404).send('Not Found');
res.status(500).send('Server Error');
```

---

## **32. Express Middleware**
**Interview Question:** "What is middleware in Express?"

**Deep Explanation:** Functions that execute during request-response cycle. Can modify req/res, end response, or call next middleware.

**Simple Example:**
```javascript
// Middleware function
const logger = (req, res, next) => {
    console.log(`${req.method} ${req.url}`);
    next(); // Call next middleware
};

// Using middleware
app.use(logger);
```

---

## **33. Advantages of Middleware Functions**
**Interview Question:** "Advantages of middleware?"

**Deep Explanation:**
1. Code reusability
2. Separation of concerns
3. Request/response modification
4. Error handling
5. Security (authentication, logging)
6. Performance monitoring

---

## **34. Application-Level Middleware**
**Interview Question:** "What is application-level middleware?"

**Deep Explanation:** Middleware bound to the Express app instance using app.use() or app.METHOD().

**Simple Examples:**
```javascript
// Global middleware (all routes)
app.use((req, res, next) => {
    console.log('Global middleware');
    next();
});

// Route-specific middleware
app.use('/admin', (req, res, next) => {
    console.log('Admin middleware');
    next();
});
```

---

## **35. Built-in Middleware**
**Interview Question:** "Name built-in Express middleware"

**Deep Explanation:**
1. **express.json()** - Parse JSON bodies
2. **express.urlencoded()** - Parse URL-encoded bodies
3. **express.static()** - Serve static files
4. **express.text()** - Parse text bodies
5. **express.raw()** - Parse raw bodies

**Simple Example:**
```javascript
app.use(express.json()); // Parse JSON
app.use(express.urlencoded({ extended: true })); // Parse form data
app.use(express.static('public')); // Serve static files
```

---

## **36. express.static Middleware**
**Interview Question:** "How to serve static files?"

**Deep Explanation:** Serves static files (HTML, CSS, JS, images) from directory.

**Simple Example:**
```javascript
// Serve files from 'public' folder
app.use(express.static('public'));

// File structure:
// public/
//   ├── index.html
//   ├── style.css
//   └── script.js

// Access at:
// http://localhost:3000/index.html
// http://localhost:3000/style.css
```

---

## **37. express.json Middleware**
**Interview Question:** "How to parse JSON requests?"

**Deep Explanation:** Parses incoming requests with JSON payloads. Populates req.body with parsed data.

**Simple Example:**
```javascript
app.use(express.json()); // Must be before routes

app.post('/api/users', (req, res) => {
    // req.body contains parsed JSON
    console.log(req.body.name);
    console.log(req.body.email);
    res.json({ success: true });
});
```

---

## **38. express.urlencoded() Middleware**
**Interview Question:** "How to parse form data?"

**Deep Explanation:** Parses incoming requests with URL-encoded payloads (like form submissions).

**Simple Example:**
```javascript
app.use(express.urlencoded({ extended: true }));

app.post('/submit-form', (req, res) => {
    // req.body contains form data
    console.log(req.body.username);
    console.log(req.body.password);
    res.send('Form submitted');
});
```

**Note:** `extended: true` allows parsing of rich objects, `extended: false` only supports strings/arrays.

---

## **39. Third-Party Middleware**
**Interview Question:** "Name some third-party middleware"

**Deep Explanation:** Community-created middleware installed via npm.

**Simple Examples:**
```javascript
const morgan = require('morgan');     // Logging
const cors = require('cors');         // CORS
const helmet = require('helmet');     // Security headers
const compression = require('compression'); // Compression

app.use(morgan('dev'));    // Log requests
app.use(cors());           // Enable CORS
app.use(helmet());         // Security headers
app.use(compression());    // Compress responses
```

---

## **40. Body Parser**
**Interview Question:** "What is body-parser?"

**Deep Explanation:** Previously used to parse request bodies. Now built into Express as express.json() and express.urlencoded().

**Simple Example:**
```javascript
// Old way (before Express 4.16)
const bodyParser = require('body-parser');
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));

// New way (Express 4.16+)
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
```

---

## **41. Cookie Parser**
**Interview Question:** "How to handle cookies in Express?"

**Deep Explanation:** Parse Cookie header and populate req.cookies.

**Simple Example:**
```javascript
const cookieParser = require('cookie-parser');
app.use(cookieParser());

app.get('/', (req, res) => {
    // Read cookies
    console.log(req.cookies);
    
    // Set cookie
    res.cookie('username', 'john', { maxAge: 900000 });
    
    // Clear cookie
    res.clearCookie('username');
    
    res.send('Cookie handled');
});
```

---

## **42. CORS (Cross-Origin Resource Sharing)**
**Interview Question:** "What is CORS and how to enable it?"

**Deep Explanation:** Security feature that allows servers to specify which origins can access resources.

**Simple Example:**
```javascript
const cors = require('cors');

// Enable CORS for all origins
app.use(cors());

// Enable for specific origin
app.use(cors({
    origin: 'http://example.com'
}));

// Enable with options
app.use(cors({
    origin: '*',
    methods: ['GET', 'POST'],
    allowedHeaders: ['Content-Type']
}));
```

---

## **43. MVC (Model-View-Controller)**
**Interview Question:** "Explain MVC pattern in Express"

**Deep Explanation:** Architectural pattern separating application into:
- **Model**: Data and business logic
- **View**: UI/presentation layer
- **Controller**: Handles requests, processes data

**Simple Example Structure:**
```
project/
├── models/
│   └── User.js
├── views/
│   └── index.ejs
├── controllers/
│   └── userController.js
└── app.js
```

```javascript
// Model (User.js)
class User {
    constructor(name, email) {
        this.name = name;
        this.email = email;
    }
}

// Controller (userController.js)
exports.getUser = (req, res) => {
    const user = new User('John', 'john@example.com');
    res.render('index', { user });
};

// View (index.ejs)
<h1>Hello <%= user.name %></h1>
```

---

## **44. Template Engine in Express**
**Interview Question:** "What are template engines in Express?"

**Deep Explanation:** Generate HTML dynamically by embedding JavaScript in templates.

**Simple Example:**
```javascript
// Set template engine
app.set('view engine', 'ejs');

// Render template
app.get('/', (req, res) => {
    res.render('index', { 
        title: 'Home Page',
        user: 'John'
    });
});
```

---

## **45. EJS in Express**
**Interview Question:** "How to use EJS in Express?"

**Deep Explanation:** Embedded JavaScript templates. Syntax: `<%= variable %>` outputs value, `<% code %>` executes JS.

**Simple Example:**
```javascript
// Setup
app.set('view engine', 'ejs');

// Route
app.get('/profile', (req, res) => {
    res.render('profile', {
        user: { name: 'John', age: 30 },
        skills: ['JavaScript', 'Node.js', 'Express']
    });
});
```

```html
<!-- profile.ejs -->
<h1>Hello <%= user.name %></h1>
<p>Age: <%= user.age %></p>

<ul>
  <% skills.forEach(skill => { %>
    <li><%= skill %></li>
  <% }) %>
</ul>
```

---

## **46. Authentication vs Authorization**
**Interview Question:** "Difference between authentication and authorization?"

**Deep Explanation:**
- **Authentication**: Who are you? (Login)
- **Authorization**: What can you do? (Permissions)

**Simple Example:**
```javascript
// Authentication (Login)
app.post('/login', (req, res) => {
    const { username, password } = req.body;
    if (username === 'admin' && password === '123') {
        res.send('Authenticated');
    } else {
        res.status(401).send('Unauthorized');
    }
});

// Authorization (Check role)
app.get('/admin', (req, res) => {
    const userRole = 'user'; // Get from session/token
    if (userRole === 'admin') {
        res.send('Admin panel');
    } else {
        res.status(403).send('Forbidden');
    }
});
```

**Summary:**
- **401 Unauthorized**: Authentication failed
- **403 Forbidden**: Authenticated but not authorized
