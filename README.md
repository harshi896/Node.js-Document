# Node.js on Ubuntu

![Node.js Logo](https://nodejs.org/static/images/logo.svg)

## Table of Contents

1. [Introduction to Node.js](#introduction-to-nodejs)
    - [What is Node.js?](#what-is-nodejs)
    - [Features of Node.js](#features-of-nodejs)
    - [Use Cases of Node.js](#use-cases-of-nodejs)
2. [Setting Up Node.js on Ubuntu](#setting-up-nodejs-on-ubuntu)
    - [Prerequisites](#prerequisites)
    - [Installing Node.js](#installing-nodejs)
        - [Using the Ubuntu Package Manager](#using-the-ubuntu-package-manager)
        - [Using Node Version Manager (NVM)](#using-node-version-manager-nvm)
    - [Verifying Installation](#verifying-installation)
3. [Basic Usage of Node.js](#basic-usage-of-nodejs)
    - [Running a Simple Script](#running-a-simple-script)
   
4. [Node.js Modules](#nodejs-modules)
    - [Core Modules](#core-modules)
   
5. [Node.js Package Manager (NPM)](#nodejs-package-manager-npm)
    - [Introduction to NPM](#introduction-to-npm)
    - [Installing Packages](#installing-packages)
    
6. [Building a Simple Web Server](#building-a-simple-web-server)
    - [Creating a Basic Server](#creating-a-basic-server)
    - [Handling Requests and Responses](#handling-requests-and-responses)
7. [Asynchronous Programming in Node.js](#asynchronous-programming-in-nodejs)
    - [Callbacks](#callbacks)
    - [Promises](#promises)
    - [Async/Await](#asyncawait)
8. [Conclusion](#conclusion)
9. [Reference Links](#references)
    


---

## Introduction to Node.js

### What is Node.js?
Node.js is a runtime environment that allows you to run JavaScript code on the server side. It is built on Chrome's V8 JavaScript engine and provides an event-driven, non-blocking I/O model, making it lightweight and efficient.

### Features of Node.js
- **Asynchronous and Event-Driven:** All APIs in Node.js are asynchronous, meaning non-blocking.
- **Single-Threaded but Highly Scalable:** Node.js uses a single-threaded model with event looping, which helps handle multiple requests.
- **Fast Execution:** Node.js is built on Google Chrome's V8 JavaScript Engine, making its execution very fast.
- **No Buffering:** Node.js applications never buffer data. They output the data in chunks.

### Use Cases of Node.js
- Real-time applications (e.g., chat applications, online gaming)
- REST APIs
- Single Page Applications (SPAs)
- Data-intensive applications

## Setting Up Node.js on Ubuntu

### Prerequisites
- A system running Ubuntu
- Access to a terminal with sudo privileges

### Installing Node.js

#### Using the Ubuntu Package Manager
1. Update your package index:
    ```bash
    sudo apt update
    ```
    ![sudo apt update](/Screenshot1.png)


2. Install Node.js and npm (Node Package Manager):
    ```bash
    sudo apt install nodejs npm
    ```
    ![nodejs and nvm installation](/Screenshot2.png)

#### Using Node Version Manager (NVM)
1. Install NVM:
    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
    ```
    ![nvm installation](/Screenshot3.png)

2. Load NVM:
    ```bash
    source ~/.bashrc
    ```
    ![reload](/Screenshot4.png)

3. Install the latest version of Node.js:
    ```bash
    nvm install node
    ```
    ![node installation](/Screenshot5.png)

### Verifying Installation
Check the installed version of Node.js and npm:
```bash
node -v
npm -v
```
![node and nvm version check](/Screenshot6.png)

## Basic Usage of Node.js

## Running a Simple Script
Create a file `app.js`:
```javascript
console.log('Hello, Node.js!');
```

Then, run the script using Node.js:
```javascript
node app.js
```



##  Node.js Modules

Node.js has a module system that allows you to organize your code into separate files and reuse them across your application. There are three types of modules in Node.js: core modules, custom modules, and external modules.

### Core Modules
Node.js comes with a set of built-in modules that you can use without any additional installation. These modules provide various functionalities such as file system operations, creating servers, handling streams, and more.

### Common Core Modules
- `fs` (File System): Provides an API for interacting with the file system.
- `http`: Used to create HTTP servers and clients.
- `path`: Utilities for handling and transforming file paths.
- `os`: Provides operating system-related utility methods and properties.
- `events`: Provides the EventEmitter class for handling events.
- `util`: Provides utility functions for debugging and creating custom objects.

#### Example of Using a Core Module
Using the `fs` module to read a file:
```javascript
const fs = require('fs');

fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) {
    console.error(err);
    return;
  }
  console.log(data);
});
```

## Node.js Package Manager (NPM)

NPM (Node Package Manager) is the default package manager for Node.js. It allows you to install, share, and manage dependencies in your Node.js projects.

### Introduction to NPM
NPM is used to manage packages or modules in Node.js applications. It includes a command-line client (CLI) that interacts with a remote registry, enabling you to manage dependencies.

### Installing Packages
- **Installing a Package Globally**

To install a package globally, use the `-g` flag. This makes the package available from anywhere on your system.
```bash
npm install -g nodemon
```
![global package installation](/Screenshot7.png)

## Building a Simple Web Server

Node.js allows you to build web servers using its built-in `http` module. This is an essential aspect of many Node.js applications.

### Creating a Basic Server
Create a file `server.js`:
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello, World!\n');
});

server.listen(3000, '127.0.0.1', () => {
  console.log('Server running at http://127.0.0.1:3000/');
});
```

### Handling Requests and Responses

When building a web server with Node.js, it's essential to handle various types of HTTP requests and provide appropriate responses. This section covers the basics of handling requests and responses in Node.js.

- **Handling Different Routes**
You can handle different routes by inspecting the `req.url` property. Here's an example:

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.url === '/') {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Welcome to the homepage!\n');
  } else if (req.url === '/about') {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Welcome to the about page!\n');
  } else {
    res.statusCode = 404;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Page not found\n');
  }
});

server.listen(3000, '127.0.0.1', () => {
  console.log('Server running at http://127.0.0.1:3000/');
});
```

## Asynchronous Programming in Node.js

Node.js is designed to handle asynchronous operations efficiently. This is achieved through various mechanisms like callbacks, promises, and async/await. Understanding these concepts is crucial for writing efficient Node.js applications.

### Callbacks
Callbacks are the basic way of handling asynchronous operations in Node.js. A callback is a function passed as an argument to another function, to be "called back" at a later time.

- **Example of a Callback**
```javascript
const fs = require('fs');

fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) {
    console.error('Error reading file:', err);
    return;
  }
  console.log('File content:', data);
});
```
### Promises
Promises provide a cleaner way to handle asynchronous operations compared to callbacks. They represent the eventual result of an asynchronous operation.

- **Example of using a promise**
```javascript
const fsPromises = require('fs').promises;

fsPromises.readFile('example.txt', 'utf8')
  .then(data => console.log(data))
  .catch(err => console.error(err));
  ```

### Async/Await
Async/Await is a modern way to write asynchronous code, built on top of promises, and makes the code more readable.

- **Example using async/await**
```javascript
const fs = require('fs').promises;

async function readFile() {
  try {
    const data = await fs.readFile('example.txt', 'utf8');
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}

readFile();
```



## Conclusion

Node.js is a powerful platform for building server-side applications in JavaScript. Throughout this document, we've covered various aspects of Node.js development, from installation and basic usage to advanced topics like asynchronous programming, debugging, and testing.

### Key Takeaways

- **Getting Started**: Node.js allows you to run JavaScript on the server-side, leveraging its event-driven architecture and non-blocking I/O model for high performance.
- **Building Applications**: You can create web servers, handle file operations, and perform network communication using built-in modules like `http`, `fs`, and `net`.
- **Modules and Packages**: Node.js uses a module system that allows you to organize your code into reusable components. You can use built-in modules, create custom modules, and install external packages via npm.
- **Asynchronous Programming**: Understanding callbacks, promises, and async/await is crucial for handling asynchronous operations efficiently in Node.js.
- **Debugging**: Node.js provides built-in debugging tools and integrates with Chrome DevTools for effective debugging of applications.
- **Testing**: Using frameworks like Mocha and assertion libraries like Chai, you can write and automate tests to ensure the reliability and correctness of your code.


## References

Here are some useful resources that I used to make this document:

- [Node.js Official Documentation](https://nodejs.org/en/docs/)
- [MDN Web Docs for JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

