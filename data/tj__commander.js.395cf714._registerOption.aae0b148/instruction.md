# Bug Report

### Describe the bug

When adding options with long flags to a command, duplicate detection is not working properly. I can add two options with the same long flag without getting an error, even though they should conflict.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-a, --alpha', 'first option')
  .option('-b, --alpha', 'second option with same long flag');

// Expected: Should throw an error about conflicting flag '--alpha'
// Actual: No error is thrown, both options are registered
```

### Expected behavior

The library should detect the duplicate `--alpha` flag and throw an error indicating that the flag is already in use by another option. This used to work correctly before.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
