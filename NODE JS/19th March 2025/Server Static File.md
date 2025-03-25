# What does 'serve static file' mean ?

- Static files are files that don’t change when your application is running.
- These include `HTML, CSS, JavaScript files, images, videos, fonts, and documents`. They’re called `static` because they do not require any server-side processing or dynamic content generation. Once created, they remain constant until manually altered by a developer.

# Demo of serving static files with `http` module

```js
const http = require("http");
const path = require("path");
const url = require("url");
const fs = require("fs");
  
const MIME_TYPES = {
    ".txt": "text/plain",
    ".html": "text/html",
    ".css": "text/css",
    ".js": "text/javascript",
  
    ".jpeg": "image/jpeg",
    ".jpg": "image/jpeg",
    ".png": "image/png",
    ".gif": "image/gif",
    ".svg": "image/svg+xml",
  
    ".json": "application/json",
    ".xml": "application/xml",
    ".pdf": "application/pdf",
    ".zip": "application/zip",
    ".doc": "application/msword",
    ".xls": "application/vnd.ms-excel",
  
    ".mpeg": "video/mpeg",
    ".mp4": "video/mp4",
};
  
http.createServer((req, res) => {
    const query = url.parse(req.url).query
    if(query.split("=")[0] !== "file"){
        res.writeHead(400, { "content-type": "text/html" });
        res.end("Invalid Url");
        return
    }
    const file = query.split("=")[1];
    const filePath = path.join(__dirname,"Test Files", file);
    const ext = path.extname(filePath);
    fs.readFile(filePath, (err, data) => {
        if (err || !fs.statSync(filePath).isFile()) {
            res.writeHead(404, { "content-type": "text/html" });
            res.end("File Not Found");
            return;
        }
        res.writeHead(200, { "content-type": MIME_TYPES[ext] });
        res.end(data);
    });
}).listen(3000, () => {
    console.log("Server Listening on http://localhost:3000");
});
```




