# Node.js & Express REST API
## MERN Stack Development Course

---

## Introduction to Backend Development

### From Frontend to Full Stack
- You've mastered HTML, CSS, JavaScript, and React
- Frontend runs in the browser (client-side)
- Backend runs on servers (server-side)
- Node.js enables JavaScript on the server

**Question:** What limitations have you encountered when building purely frontend applications?

---

## What is Node.js?

Node.js is a JavaScript runtime built on Chrome's V8 engine that enables JavaScript to run outside the browser.

### Key Features
- **Event-driven**: Handles multiple operations simultaneously
- **Non-blocking I/O**: Doesn't wait for operations to complete
- **Single-threaded**: Uses one main thread with event loop
- **NPM**: World's largest software registry

**Question:** Why might running JavaScript on a server be advantageous compared to other server-side languages?

---

## Node.js vs Browser JavaScript

### What's Different?

| Browser JavaScript | Node.js |
|-------------------|---------|
| window object | global object |
| document object | No DOM |
| Browser APIs | Node.js APIs |
| ES6 modules | CommonJS modules |
| Client-side only | Server-side |

### What's the Same?
- JavaScript syntax
- Data types
- Functions and objects
- ES6+ features

---

## Your First Node.js Application

### Creating a Simple Server

```javascript
// server.js
console.log("Hello from Node.js!");

// Run with: node server.js
```

### Reading System Information

```javascript
const os = require('os');

console.log('Platform:', os.platform());
console.log('CPU Architecture:', os.arch());
console.log('Free Memory:', os.freemem());
```

**Exercise:** Create a Node.js script that displays your computer's network interfaces.

---

## Node.js Module System

### What are Modules?
Modules are reusable pieces of code with encapsulated functionality.

### Types of Modules
1. **Core Modules**: Built into Node.js (fs, http, path)
2. **Local Modules**: Your own files
3. **External Modules**: From NPM

### CommonJS Syntax
```javascript
// Exporting
module.exports = { functionName };

// Importing
const module = require('./module');
```

---

## Slide 6: Creating Custom Modules

### Math Operations Module

```javascript
// mathOperations.js
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;
const multiply = (a, b) => a * b;

module.exports = {
    add,
    subtract,
    multiply
};

// main.js
const math = require('./mathOperations');
console.log(math.add(5, 3)); // 8
```

**Question:** How does this module system compare to ES6 import/export you use in React?

---

## NPM - Node Package Manager

### Essential Commands

```bash
npm init                    # Initialize project
npm install express         # Install package
npm install -D nodemon      # Install dev dependency
npm install -g package      # Install globally
npm uninstall package       # Remove package
```

### package.json
- Project metadata
- Dependencies list
- Scripts configuration
- Version management

**Exercise:** Initialize a new Node.js project and explore the generated package.json file.

---

## Core Node.js Modules - File System

### Reading and Writing Files

```javascript
const fs = require('fs');

// Asynchronous read
fs.readFile('data.txt', 'utf8', (err, data) => {
    if (err) throw err;
    console.log(data);
});

// Synchronous write
try {
    fs.writeFileSync('output.txt', 'Hello World');
} catch (err) {
    console.error(err);
}
```

**Question:** When would you use synchronous vs asynchronous file operations?

---

## Core Node.js Modules - HTTP

### Creating a Basic Web Server

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello World from Node.js Server!');
});

server.listen(3000, () => {
    console.log('Server running on port 3000');
});
```

**Exercise:** Modify the server to return different responses based on the URL path.

---

## Introduction to Express.js

### What is Express?
Express is a minimal and flexible Node.js web application framework.

### Why Express?
- Simplifies server creation
- Robust routing system
- Middleware support
- Template engine integration
- RESTful API development

### Installation
```bash
npm install express
```

---

## Slide 11: Your First Express Server

### Basic Express Application

```javascript
const express = require('express');
const app = express();
const PORT = 3000;

app.get('/', (req, res) => {
    res.send('Hello from Express!');
});

app.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`);
});
```

**Question:** How is this different from the raw Node.js HTTP server we created earlier?

---

## Express Routing Basics

### HTTP Methods & Routes

```javascript
// GET - Retrieve data
app.get('/users', (req, res) => {
    res.json({ users: ['Alice', 'Bob'] });
});

// POST - Create data
app.post('/users', (req, res) => {
    res.status(201).json({ message: 'User created' });
});

// PUT - Update data
app.put('/users/:id', (req, res) => {
    res.json({ message: `User ${req.params.id} updated` });
});

// DELETE - Remove data
app.delete('/users/:id', (req, res) => {
    res.json({ message: `User ${req.params.id} deleted` });
});
```

