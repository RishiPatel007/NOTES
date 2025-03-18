# Complete API Guide

## What is an API? 

**API** stands for **Application Programming Interface**.

In the context of APIs:

- The word **Application** refers to any software with a distinct function
- **Interface** can be thought of as a contract of service between two applications

This contract defines how applications communicate with each other using requests and responses. API documentation contains information on how developers should structure those requests and responses.


## Why Use an API Instead of Directly Adding Functionality to Every Client?

1. **Avoids Redundancy & Saves Resources**
    
    - Without an API, **each client (mobile app, web app, desktop app)** would need to implement the same logic separately.
    - This increases **development time, complexity, and resource consumption** on every client device.
    - With an API, the heavy processing happens **on the server**, keeping clients lightweight.
2. **Easier Maintenance & Updates**
    
    - If you **change business logic**, you’d have to update **every client** separately (which is slow and error-prone).
    - With an API, you update **only the backend**, and all clients automatically get the new behavior.
3. **Security & Data Control**
    
    - Without an API, clients might directly access **databases or sensitive logic**, creating security risks.
    - An API acts as a **controlled gateway**, enforcing authentication, authorization, and data validation.
4. **Scalability**
    
    - APIs allow multiple clients (mobile, web, IoT) to **reuse** the same backend services without duplication.
    - If traffic grows, you can **scale the API** without needing to modify every client.
5. **Cross-Platform Compatibility**
    
    - APIs enable **different clients (iOS, Android, Web, Desktop)** to access the same features, ensuring consistency.
    - Without an API, you’d need **separate implementations** for each platform.
---
## How APIs Work

API architecture is usually explained in terms of client and server:

- The application sending the request is called the **client**
- The application sending the response is called the **server**

There are four different API architectures, each with distinct characteristics:

### SOAP APIs

- Use Simple Object Access Protocol
- Client and server exchange messages using XML
- Less flexible but offers formal contract definition
- More popular in enterprise environments

### RPC APIs

