Express.js is a minimal and flexible web application framework that provides a list of features for building web and mobile applications easily. It simplifies the development of server-side applications by offering an easy-to-use API for routing, middleware, and HTTP utilities.


# Basic app in express 

```js
const express = require("express");

const app = express();
const PORT = 3000;

app.get("/", (req, res) => {
	res.send("Something");
});

app.listen(PORT, (err) => {
	if (err) {
		console.log(err);
		return;
	}
	console.log(`Express app listening on PORT : ${PORT}`);
});

```


---

# Middleware for parsing json data

- We use express.json() middleware to parse req.body into json format

```js
app.use(express.json());

app.post("/", (req, res) => {
	const { name } = req.body;
	res.send(`Hello ${name}`);
});
```


# Serving static file 

## There are two ways to serve static file

- ### By using express.static() middleware function
- ### By using res.sendFile() method

```js
app.use("/static", express.static(path.join(__dirname, "static", "index.html")));

app.get("/file", (req, res) => {
	res.sendFile(path.join(__dirname, "static", "index.html"));
});
```


# Middleware 

- We use app.use() to set middleware , for custom middleware we can pass a callback `or` path and callback
- In callback , we pass (req,res,next) (or (err,req,res,next) in error handler middleware )
- We can also chain middleware by calling next()
- If next is not called it will go directly to route handler

```js
app.use((req, res, next) => {
	console.log("middleware 1");
	next();
});
app.use((req, res, next) => {
	console.log("middleware 2");
	next();
});

app.get('/' , (req,res)=>{
	console.log("Get")
})
```

