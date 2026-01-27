# Bug Report

### Describe the bug

The `addHelpOption()` method is not working as expected. When I try to add a custom help option to a command, it doesn't seem to be registered properly and the method returns the wrong value.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

const customHelpOption = new Option('-h, --help', 'display custom help');
const result = program.addHelpOption(customHelpOption);

// Expected: result should be the program instance for chaining
// Actual: result is the option itself

// Also, the help option doesn't seem to be set on the command
console.log(program._helpOption); // Expected: customHelpOption, Actual: null
```

### Expected behavior

1. The method should return the command instance (for method chaining)
2. The custom help option should be properly stored in `_helpOption`

This breaks method chaining patterns like:
```js
program
  .addHelpOption(customOption)
  .addOption(anotherOption)  // This would fail
```

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
