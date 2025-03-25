A Template Engine simplifies the use of static templates with minimal code. During runtime on the client side, variables in the template are replaced with actual values. These engines help developers create templates for web pages, written in a markup language with placeholders for dynamic content. When rendered, these placeholders are substituted with real data, producing a dynamic document.

# EJS

- What is the "E" for? "Embedded?" Could be. How about "Effective," "Elegant," or just "Easy"? EJS is a simple templating language that lets you generate HTML markup with plain JavaScript. No religiousness about how to organize things. No reinvention of iteration and control-flow. It's just plain JavaScript.

## Benefits

- ### Use plain JavaScript
	- We love JavaScript. It's a totally friendly language. All templating languages grow to be Turing-complete. Just cut out the middle-man, and use JS!
- ### Simple syntax
	- JavaScript code in simple, straightforward scriptlet tags. Just write JavaScript that emits the HTML you want, and get the job done!
- ### Speedy execution
	- We all know how fast V8 and the other JavaScript runtimes have gotten. EJS caches the intermediate JS functions for fast execution.

## CLI Command

```bash
ejs demo.ejs -f data.json -o index.html
```
***Feed template file  a data file and specify an output file.***

```html
// demo.ejs File
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title></title>
	</head>
	<body>
		<% if (user) { %>
		<h2><%= user.name %></h2>
		<% } %> <% users.forEach(element => { %> <%= element.name %> <% }); %>
	</body>
</html>

```

```json
// data.json

{
	"user": { "name": "someone" },
	"users": [{ "name": "Rishi" }, { "name": "Meet" }]
}
```

```html
// index.html

<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title></title>
	</head>
	<body>
		<h2>someone</h2>

		Rishi Meet
	</body>
</html>

```


---


## Within js file

```js
const ejs = require("ejs");


// Approach 1

let template = `
  <h2>Hello <%= name %>!</h2>
  <p>Today is <%= date %></p>
  <p>1 + 2 is <%= 1 + 2 %></p>
`;
const output = ejs.render(template, {
	name: "John",
	date: new Date().toISOString().split("T")[0],
});

console.log(output);

// Approach 2

const renderTemplate = ejs.compile(`
  <h2>Hello <%= name %>!</h2>
  <p>Today is <%= date %></p>
  <p>1 + 2 is <%= 1 + 2 %></p>
`);

console.log(
	renderTemplate({
		name: "John",
		date: new Date().toISOString().split("T")[0],
	})
);



// output
//	<h2>Hello John!</h2>
//	<p>Today is 2025-03-25</p>
//	<p>1 + 2 is 3</p>
```