- Remote Procedure Calls
- Client completes a function (or procedure) on the server
- Server sends the output back to the client
- Examples include gRPC (Google's high-performance RPC framework)

### WebSocket APIs

- Uses JSON objects to pass data
- Supports two-way communication between client apps and the server
- Server can send callback messages to connected clients
- More efficient than REST for real-time applications
- Maintains a persistent connection

### REST APIs

- Representational State Transfer
- HTTP-based API that follows a request-response pattern
- Each request is independent (stateless)
- Server does not maintain any session state
- Most widely used API architecture for web services
---
## What is an API endpoint and why is it important?

API endpoints are the final touchpoints in the API communication system. These include server URLs, services, and other specific digital locations from where information is sent and received between systems.

### How to secure a REST API?

All APIs must be secured through proper authentication and monitoring. The two main ways to secure REST APIs include:
#### 1. Authentication tokens 
These are used to authorize users to make the API call.
#### 2. API keys
API keys verify the program or application making the API call.

---
## Request and Response

### Request Components

1. **HTTP Method** (GET, POST, PUT, DELETE, etc.)
2. **URL/Endpoint** (e.g., `https://api.example.com/users`)
3. **Headers** (metadata about the request)
4. **Body** (data sent with the request, typically for POST/PUT)
5. **Query Parameters** (additional data sent in the URL, e.g., `?sort=desc`)

### Response Components

1. **Status Code** (200, 404, 500, etc.)
2. **Headers** (metadata about the response)
3. **Body** (returned data, typically in JSON or XML format)
4. **Content-Type** (defines the format of the response)

### Example Request and Response

**Request:**

```js
GET /api/users/123 HTTP/1.1
Host: example.com
Authorization: Bearer token123
Accept: application/json
```

**Response:**

```js
HTTP/1.1 200 OK
Content-Type: application/json
Cache-Control: max-age=3600

{
  "id": 123,
  "name": "John Doe",
  "email": "john@example.com"
}
```

## API Route Design

Good API design follows these principles:
### REST vs. RPC Approach

| CRUD Operation | REST (Resource-Based) | RPC (Action-Based)    |
| -------------- | --------------------- | --------------------- |
| **Create**     | `POST /users`         | `CreateUser(request)` |
| **Read**       | `GET /users/{id}`     | `GetUser(request)`    |
| **Update**     | `PUT /users/{id}`     | `UpdateUser(request)` |
| **Delete**     | `DELETE /users/{id}`  | `DeleteUser(request)` |
|                |                       |                       |

In **RPC**, each action is explicitly defined as a method in the API.  
In **REST**, actions are inferred from the HTTP method applied to a resource.

### REST API Design Best Practices

1. **Use nouns, not verbs for resources**
    - Good: `/articles`
    - Avoid: `/getArticles`
2. **Use plural nouns for collections**
    - Good: `/users`, `/posts`
    - Avoid: `/user`, `/post`
3. **Use HTTP methods appropriately**
    - `GET`: Retrieve resources
    - `POST`: Create new resources
    - `PUT`: Update resources (full update)
    - `PATCH`: Update resources (partial update)
    - `DELETE`: Remove resources
4. **Nest resources for showing relationships**
    - `/users/{id}/posts` (get all posts from a specific user)
5. **Use query parameters for filtering, sorting, and pagination**
    - `/users?status=active&sort=name&page=2`
6. **Version your API**
    - `/v1/users`
    - `/v2/users`

### Why REST is Often Better for CRUD Operations

1. **Standardized Conventions (HTTP Methods)**
    - REST follows widely accepted standards (`GET`, `POST`, `PUT`, `DELETE`)
    - HTTP methods naturally map to CRUD operations, making APIs more predictable
2. **Better Caching**
    - REST uses HTTP caching (`GET` requests can be cached)
    - RPC methods don't directly support caching unless explicitly implemented
3. **Statelessness**
    - REST enforces stateless communication, which makes it easier to scale
    - RPC can be stateful depending on implementation, which might introduce complexity
4. **Interoperability**
    - REST works well with browsers and is universally supported
    - RPC (especially gRPC) requires specific client libraries and is not natively supported by browsers
5. **Easier to Consume**
    - REST APIs are simpler to use with web clients (fetch, Axios, etc.)
    - gRPC requires special client code for communication

**When to choose:**

- ✅ **Use REST** if you need **standardized, scalable, and cacheable** CRUD APIs (e.g., public web APIs)
- ✅ **Use RPC** if you need **efficient, low-latency, or streaming-based** communication (e.g., microservices)


## Response Status Codes

HTTP status codes indicate whether a specific HTTP request has been successfully completed:

### 1xx: Informational

- `100 Continue` - Server has received the request headers and client should proceed to send the request body

### 2xx: Success

- `200 OK` - Request succeeded
- `201 Created` - Request succeeded and a new resource was created
- `204 No Content` - Request succeeded but returns no content

### 3xx: Redirection

- `301 Moved Permanently` - Resource has been permanently moved to a new URL
- `302 Found` - Resource temporarily moved to a different URL
- `304 Not Modified` - Resource hasn't been modified since last request

### 4xx: Client Error

- `400 Bad Request` - Server cannot process the request due to client error
- `401 Unauthorized` - Authentication is required but was not provided
- `403 Forbidden` - Server understood the request but refuses to authorize it
- `404 Not Found` - Resource could not be found
- `422 Unprocessable Entity` - Request was well-formed but contains semantic errors

### 5xx: Server Error

- `500 Internal Server Error` - Server encountered an unexpected condition
- `502 Bad Gateway` - Server acting as gateway received invalid response from upstream server
- `503 Service Unavailable` - Server is not ready to handle the request
- `504 Gateway Timeout` - Server acting as gateway did not receive a timely response

## Headers

Headers provide additional information about the request or response.

### Common Request Headers

- `Authorization`: Authentication credentials for HTTP authentication
- `Content-Type`: Media type of the resource in the request body
- `Accept`: Media types acceptable for the response
- `User-Agent`: Information about the client's software
- `Origin`: Origin of the cross-site access request or preflight request

### Common Response Headers

- `Content-Type`: Media type of the resource in the response body
- `Cache-Control`: Directives for caching mechanisms
- `Set-Cookie`: Send a cookie from the server to the client
- `Access-Control-Allow-Origin`: Indicates whether a resource can be shared
- `Content-Length`: Size of the response body in bytes

### Custom Headers

- Often prefixed with `X-` (though this convention is deprecated)
- Example: `X-API-Key`, `X-Request-ID`

## Testing in Postman

Postman is a popular API client that makes it easy to create, share, test, and document APIs.

### Setting Up Requests in Postman

1. Create a new request
2. Select the HTTP method (GET, POST, PUT, DELETE, etc.)
3. Enter the request URL
4. Add headers in the Headers tab
5. For POST/PUT requests, add data in the Body tab
6. Click "Send" to execute the request

### Working with Headers in Postman

- Add headers in the "Headers" tab
- Common headers include:
    - `Content-Type: application/json`
    - `Authorization: Bearer your_token_here`
    - `Accept: application/json`

### Authentication in Postman

- Basic Auth: Username and password
- Bearer Token: JWT or OAuth token
- API Key: Either in headers or query parameters
- OAuth 2.0: Full OAuth flow support

### Testing with Postman

- Write tests in JavaScript using the Postman scripting API
- Verify status codes, response bodies, headers, and timing
- Use Postman's environment variables to store and reuse values
- Create collections to group related requests
- Run collections as part of automated testing workflows
	
## Creating a Server

### Node.js Server with Http

```js
const http = require('http');

const server = http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello, this is a Node.js HTTP server!');
});

const PORT = 3000;
server.listen(PORT, () => {
    console.log(`Server is running at http://localhost:${PORT}`);
});

