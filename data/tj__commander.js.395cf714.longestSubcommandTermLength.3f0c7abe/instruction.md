# Bug Report

### Describe the bug

I'm experiencing an issue with help text formatting where subcommand terms are displaying with incorrect widths/alignment. The help output looks broken when multiple subcommands are present, with the alignment being completely off.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('short')
  .description('A short command');

program
  .command('very-long-command-name')
  .description('A command with a long name');

program
  .command('medium-cmd')
  .description('Medium length command');

program.outputHelp();
```

When running this, the help output shows misaligned descriptions and the spacing calculation seems wrong. The longer the command name, the worse the alignment gets.

### Expected behavior

All subcommand descriptions should be properly aligned in the help output, regardless of the command name length. The formatting should calculate the correct maximum width needed for all subcommand terms and align the descriptions accordingly.

### System Info
- commander.js version: latest
- Node.js version: v18.x

---
Repository: /testbed
