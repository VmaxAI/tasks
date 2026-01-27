# Bug Report

### Describe the bug

When customizing the help option using `helpOption()` with custom flags but no description, the help option doesn't appear in the correct option group. The option seems to be created but not properly initialized for grouping.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Set up default option group
program.configureHelp({
  showGlobalOptions: true
});

// Customize help option with just flags
program.helpOption('-H, --help');

program.parse();
```

When running with `--help`, the help option is not properly grouped or may not display as expected in the help output.

### Expected behavior

The help option should be properly initialized and grouped even when only custom flags are provided without a custom description. It should work the same way as when both flags and description are provided.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
