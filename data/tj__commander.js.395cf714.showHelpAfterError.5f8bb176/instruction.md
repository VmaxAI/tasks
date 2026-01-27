# Bug Report

### Describe the bug

When calling `showHelpAfterError()` with a string argument, the help text is not being displayed after errors. Instead of treating the string as a truthy value (which should enable help display with custom text), it seems to be getting converted to a boolean incorrectly.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .showHelpAfterError('(add --help for additional information)')
  .argument('<file>')
  .action(() => {});

// When running with invalid arguments, the custom help message should appear
// but it doesn't show up
```

Steps to reproduce:
1. Create a command with `showHelpAfterError()` passing a custom string message
2. Trigger an error by providing invalid arguments
3. The custom help message doesn't display after the error

### Expected behavior

When passing a string to `showHelpAfterError()`, it should:
- Display the help after an error occurs
- Show the custom string message provided

The method should treat any string value as truthy and enable the help display feature with that custom message.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
