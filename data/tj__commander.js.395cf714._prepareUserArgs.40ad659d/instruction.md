# Bug Report

### Describe the bug

I'm experiencing a parsing issue when using the `parse()` method with custom parse options. When I try to parse command-line arguments with `{ from: 'eval' }`, the program crashes with an unexpected error instead of properly parsing the arguments.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-d, --debug', 'output extra debugging')
  .option('-s, --small', 'small pizza size');

// This causes an error
program.parse(['-d', '-s'], { from: 'eval' });
```

Running this code results in an error being thrown. The same issue occurs with other `from` values like `'user'` when trying to parse arguments.

### Expected behavior

The `parse()` method should correctly handle the arguments based on the `from` option specified in parseOptions. It should extract user arguments according to the convention specified without throwing errors.

### System Info
- commander version: latest
- Node.js version: v18.x
- OS: macOS

This seems to have started happening recently. Previously this code was working fine for parsing arguments in different contexts (eval, user, etc.).

---
Repository: /testbed
