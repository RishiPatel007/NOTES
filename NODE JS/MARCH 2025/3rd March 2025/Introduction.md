# *Node.js*, *npm*, and nvm: Overview

## *Node.js*

*Node.js* is a JavaScript runtime built on Chrome's V8 JavaScript engine that allows you to execute JavaScript code on the server-side. It uses an event-driven, non-blocking I/O model.

Made by Ryan Dahl

*npm* made by **Isaac Z. Schlueter , owned by Github**

Nvm made by Open Js Foundation

**Current Version:** 22.14.0 LTS and 23.9.0 Latest

*npm* is the default package manager for *Node.js*, allowing you to install, share, and manage dependencies.

| **Advantages**                                                          | **Disadvantages**                                                         |
| ----------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Single language (JavaScript) for both client and server                 | Not ideal for CPU-intensive tasks                                         |
| Non-blocking I/O makes it highly efficient for I/O-intensive operations | Callback hell can make code harder to maintain (though async/await helps) |
| Large ecosystem of packages via *npm*                                   | Single-threaded nature (though Worker Threads API helps address this)     |
| Great for real-time applications like chat, gaming servers              |                                                                           |
| Excellent for microservices architecture                                |                                                                           |


## *npm* (Node Package Manager)

**Current Version:** ==11.1.0==

**Advantages:**

- Vast library of open-source packages
- Easy dependency management
- Simple version control for packages
- Built-in security features

**Disadvantages:**

- Can lead to "dependency hell" with complex projects
- Security concerns with third-party packages
- Sometimes creates large node_modules directories

## nvm (Node Version Manager)

nvm is a tool that allows you to manage multiple *Node.js* versions on a single machine.

latest version : 0.40.1

**Advantages:**

- Switch between Node versions easily
- Test applications across different Node versions
- Install and uninstall versions without affecting other projects

---
# Traditional Server vs. *Node.js*

### Traditional Server Model (e.g., Php)

- Uses thread-based approach
- Creates a new thread for each connection
- Blocks while waiting for I/O operations
- Memory usage increases with each connection
- Slows down under high load due to thread limitations

### *Node.js* Model

- Single-threaded event loop
- Non-blocking I/O operations
- Can handle thousands of concurrent connections
- Uses callbacks/promises to handle operations when they complete
- Maintains performance under high load since it doesn't wait for operations to complete

---
# HTTP and Its Methods

HTTP (Hypertext Transfer Protocol) is the foundation of data communication on the web.

**Common `HTTP` Methods:**

- `GET`: Retrieve data
- `POST`: Submit data to be processed
- `PUT`: Update existing resources
- `DELETE`: Remove a resource
- `PATCH`: Partially update a resource
- `OPTIONS`: Describes communication options for a resource
- `HEAD`: Same as `GET` but returns only headers, no body

---
# Node Installation 

> [!Overview]
> `npm init` is a command that initializes a new *Node.js* project by creating a `package.json` file. This file is essential for *Node.js* projects as it contains metadata about your project and manages dependencies. Then we can change `pakage.json` script and add `run` : `Node index.js` this will run index.js on executing node run dev

```js
{
  "name": "my-project",
  "version": "1.0.0",
  "description": "A sample *Node.js* project",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Your Name",
  "license": "ISC"
}

```
