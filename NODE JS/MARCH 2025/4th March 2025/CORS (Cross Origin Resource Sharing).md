- **Definition**: CORS is a security feature implemented by web browsers that allows or restricts web applications running at one origin (domain, protocol, or port) to request resources from a different origin.

- **Purpose**: It relaxes the Same-Origin Policy (SOP), which prevents scripts from one origin from accessing resources on another origin, enabling controlled cross-origin requests.

- **How It Works**:
    - The browser sends an HTTP request with an Origin header (e.g., Origin: https://example.com).
    - The server responds with an Access-Control-Allow-Origin header, specifying which origins are permitted (e.g., Access-Control-Allow-Origin: https://example.com or * for all).
    - If the origin isn’t allowed, the browser blocks the response.
    
- **Types of Requests**:
    - **Simple Requests**: GET, POST, or HEAD requests with certain headers (e.g., Content-Type: application/x-www-form-urlencoded). These don’t require a preflight.
    - **Preflight Requests**: For complex requests (e.g., PUT, DELETE, or custom headers), the browser sends an OPTIONS request first to check permissions.
    
- **Key Headers**:
	- Access-Control-Allow-Origin : Specifies which domains with port are allowed . 
    - Access-Control-Allow-Methods: Specifies allowed HTTP methods (e.g., GET, POST).
    - Access-Control-Allow-Headers: Lists allowed headers.
    - Access-Control-Max-Age: Duration (in seconds) the preflight response can be cached.
    
- **Common Use Case**: Enables APIs hosted on one domain (e.g., api.example.com) to be accessed by a frontend on another (e.g., www.example.com).