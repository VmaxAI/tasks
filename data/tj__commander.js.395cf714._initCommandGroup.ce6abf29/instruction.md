# Bug Report

### Describe the bug

When setting a default help group for commands, subcommands that don't already have a help group assigned are not inheriting the default help group. It seems like the default help group is only being applied to subcommands that already have a help group set, which is the opposite of what should happen.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program.configureHelp({
  sortSubcommands: true,
  sortOptions: true
});

// Set a default help group for all subcommands
program.setDefaultCommandGroup('My Commands');

// Add a subcommand without explicitly setting a help group
program
  .command('test')
  .description('Test command');

// Add another subcommand with an explicit help group
program
  .command('other')
  .description('Other command')
  .helpGroup('Custom Group');

program.parse();
```

### Expected behavior

The `test` command should be grouped under "My Commands" in the help output since it doesn't have an explicit help group set. The `other` command should remain in "Custom Group" since it has an explicit group.

### Actual behavior

The `test` command is not being grouped under "My Commands". Only commands that already have a help group explicitly set seem to be affected by the default command group setting.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
