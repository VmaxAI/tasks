# Bug Report

### Describe the bug
When defining optional arguments with bracket notation like `[arg]`, the argument name is being truncated incorrectly. The last character of the argument name is getting cut off.

### Reproduction
```js
const arg = new Argument('[optional]', 'An optional argument');
console.log(arg.name()); // Expected: 'optional', Actual: 'optiona'

const arg2 = new Argument('[file]', 'File path');
console.log(arg2.name()); // Expected: 'file', Actual: 'fil'
```

Also seeing similar issues with variadic arguments - they're not being parsed correctly either:

```js
const varArg = new Argument('<files...>', 'Multiple files');
console.log(varArg.name()); // The name is wrong here too
```

### Expected behavior
The argument name should be extracted correctly from the bracket notation, preserving all characters of the actual name.

### System Info
- Node version: 18.x
- commander.js version: latest

---
Repository: /testbed
