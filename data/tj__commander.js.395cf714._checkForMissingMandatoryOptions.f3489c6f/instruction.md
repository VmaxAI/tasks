# Bug Report

### Describe the bug

When a mandatory option is set to `undefined` at the command level but then set to a valid value in a subcommand, the validation incorrectly throws a missing mandatory option error. The issue appears to be related to how the command hierarchy is traversed when checking for mandatory options.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-c, --config <path>', 'config file path')
  .requiredOption('-r, --required <value>', 'required option');

program
  .command('subcommand')
  .action(() => {
    console.log('Subcommand executed');
  });

// This throws an error even though the parent command's required option
// might be satisfied by the subcommand context
program.parse(['node', 'test', 'subcommand', '-r', 'value']);
```

### Expected behavior

The mandatory option validation should properly handle the case where options are defined at different levels of the command hierarchy. When a subcommand is executed, the validation should check options in the correct order and not fail if the mandatory option has a valid value at any level.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
