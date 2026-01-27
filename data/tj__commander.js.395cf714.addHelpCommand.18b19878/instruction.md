# Bug Report

### Describe the bug

When calling `addHelpCommand()` with a string argument and description, the help command is not being added correctly. The method seems to have inverted logic - it's treating string arguments as if they were objects and vice versa.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Try to add a custom help command with string arguments
program.addHelpCommand('aide', 'afficher l\'aide');

program.parse();
```

Expected: A custom help command named "aide" should be added
Actual: The help command is not added properly, and the implicit help command flag is set incorrectly

### Steps to reproduce

1. Create a new Command instance
2. Call `addHelpCommand()` with string arguments (custom name and description)
3. The help command doesn't work as expected

This appears to be a regression - the method used to work correctly with both string and object arguments for backwards compatibility.

### Expected behavior

`addHelpCommand()` should accept both:
- String arguments: `addHelpCommand('help', 'display help')`  
- Object argument: `addHelpCommand(helpCommandObject)`

And properly set up the help command in both cases.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
