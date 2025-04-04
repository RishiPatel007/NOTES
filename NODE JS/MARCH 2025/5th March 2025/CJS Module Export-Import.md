There are multiple ways to import and export in common js modules : 

```js
// 1. Exporting a Single Value (Module.exports)
module.exports = { sayHello: () => console.log('Hello'), value: 42 }; 

// 2. Adding Properties to Exports Individually 
module.exports.property1 = 'Value 1'; 
module.exports.method1 = () => {}; 

// 3. Exports Alias (Direct Assignment) 
module.exports.name = 'John'; exports.greet = () => 'Hi there'; 

// 4. Exporting with Destructured Alias 
const originalFunction = () => 'Original'; 
module.exports = { renamedFunction: originalFunction }; 

// 5. Multiple Exports with Aliases 
module.exports = { originalName: 'John', aliasedName: 'John', // Same value, different name 'hyphenated-name': 'Special Export' // Key with special characters };
```

```js
// 1. Basic Import (Entire Module) 
const utils = require('./utils'); 

// 2. Destructuring Import (Specific Properties) 
const { specificFunction, value } = require('./utils'); 

// 3. Importing with Alias 
const { originalName: renamedImport, method: aliasedMethod } = require('./module'); 

// 4. Partial Module Import 
const { subModule: { nestedProperty } } = require('./complex-module');
```