# Bug Report

### Describe the bug

I'm experiencing an issue with argument term styling in the help output. When displaying command arguments, the first character of each argument term is being cut off. For example, if an argument is defined as `<file>`, it appears as `file>` in the help text.

### Reproduction

```js
const program = require('commander');

program
  .argument('<input>', 'input file')
  .argument('[output]', 'output file')
  .action(() => {});

program.parse();
```

When running with `--help`, the arguments section shows:
```
Arguments:
  nput>      input file
  output]    output file
```

Instead of the expected:
```
Arguments:
  <input>    input file
  [output]   output file
```

### Expected behavior

The argument terms should display with their full names including the first character. The angle brackets or square brackets notation should be preserved in the output.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
