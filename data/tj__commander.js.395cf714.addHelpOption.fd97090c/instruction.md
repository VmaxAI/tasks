# Bug Report

### Describe the bug

After a recent update, the help option functionality appears to be broken. When trying to customize the help option using `addHelpOption()`, the custom help option doesn't work properly and the default help behavior is not functioning as expected.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Try to customize the help option
program.addHelpOption(
  new Option('-h, --help', 'display custom help')
);

program.parse();
```

When running this code and trying to use the help option, it doesn't behave correctly. The help output is either not displayed or shows unexpected behavior.

### Expected behavior

The custom help option should be properly registered and work when invoked. The `addHelpOption()` method should correctly store and initialize the provided option so that help functionality works as intended.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
