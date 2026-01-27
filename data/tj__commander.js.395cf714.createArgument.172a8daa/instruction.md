# Bug Report

### Describe the bug

The `createArgument` function is returning an unexpected object structure instead of the Argument instance directly. When trying to use the returned value as an Argument, it fails because the function now wraps it in an object with an `argument` property.

### Reproduction

```js
const { createArgument } = require('commander');

// Create an argument
const arg = createArgument('<file>', 'file to process');

// Try to use it - this will fail
program.addArgument(arg);
// Error: arg is not an Argument instance

// The returned value is now: { argument: Argument }
// instead of just: Argument
```

### Expected behavior

`createArgument` should return an Argument instance directly, just like `createCommand` returns a Command instance and `createOption` returns an Option instance. The API should be consistent across all factory functions.

### System Info
- commander version: latest
- Node version: 18.x

This seems to have broken after a recent update. The other factory functions (`createCommand`, `createOption`) work fine and return instances directly.

---
Repository: /testbed
