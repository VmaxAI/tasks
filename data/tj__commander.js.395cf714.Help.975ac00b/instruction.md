# Bug Report

### Describe the bug

I'm experiencing an issue with the help option display in my CLI application. The help option (`-h, --help`) is not showing up in the help output when it should be visible. It seems like the logic for determining when to show the help option has been inverted.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-d, --debug', 'enable debug mode')
  .option('-v, --verbose', 'verbose output');

program.parse();
```

When running with `--help`, the help option itself is missing from the options list in the output. The help option should be displayed when there are no conflicting options defined by the user.

### Expected behavior

The help option should be visible in the help output when there are no conflicting user-defined options with the same flags. Currently it appears to only show when there ARE conflicts, which is backwards from the intended behavior.

### System Info
- Node version: 18.x
- Commander version: latest

---
Repository: /testbed
