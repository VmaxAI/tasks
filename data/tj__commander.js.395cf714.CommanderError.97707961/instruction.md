# Bug Report

### Describe the bug

I'm experiencing an issue with error handling in Commander. When a `CommanderError` is thrown, the error name and exit code properties are not being set correctly.

### Reproduction

```js
const { CommanderError } = require('commander');

// Create a CommanderError with specific code and exitCode
const error = new CommanderError(1, 'commander.invalidArgument', 'Invalid argument provided');

console.log('Error name:', error.name);  // Expected: 'CommanderError', Got: 'Error'
console.log('Exit code:', error.exitCode);  // Expected: exitCode parameter, Got: code parameter value
```

### Expected behavior

1. The `error.name` property should be set to `'CommanderError'` (or the constructor name)
2. The `error.exitCode` property should be set to the `exitCode` parameter passed to the constructor, not the `code` parameter

### Current behavior

- `error.name` is always `'Error'` instead of reflecting the actual error class name
- `error.exitCode` is being set to the `code` parameter value instead of the `exitCode` parameter

This makes it difficult to properly identify and handle different types of Commander errors in error handling code.

### System Info
- Commander version: latest
- Node version: 18.x

---
Repository: /testbed
