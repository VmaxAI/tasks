# Bug Report

### Describe the bug

When creating subcommands and copying inherited settings from a parent command, the `showHelpAfterError` configuration is not being applied correctly. Instead, it seems like `showSuggestionAfterError` is being used for both settings, causing the help display behavior to be incorrect.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program.showHelpAfterError('(add --help for additional information)');

const subcommand = new Command('sub')
  .description('A subcommand');

program.addCommand(subcommand);

// When an error occurs in the subcommand, the help message behavior
// doesn't match what was configured on the parent command
```

### Expected behavior

When `showHelpAfterError` is configured on a parent command, subcommands should inherit this setting correctly and display the configured help message after errors. Currently, the subcommand doesn't respect this setting.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
