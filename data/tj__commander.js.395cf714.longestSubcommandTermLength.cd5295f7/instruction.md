# Bug Report

### Describe the bug

The help output for subcommands is not displaying correctly - the column widths seem wrong and subcommand descriptions are not aligning properly. It looks like the formatting calculation for subcommand terms is broken.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('short')
  .description('A short command');

program
  .command('very-long-subcommand-name')
  .description('A command with a long name');

program
  .command('medium-cmd')
  .description('Another command');

program.parse();
```

When running with `--help`, the subcommand descriptions don't align correctly in columns. The spacing appears to be using the width of the shortest command instead of the longest one.

### Expected behavior

The help formatter should calculate the maximum width across all visible subcommands so that descriptions align in a neat column. Currently it seems to be doing the opposite - using a minimum width calculation instead.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
