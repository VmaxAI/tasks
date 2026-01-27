# Bug Report

### Describe the bug

When using the help command with a subcommand that has an executable handler, the help is displayed but then the program attempts to dispatch the subcommand anyway. This causes unexpected behavior where the executable subcommand is invoked after showing help, instead of just displaying the help and exiting.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('deploy', 'deploy with external handler')
  .description('Deploy the application');

program.parse(['node', 'test', 'help', 'deploy']);
```

### Expected behavior

When running `help deploy` for a subcommand with an executable handler, it should:
1. Display the help for the deploy subcommand
2. Exit without attempting to execute the deploy command

### Actual behavior

The help is shown, but then the program tries to dispatch/execute the deploy subcommand as well, leading to the executable handler being invoked when it shouldn't be.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