---

## Understanding Middleware

### What is Middleware?
Functions that execute during the request-response cycle.

### Middleware Structure
```javascript
const myMiddleware = (req, res, next) => {
    console.log('Middleware executed');
    next(); // Pass control to next middleware
};

app.use(myMiddleware);
```

### Common Middleware
```javascript
app.use(express.json());        // Parse JSON bodies
app.use(express.static('public')); // Serve static files
```

**Question:** How might middleware help with authentication or logging?

---

## Request and Response Objects

### Request Object (req)
```javascript
app.get('/users/:id', (req, res) => {
    console.log(req.params.id);    // URL parameters
    console.log(req.query);        // Query strings
    console.log(req.body);         // Request body
    console.log(req.headers);      // Headers
});
```

### Response Object (res)
```javascript
res.send('Text response');
res.json({ data: 'value' });
res.status(404).send('Not found');
res.redirect('/new-path');
```

---

## Building a Complete REST API

### User Management API

```javascript
const express = require('express');
const app = express();

app.use(express.json());

let users = [
    { id: 1, name: 'Alice', email: 'alice@example.com' },
    { id: 2, name: 'Bob', email: 'bob@example.com' }
];

// GET all users
app.get('/api/users', (req, res) => {
    res.json(users);
});

// GET single user
app.get('/api/users/:id', (req, res) => {
    const user = users.find(u => u.id === parseInt(req.params.id));
    if (!user) return res.status(404).json({ error: 'User not found' });
    res.json(user);
});

// POST new user
app.post('/api/users', (req, res) => {
    const newUser = {
        id: users.length + 1,
        name: req.body.name,
        email: req.body.email
    };
    users.push(newUser);
    res.status(201).json(newUser);
});
```

---

## Slide 16: Error Handling in Express

### Error Handling Middleware

```javascript
// Route handler with error
app.get('/api/users/:id', (req, res, next) => {
    try {
        const user = findUser(req.params.id);
        if (!user) throw new Error('User not found');
        res.json(user);
    } catch (error) {
        next(error);
    }
});

// Error handling middleware
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).json({ 
        error: 'Something went wrong!',
        message: err.message 
    });
});
```

**Exercise:** Add error handling to the user creation endpoint for missing required fields.

---

## Environment Variables

### Using dotenv Package

```javascript
// .env file
PORT=3000
DATABASE_URL=mongodb://localhost:27017/myapp
JWT_SECRET=mysecretkey

// app.js
require('dotenv').config();

const PORT = process.env.PORT || 3000;
const dbUrl = process.env.DATABASE_URL;

app.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`);
});
```

**Question:** Why should sensitive information like API keys be stored in environment variables?

---

## CORS Configuration

### Enabling Cross-Origin Requests

```javascript
const cors = require('cors');

// Allow all origins
app.use(cors());

// Specific configuration
app.use(cors({
    origin: 'http://localhost:3001',
    methods: ['GET', 'POST', 'PUT', 'DELETE'],
    credentials: true
}));
```

**Question:** Why is CORS necessary when your React app communicates with your Express API?

---

## Connecting Frontend to Backend

### React Integration Example

```javascript
// Express API endpoint
app.get('/api/products', (req, res) => {
    res.json([
        { id: 1, name: 'Product 1', price: 29.99 },
        { id: 2, name: 'Product 2', price: 39.99 }
    ]);
});

// React component
useEffect(() => {
    fetch('http://localhost:5000/api/products')
        .then(res => res.json())
        .then(data => setProducts(data))
        .catch(err => console.error(err));
}, []);
```

---

## Best Practices & Next Steps

### Best Practices
- Use environment variables for configuration
- Implement proper error handling
- Validate input data
- Use middleware for common functionality
- Structure your code with separate route files
- Document your API endpoints

### Next Steps
- Learn MongoDB integration
- Implement authentication (JWT)
- Explore advanced middleware
- Study deployment strategies
- Practice building full MERN applications

**Question:** What type of application would you like to build with your new Node.js and Express knowledge?

---

## Practical Exercises

### Exercise 1: Basic API
Create a TODO API with endpoints for:
- Creating tasks
- Reading all tasks
- Updating task status
- Deleting tasks

### Exercise 2: Middleware Practice
Build custom middleware for:
- Request logging
- Request timing
- Basic authentication

### Exercise 3: Full Integration
Connect your React frontend to display and manage data from your Express API.
