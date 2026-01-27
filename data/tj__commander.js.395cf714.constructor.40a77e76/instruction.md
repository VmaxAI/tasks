# Bug Report

### Describe the bug

I'm experiencing an issue where `CommanderError` objects have their `code` and `exitCode` properties swapped. When I create a new error with specific exit code and error code values, they end up assigned to the wrong properties.

### Reproduction

```js
const { CommanderError } = require('commander');

const error = new CommanderError(1, 'commander.invalidArgument', 'Invalid argument provided');

console.log('Exit code:', error.exitCode);  // Expected: 1, Actual: 'commander.invalidArgument'
console.log('Error code:', error.code);      // Expected: 'commander.invalidArgument', Actual: 1
```

### Expected behavior

The `exitCode` property should contain the numeric exit code (first parameter), and the `code` property should contain the string error identifier (second parameter). Currently they appear to be reversed.

### System Info
- Commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
