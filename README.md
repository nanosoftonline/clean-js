# Clean Architecture JavaScript
Oftentimes, we find ourselves facing challenges when writing client-side JavaScript. For instance, consider a scenario where we have an HTML form, and we want to add functionality to it unobtrusively. In such cases, we typically create an accompanying JavaScript file with event hooks. However, this approach can quickly spiral out of control, making it difficult to maintain, hard to read, and sometimes challenging to locate specific functionality.

Before JavaScript modules (ES6 modules) were widely supported in web browsers, developers used various techniques to organize and load JavaScript code on the client side. One common approach was to use scripts and the global scope to include and execute JavaScript files:

1. **IIFE (Immediately Invoked Function Expression):** Developers often wrapped their code in immediately invoked function expressions to create a private scope for their variables and functions, preventing global namespace pollution.

1. **Namespace Objects:** Developers used plain JavaScript objects to create namespaces, where they could encapsulate related functions and variables. This helped prevent naming conflicts.

1. **AMD (Asynchronous Module Definition):** AMD is a specification for defining and loading modules asynchronously. Libraries like RequireJS implement this approach, allowing developers to declare dependencies and load modules on-demand.

1. **Script Tags:** Developers often used script tags in HTML to include external JavaScript files. Order of script inclusion was important, as scripts were loaded and executed sequentially.

1. **Global Variables:** Unfortunately, many older JavaScript applications simply used global variables to share data and functionality between different parts of the code, which could lead to naming conflicts and maintainability issues.

In addition to the principle that application logic should ideally be kept on the server side with the client side primarily handling UI logic, when client-side code becomes unmanageable, it can indeed pose a significant problem.

## Modules
A module is a self-contained unit of code that encapsulates a specific functionality or set of related functions, variables, or data. Modules are designed to promote code organization, reusability, and maintainability by breaking a program into smaller, manageable pieces. These pieces can be developed, tested, and maintained independently, making it easier to collaborate on larger software projects.

With JavaScript modules we can fix almost all of the problems above where modules aid us in splitting the code into separate files where each file is a module with its own scope. We do this by exporting and importing functions

### Exporting 
You can use the export keyword to expose functions, variables, or classes from a module:
```js
// math.js
export function add(a, b) {
  return a + b;
}
```
You can also have a default export in a module, which can be imported without curly braces:

```js
// math.js
export default function add(a, b) {
  return a + b;
}
```
### Importing 
To use the exported functionality in another module, you can use the import statement:
```js
// app.js
import { add } from './math.js';

console.log(add(2, 3)); // This imports the 'add' function from the 'math' module.

```

