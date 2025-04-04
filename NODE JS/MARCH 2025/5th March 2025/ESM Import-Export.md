There are multiple ways to import and export in ecmascript modules : 

## Export

Modules with **functions** or **variables** can be stored in any external file.

There are two types of exports: **Named Exports** and **Default Exports**.

---

## Named Exports

Let us create a file named `person.js`, and fill it with the things we want to export.

You can create named exports two ways. In-line individually, or all at once at the bottom.

### In-line individually:

`person.js`
```js
export const name = "Jesse";
export const age = 40;
```

### All at once at the bottom:

`person.js`
```js
const name = "Jesse";
const age = 40;
export {name, age};
// export { myFunction as function1, myVariable as variable }; // we can also give alias names here
```
## Default Exports

Let us create another file, named `message.js`, and use it for demonstrating default export.

You can only have one default export in a file.

`message.js`
```js
const message = () => {  
const name = "Jesse";  
const age = 40;  
return name + ' is ' + age + 'years old.';  
};  
  
export default message;
// export { message as default }; Same as above
```
`other.js`
```js
import otherName from './message.js' // we can have any name for default export
```

## Re-exporting / Aggregating / Barrel Files
A module can also "relay" values exported from other modules without the hassle of writing two separate import/export statements. This is often useful when creating a single module concentrating various exports from various modules (usually called a "barrel module").
```js
export { default as function1, function2 } from "bar.js";

// same as

import { default as function1, function2 } from "bar.js";
export { function1, function2 };
```

We can combine multiple files so that when importing we don't have import every files one by one
```js
export { TabList } from './tab-list'
export { TabPanel } from './tab-panel'
```

## Cheat Sheet For Export

```js
// Exporting declarations
export let name1, name2/*, … */; // also var
export const name1 = 1, name2 = 2/*, … */; // also var, let
export function functionName() { /* … */ }
export class ClassName { /* … */ }
export function* generatorFunctionName() { /* … */ }
export const { name1, name2: bar } = o;
export const [ name1, name2 ] = array;

// Export list
export { name1, /* …, */ nameN };
export { variable1 as name1, variable2 as name2, /* …, */ nameN };
export { variable1 as "string name" };
export { name1 as default /*, … */ };

// Default exports
export default expression;
export default function functionName() { /* … */ }
export default class ClassName { /* … */ }
export default function* generatorFunctionName() { /* … */ }
export default function () { /* … */ }
export default class { /* … */ }
export default function* () { /* … */ }

// Aggregating modules
export * from "module-name";
export * as name1 from "module-name";
export { name1, /* …, */ nameN } from "module-name";
export { import1 as name1, import2 as name2, /* …, */ nameN } from "module-name";
export { default, /* …, */ } from "module-name";
export { default as name1 } from "module-name";

```

## Cheat Sheet For Import

```js
import defaultExport from "module-name";
import * as name from "module-name";
import { export1 } from "module-name";
import { export1 as alias1 } from "module-name";
import { default as alias } from "module-name";
import { export1, export2 } from "module-name";
import { export1, export2 as alias2, /* … */ } from "module-name";
import { "string name" as alias } from "module-name";
import defaultExport, { export1, /* … */ } from "module-name";
import defaultExport, * as name from "module-name";
import "module-name";
```
