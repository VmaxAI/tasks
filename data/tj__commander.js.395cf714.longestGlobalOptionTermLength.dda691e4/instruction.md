# Bug Report

### Describe the bug

The help text formatting for global options is displaying incorrectly. When multiple global options are present, the column widths seem to be calculated wrong, causing misaligned output in the help display.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-d, --debug', 'output extra debugging')
  .option('-s, --small', 'small option')
  .option('-v, --verbose', 'verbose mode')
  .option('--very-long-option-name <value>', 'an option with a very long name');

program.parse();
```

When running with `--help`, the global options section doesn't align properly. The option descriptions appear to be using the wrong indentation, making the help output look broken.

### Expected behavior

All option descriptions should be aligned in a single column, with the column width determined by the longest option term. The formatting should look clean and professional like it did in previous versions.

### System Info
- commander.js version: latest
- Node.js version: v18.x

---
Repository: /testbed
