# Bug Report

### Describe the bug

When using custom styles for command descriptions in the help formatter, the styling is not being applied correctly. The description text appears unstyled in the help output even though `styleDescriptionText()` is being called.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Override styleDescriptionText to add color/formatting
program.configureHelp({
  styleDescriptionText: (str) => {
    return `\x1b[36m${str}\x1b[0m`; // cyan color
  }
});

program
  .command('test')
  .description('This should be styled')
  .action(() => {});

program.parse();
```

Run with `--help` flag and the command description will not have the cyan styling applied, even though option descriptions and other text are styled correctly.

### Expected behavior

Command descriptions should be styled using the `styleDescriptionText()` method, just like option descriptions and other help text elements.

### System Info
- commander version: latest
- Node.js: v18.x

---
Repository: /testbed
