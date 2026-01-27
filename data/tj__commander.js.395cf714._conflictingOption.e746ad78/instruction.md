# Bug Report

### Describe the bug

When using conflicting options with negated boolean flags, the error message reports the wrong option name. Instead of showing which option was actually used (positive or negative variant), it shows the opposite one.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('--cheese', 'add cheese')
  .option('--no-cheese', 'remove cheese')
  .option('--peppers', 'add peppers')
  .conflicts('cheese', 'peppers');

// Use the negative variant
program.parse(['node', 'test', '--no-cheese', '--peppers']);
```

When running this with `--no-cheese` and `--peppers`, the error message incorrectly refers to `--cheese` instead of `--no-cheese`.

### Expected behavior

The error message should accurately report which option variant was actually used. If I use `--no-cheese`, the error should mention `--no-cheese`, not `--cheese`.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
