# Bug Report

### Describe the bug

When using arguments without choices or default values, the help text is showing `(undefined)` instead of just displaying the description. This makes the help output look broken for simple arguments that only have a description.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .argument('<file>', 'input file to process')
  .action((file) => {
    console.log('Processing:', file);
  });

program.parse();
```

When running with `--help`, the output shows:
```
Arguments:
  file  input file to process (undefined)
```

### Expected behavior

The help text should only display the description without the extra `(undefined)` when there are no choices or default values:

```
Arguments:
  file  input file to process
```

The extra info in parentheses should only appear when there's actually extra information to show (like choices or default values).

---
Repository: /testbed
