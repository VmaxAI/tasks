# Bug Report

### Describe the bug

I'm experiencing an issue where adding options with conflicting long flags doesn't throw an error as expected. The conflict detection seems to be broken and allows duplicate long option flags to be registered without any warning.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-s, --source <file>', 'source file')
  .option('-d, --source <file>', 'another option with same long flag');

// Expected: Should throw an error about conflicting '--source' flag
// Actual: No error is thrown, both options are registered
```

### Expected behavior

When trying to register two options that share the same long flag (e.g., `--source`), the library should detect the conflict and throw an error indicating that the flag is already in use by another option.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
