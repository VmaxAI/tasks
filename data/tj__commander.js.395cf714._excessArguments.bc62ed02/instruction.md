# Bug Report

### Describe the bug

The error message for excess arguments has incorrect grammar when showing the expected number of arguments. The pluralization of "argument" is based on the wrong count - it's checking the received arguments count instead of the expected arguments count.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .argument('<file>')
  .action(() => {});

// Try parsing with multiple arguments when only one is expected
program.parse(['node', 'test', 'file1', 'file2']);
```

### Expected behavior

When 2 arguments are provided but only 1 is expected, the error message should say:
```
error: too many arguments. Expected 1 argument but got 2.
```

### Actual behavior

The error message incorrectly pluralizes based on the number of received arguments instead of expected arguments. So when expecting multiple arguments but receiving a different number, the grammar doesn't match the expected count.

For example, if a command expects 3 arguments but receives 1, it would say "Expected 3 arguments" (correct), but in other cases the pluralization might be wrong.

---
Repository: /testbed
