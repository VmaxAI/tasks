# Bug Report

### Describe the bug

When using conflicting options with positive flags (like `--foo`), the error message incorrectly references the negative option flag (like `--no-foo`) instead of the positive one that was actually used.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('--foo', 'enable foo')
  .option('--no-foo', 'disable foo')
  .option('--bar', 'enable bar')
  .conflicts('foo', 'bar');

program.parse(['node', 'test', '--foo', '--bar']);
```

When running this with conflicting options `--foo` and `--bar`, the error message shows the wrong flag name in the error output. It displays the negative variant instead of the positive option that was actually provided on the command line.

### Expected behavior

The error message should reference `--foo` (the option that was actually used) rather than `--no-foo` in the conflict error message.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
