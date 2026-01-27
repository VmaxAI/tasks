# Bug Report

### Describe the bug

When using subcommands with executable handlers, the subcommand is not being executed properly when no additional arguments are passed. Instead of running the executable handler, the command falls through to parsing which causes unexpected behavior.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('deploy')
  .executableSubcommandAction((args) => {
    console.log('Deploy executed');
  });

// This doesn't execute the handler as expected
program.parse(['node', 'script.js', 'deploy']);
```

### Expected behavior

The executable subcommand handler should be invoked even when no additional operands are provided to the subcommand. The handler should execute and print "Deploy executed".

### Actual behavior

The subcommand handler is not being called, and the command appears to be parsed instead of executed.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
