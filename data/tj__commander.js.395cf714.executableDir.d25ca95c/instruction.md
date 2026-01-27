# Bug Report

### Describe the bug

The `executableDir()` method is not working as expected. When I try to set a custom executable directory path, it doesn't get saved and subsequent calls to retrieve the path return `undefined` or the old value instead of the path I just set.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Try to set executable directory
program.executableDir('/custom/path');

// Try to retrieve it
console.log(program.executableDir()); // Expected: '/custom/path', Actual: undefined
```

Also, when calling `executableDir()` with a path argument, it seems to return the current value instead of the Command instance for chaining:

```js
const result = program.executableDir('/my/path');
console.log(result); // Returns the current _executableDir value instead of the program instance
```

### Expected behavior

1. When called with a path argument, it should store that path and return the Command instance for method chaining
2. When called without arguments, it should return the currently set executable directory path

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
