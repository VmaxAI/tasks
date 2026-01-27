# Bug Report

### Describe the bug

When using `showGlobalOptions` with Commander.js, the help output is not displaying any global options that should be inherited from parent commands. It appears that global options are completely missing from the help text even though they are defined on parent commands and should be visible.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-g, --global <value>', 'A global option')
  .option('-v, --verbose', 'Verbose output');

const subcommand = program
  .command('sub')
  .option('-l, --local <value>', 'A local option')
  .configureHelp({ showGlobalOptions: true });

subcommand.help();
```

### Expected behavior

The help output for the subcommand should display both the local options and the global options inherited from the parent command (like `-g, --global` and `-v, --verbose`). The global options section should show all non-hidden options from ancestor commands.

### Actual behavior

The global options section is empty or not showing the expected inherited options from parent commands.

### System Info
- Commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
