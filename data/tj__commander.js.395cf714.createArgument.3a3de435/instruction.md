# Bug Report

### Describe the bug

I'm experiencing an issue where `createArgument()` is returning `null` instead of creating an `Argument` object when both `name` and `description` parameters are provided. This is causing my command-line application to fail when trying to define arguments with descriptions.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// This returns null instead of an Argument object
const arg = program.createArgument('username', 'The username for login');
console.log(arg); // prints: null

// Expected: Should return an Argument instance
```

### Expected behavior

When calling `createArgument()` with both a name and description, it should return a new `Argument` object, not `null`. The method should work properly regardless of whether one or both parameters are provided.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
