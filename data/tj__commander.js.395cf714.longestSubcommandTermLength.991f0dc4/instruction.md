# Bug Report

### Describe the bug

The help text formatting for subcommands is displaying incorrectly. When multiple subcommands are present, the column width seems to be calculated wrong, causing misalignment in the help output.

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
  .description('Medium length command');

program.parse();
```

Run with `--help` flag and observe that the description text is not properly aligned. The column width appears to be too narrow for the longest subcommand name.

### Expected behavior

The help output should calculate the proper column width based on the longest subcommand term, so all descriptions align correctly in a column format.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
