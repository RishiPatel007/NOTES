# Modules

JavaScript modules allow you to break up your code into separate files .This makes it easier to maintain a code-base.
Modules are imported from external files with the `import` statement.

## Why is a Module System Required?

Early development of JavaScript encountered several difficulties that made an organized approach to coding necessary

1. **Global Scope Issues:** When all variables and functions were first defined in the global scope, managing big codebases became challenging due to conflicts. When multiple scripts attempted to use the same variable names, this frequently led to issues.
2. **Maintainability:** Without a modular architecture, code maintenance became more and more challenging as applications expanded in size and complexity. Developers can divide larger, more complex applications into smaller, more manageable chunks with a module system.
3. **Collaboration:** A module system fosters a collaborative environment by enabling several developers to work on separate modules separately and without hindrance.
4. **Performance Optimization:** By loading only the necessary modules when needed, asynchronous loading (ES Modules), which is supported by modern module systems, can enhance application performance.
5. **Standardization:** JavaScript programs can now be structured consistently across various contexts thanks to the introduction of standardized module systems like ES Modules.

## Common Js

The purpose of CommonJS was to create a JavaScript module system, specifically for Node.js server-side development. Since its introduction in 2009, it has gained widespread use, particularly within the Node.js ecosystem.

### Key Features

- **Synchronous Loading:** CommonJS modules are loaded synchronously, which means that before executing code, it waits for the module to load. Applications may exhibit blocking behavior as a result of this.
- **Export Mechanism:** Modules can easily share functions, objects, or variables across other files by exporting values using module.exports or exports.
- **Runtime Environment:** CommonJS is mainly used for backend applications and is fully supported in all Node.js versions.

## ECMAScript Modules (ESM)

In 2015, ESM a standardized module system for JavaScript was released alongside [ECMAScript](https://www.guvi.in/blog/features-of-ecmascript/) 6 (ES6). It seeks to offer a more contemporary method of code modularization that functions flawlessly in both server-side and client-side contexts.

### Key Features

- **Asynchronous Loading:**  Modules can be loaded asynchronously with ESM, which improves performance by letting other processes go on while modules are loaded.
- **Static Imports/Exports:** ESM makes use of the import and export syntax to allow for the parse-time static analysis of dependencies. This makes it easier to perform optimizations like tree shaking, which removes unnecessary code during bundling.
- **Native Browser Support:** ESM is the recommended option for front-end development since it is natively supported by most current web browsers.

## Comparison Table

|       Features        |              Loading               |         Export syntax         |
| :-------------------: | :--------------------------------: | :---------------------------: |
|       CommonJS        |            Synchronous             |        module.exports         |
|  ECMAScript Modules   |            Asynchronous            |    export / export default    |
|     Import syntax     |       require(‘module_name’)       | Import {…} from ‘module_name’ |
|    Browser support    |       Not natively supported       |      Natively supported       |
| Dependency Management |    Dynamic loading with require    | Static analysis at parse time |
|   Default Behavior    | Caches modules upon the first load |   Does not cache by default   |
|       Use Cases       |          Server-side apps          |     Frontend applications     |


