# Bug Report

### Describe the bug

The `createOption()` function is not working as expected. When I try to use it to create command-line options, I'm getting a function returned instead of an Option object. This breaks my CLI application as I can't chain methods or use the option directly.

### Reproduction

```js
const { createOption } = require('commander');

// This used to return an Option object
const myOption = createOption('-p, --port <number>', 'port number');

// Now myOption is a function instead of an Option
console.log(typeof myOption); // prints "function" instead of "object"

// This causes errors when trying to use it
program.addOption(myOption); // Error: expecting an Option object
```

### Expected behavior

`createOption()` should return an Option instance directly, not a function. The returned object should have all the Option methods available (like `.default()`, `.choices()`, etc.) and be usable with `program.addOption()`.

### System Info
- commander version: latest
- Node.js version: v18.x

---
Repository: /testbed
