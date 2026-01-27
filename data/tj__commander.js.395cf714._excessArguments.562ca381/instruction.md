# Bug Report

### Describe the bug

The error message for excess arguments is displaying incorrect grammar. When passing 2 arguments to a command that expects 1, the error message says "Expected 1 arguments" instead of "Expected 1 argument" (without the 's').

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<file>', 'file to process')
  .action(() => {});

// Pass 2 arguments when only 1 is expected
program.parse(['node', 'test', 'file1.txt', 'file2.txt']);
```

### Expected behavior

The error message should use proper singular/plural grammar:
- When expecting 1 argument: "Expected 1 argument but got 2."
- When expecting 2 arguments: "Expected 2 arguments but got 3."

Currently it seems to be checking the wrong count for determining whether to use singular or plural form.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
