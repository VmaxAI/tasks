# Bug Report

### Describe the bug

When calling `parse()` multiple times on the same Command instance, the state management logic appears to be inverted. The first parse call seems to be restoring state instead of saving it, and subsequent calls are saving state instead of restoring it.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .option('-d, --debug', 'enable debug mode')
  .option('-v, --verbose', 'verbose output');

// First parse
program.parse(['node', 'test.js', '--debug']);
console.log('First parse - debug:', program.opts().debug); // Expected: true

// Second parse with different args
program.parse(['node', 'test.js', '--verbose']);
console.log('Second parse - debug:', program.opts().debug); // Expected: undefined
console.log('Second parse - verbose:', program.opts().verbose); // Expected: true
```

### Expected behavior

- First call to `parse()` should save the initial state
- Subsequent calls to `parse()` should restore to the saved state before parsing new arguments
- Options from previous parse calls should not persist unless explicitly set again

### Actual behavior

The state restoration/saving logic seems backwards, causing options to persist incorrectly across multiple parse calls or state to not be properly saved on the first call.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
