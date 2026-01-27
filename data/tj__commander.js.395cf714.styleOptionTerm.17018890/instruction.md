# Bug Report

### Describe the bug

When using custom styling methods for option terms in help output, the styling is not being applied. The `styleOptionTerm` method appears to call `styleOptionText` but the result is not being used, so any custom styling defined in `styleOptionText` has no effect on the option terms displayed in the help text.

### Reproduction

```js
const { Command } = require('commander');

class CustomHelp extends Command.Help {
  styleOptionText(str) {
    return `**${str}**`;  // Add bold markers
  }
}

const program = new Command();
program.configureHelp({ Help: CustomHelp });

program
  .option('-d, --debug', 'enable debug mode')
  .option('-v, --verbose', 'verbose output');

console.log(program.helpInformation());
```

### Expected behavior

The option terms (like `-d, --debug`) should be styled with the custom formatting from `styleOptionText`. In the example above, they should appear with the bold markers `**-d, --debug**`.

### Actual behavior

The option terms appear without any custom styling applied, just as plain text `-d, --debug`.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
