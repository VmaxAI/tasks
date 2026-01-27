# Bug Report

### Describe the bug

I'm experiencing an issue where argument descriptions are not being displayed correctly in the help output. Instead of showing the actual description text, it appears that nothing or undefined is being rendered.

### Reproduction

```js
const program = require('commander').program;

program
  .argument('<file>', 'input file to process')
  .argument('[output]', 'optional output destination')
  .action(() => {});

program.parse();
```

When running with `--help`, the descriptions for the arguments are missing or showing as undefined instead of displaying "input file to process" and "optional output destination".

### Expected behavior

The help text should display the argument descriptions that were provided when defining the arguments. For example:
```
Arguments:
  file       input file to process
  output     optional output destination
```

### System Info
- Node version: 18.x
- commander version: latest

---
Repository: /testbed
