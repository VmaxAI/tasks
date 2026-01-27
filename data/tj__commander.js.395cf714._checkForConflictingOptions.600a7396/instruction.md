# Bug Report

### Describe the bug

When using nested commands (subcommands), conflicting options are not being detected properly. The validation seems to skip checking the current command's options for conflicts.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-d, --debug', 'enable debug mode')
  .conflictsWith('verbose');

program
  .command('sub')
  .option('-v, --verbose', 'verbose output')
  .conflictsWith('debug')
  .action(() => {
    console.log('Subcommand executed');
  });

// This should detect a conflict but doesn't
program.parse(['node', 'script', 'sub', '-v', '-d']);
```

### Expected behavior

The program should detect the conflicting options between the parent command and subcommand and throw an error. Instead, it appears to be skipping the conflict check for one of the commands in the hierarchy.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
