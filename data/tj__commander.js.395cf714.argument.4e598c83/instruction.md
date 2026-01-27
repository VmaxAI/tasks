# Bug Report

### Describe the bug

When using the `.argument()` method with a custom parser function and default value, the arguments are being assigned incorrectly. The default value is being treated as the parser function and the parser function is being treated as the default value.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Define an argument with a custom parser and default value
program
  .argument('<number>', 'a number argument', parseFloat, 0)
  .action((num) => {
    console.log('Parsed number:', num);
    console.log('Type:', typeof num);
  });

// When parsing a number like "42.5"
program.parse(['node', 'test', '42.5']);
```

### Expected behavior

The custom parser function (`parseFloat`) should be used to parse the argument value, and the default value (`0`) should be applied when no argument is provided. The parsed value should be a number.

### Actual behavior

The parser and default value seem to be swapped - the default value is being used as the parser and the parser is being used as the default value. This causes type errors and unexpected behavior when processing arguments.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
