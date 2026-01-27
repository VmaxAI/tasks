# Bug Report

### Describe the bug

When generating help text, argument names are not displaying correctly. Instead of showing the actual argument name, the output appears to be showing `undefined` or an object representation.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<source>', 'source file')
  .argument('[destination]', 'destination file')
  .action((source, destination) => {
    // action code
  });

program.help();
```

### Expected behavior

The help output should display the argument names like:
```
Arguments:
  source          source file
  destination     destination file
```

Instead, it seems like the argument names are not being extracted properly from the argument objects.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
