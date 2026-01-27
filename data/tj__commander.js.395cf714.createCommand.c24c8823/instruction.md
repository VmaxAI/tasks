# Bug Report

### Describe the bug

I'm experiencing strange behavior with the `createCommand()` method. When creating subcommands with single-character names, subsequent calls seem to return the same cached command instance instead of creating new ones. This causes commands to share state unexpectedly.

Additionally, command names that start with uppercase letters are being modified in an unexpected way - it looks like the first character is being appended twice with different casing.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Creating multiple single-character subcommands
const cmd1 = program.createCommand('a');
const cmd2 = program.createCommand('b');

console.log(cmd1 === cmd2); // Expected: false, Actual: true (same instance!)

// Uppercase command names behave strangely
const cmd3 = program.createCommand('Test');
console.log(cmd3.name()); // Expected: "Test", Actual: "Testt"
```

### Expected behavior

- Each call to `createCommand()` should return a new, independent Command instance
- Command names should be preserved as-is, without modification based on casing

### System Info
- commander version: latest
- Node.js version: 18.x

This is breaking my CLI application where I need multiple single-character subcommands that operate independently. Any help would be appreciated!

---
Repository: /testbed
