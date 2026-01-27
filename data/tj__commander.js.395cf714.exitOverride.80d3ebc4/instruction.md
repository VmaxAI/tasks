# Bug Report

### Describe the bug

When calling `exitOverride()` without arguments, the exit callback is not being set up correctly. The default behavior that should throw errors (except for async sub-command execution) is not working as expected.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Call exitOverride without a callback function
program.exitOverride();

// Try to trigger an error that should be thrown
program.parse(['node', 'test', '--unknown-option']);
```

### Expected behavior

When `exitOverride()` is called without arguments, it should set up a default callback that:
1. Throws errors for most cases
2. Silently ignores errors with code `commander.executeSubCommandAsync`

Instead, the current behavior seems inverted - errors that should be thrown are being ignored, and the callback assignment logic appears backwards.

### System Info
- Node version: 18.x
- Commander.js version: latest

---
Repository: /testbed
