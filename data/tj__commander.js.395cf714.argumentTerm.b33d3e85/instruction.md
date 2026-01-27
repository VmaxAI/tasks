# Bug Report

### Describe the bug
When generating help text for command arguments, the output is showing `[object Object]` instead of the actual argument name. This appears to be breaking the help formatter when displaying command usage information.

### Reproduction
```js
const { Command } = require('commander');

const program = new Command();
program
  .argument('<file>', 'file to process')
  .argument('[output]', 'output destination')
  .action((file, output) => {
    console.log('Processing:', file);
  });

program.parse();
```

When running with `--help`, the arguments section shows object representations instead of the proper argument names like `<file>` and `[output]`.

### Expected behavior
The help output should display the argument names properly formatted (e.g., `<file>`, `[output]`), not as `[object Object]`.

### System Info
- Node version: 18.x
- commander version: latest

---
Repository: /testbed
