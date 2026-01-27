# Bug Report

### Describe the bug

When calling `.description()` with only the first argument (description string), the method returns the current description instead of setting it. This breaks the expected behavior where passing a description string should update the command's description.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// This doesn't set the description as expected
program.description('My program description');

console.log(program.description()); // Expected: 'My program description', Actual: undefined
```

The issue also occurs when chaining:

```js
program
  .name('myapp')
  .description('My program description')
  .version('1.0.0');

// Description is not set
console.log(program.description()); // undefined
```

### Expected behavior

When calling `.description(str)` with a string argument, it should set the description and return the Command instance for chaining. Only when called with no arguments should it return the current description value.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
