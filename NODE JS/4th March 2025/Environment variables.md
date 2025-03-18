## Introduction

Environment variables are a key-value pair data set that are available at the operating system level.

- In our root folder we can create a new file and name it `.env`.
- By opening our .env file in a text editor and creating some key-value pairs. These are our environment variable.

``` js
DATABASE_URL=sample-database-url
PORT=3000
SECRET_KEY=mysecretkey
```

- We can access our env variables by using library like `dotenv`

```js
require('dotenv').config()
const port = process.env.PORT || 4000;  // Read from .env if not available then defaults to 4000
```

![[{env}.png]]

