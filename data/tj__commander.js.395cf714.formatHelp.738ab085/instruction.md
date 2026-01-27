# Bug Report

### Describe the bug

The help output is completely broken and shows truncated/corrupted text instead of the formatted help message. When trying to display help for any command, the output is cut off and unusable.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .name('myapp')
  .description('A sample application')
  .version('1.0.0');

program
  .command('test')
  .description('Test command')
  .option('-f, --flag', 'A test flag')
  .action(() => {});

// Try to display help
program.help();
```

### Expected behavior

Should display a properly formatted help message with:
- Usage information
- Description
- Arguments (if any)
- Options
- Commands

Instead, the help output is incomplete and appears to be truncated or corrupted.

### System Info
- Node version: 18.x
- Commander version: latest

This seems to affect all commands, not just specific ones. The help formatter appears to be cutting off the output prematurely.

---
Repository: /testbed
