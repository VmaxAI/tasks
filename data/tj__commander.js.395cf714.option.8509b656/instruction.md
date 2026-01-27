# Bug Report

### Describe the bug

When calling `.option()` with an empty string or whitespace-only string as the flags parameter, the command silently ignores the option instead of throwing an error or processing it. This causes the option registration to fail without any indication to the developer.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// This silently does nothing - no error, no option registered
program.option('', 'Some description', 'default value');

// Same issue with whitespace
program.option('   ', 'Another description');

// Expected: either an error or the option to be registered
// Actual: returns the command object but option is not added
```

### Expected behavior

The library should either:
1. Throw an error indicating that flags cannot be empty/whitespace
2. Process the option normally (if empty flags are valid)

Currently it just returns early without any feedback, making it difficult to debug when accidentally passing empty strings.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