```

### Node.js Server with Express


``` js
const express = require('express');
const app = express();
const PORT = process.env.PORT || 3000;

// Middleware to parse JSON bodies
app.use(express.json());

// Sample data
let users = [
  { id: 1, name: 'Alice', email: 'alice@example.com' },
  { id: 2, name: 'Bob', email: 'bob@example.com' }
];

// GET all users
app.get('/api/users', (req, res) => {
  res.status(200).json(users);
});

// GET a specific user
app.get('/api/users/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  
  if (!user) {
    return res.status(404).json({ message: 'User not found' });
  }
  
  res.status(200).json(user);
});

// POST a new user
app.post('/api/users', (req, res) => {
  const { name, email } = req.body;
  
  if (!name || !email) {
    return res.status(400).json({ message: 'Name and email are required' });
  }
  
  const newUser = {
    id: users.length + 1,
    name,
    email
  };
  
  users.push(newUser);
  res.status(201).json(newUser);
});

// PUT (update) a user
app.put('/api/users/:id', (req, res) => {
  const user = users.find(u => u.id === parseInt(req.params.id));
  
  if (!user) {
    return res.status(404).json({ message: 'User not found' });
  }
  
  const { name, email } = req.body;
  
  if (!name || !email) {
    return res.status(400).json({ message: 'Name and email are required' });
  }
  
  user.name = name;
  user.email = email;
  
  res.status(200).json(user);
});

// DELETE a user
app.delete('/api/users/:id', (req, res) => {
  const userIndex = users.findIndex(u => u.id === parseInt(req.params.id));
  
  if (userIndex === -1) {
    return res.status(404).json({ message: 'User not found' });
  }
  
  const deletedUser = users.splice(userIndex, 1);
  res.status(200).json(deletedUser[0]);
});

// Start the server
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

### API Architecture Diagram

Copy

`┌─────────────┐       ┌─────────────┐       ┌─────────────┐ │             │       │             │       │             │ │   Client   ├───────►    API      ├───────►  Database   │ │             │       │             │       │             │ └─────────────┘       └─────────────┘       └─────────────┘      Request             Process             Data Storage                         Response`

This basic diagram illustrates the typical flow:

1. Client sends a request to the API
2. API processes the request and interacts with the database if needed
3. API sends a response back to the client