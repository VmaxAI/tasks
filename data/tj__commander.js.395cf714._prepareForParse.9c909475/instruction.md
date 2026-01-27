# Bug Report

### Describe the bug

When calling `parse()` multiple times on the same command instance, the state management logic appears to be inverted. The first call works correctly, but subsequent calls to `parse()` don't properly restore the command state, causing unexpected behavior.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .option('-d, --debug', 'enable debug mode')
  .option('-v, --verbose', 'verbose output');

// First parse works fine
program.parse(['node', 'test.js', '--debug']);
console.log('First parse:', program.opts()); // { debug: true }

// Second parse doesn't work as expected
program.parse(['node', 'test.js', '--verbose']);
console.log('Second parse:', program.opts()); // Expected: { verbose: true }, but state is corrupted
```

### Expected behavior

Each call to `parse()` should properly reset the command state and parse the new arguments independently. The second call should give `{ verbose: true }` with the debug option cleared.

### System Info
- commander.js version: latest
- Node.js version: 18.x

This seems like a regression in the state management logic. The command instance should be reusable across multiple parse calls.

---
Repository: /testbed
