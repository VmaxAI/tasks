# Bug Report

### Describe the bug

When using the `help` command with a subcommand that has an executable handler, the help output is not being displayed correctly. Instead of showing the help information for the subcommand, it seems to be attempting to execute the subcommand itself.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('deploy', 'deploy description')
  .option('-e, --env <env>', 'environment');

program.parse(['node', 'test', 'help', 'deploy']);
```

### Expected behavior

The help command should display the help information for the `deploy` subcommand, regardless of whether it has an executable handler or not. Currently it only works for non-executable subcommands.

### Additional context

This issue appears to affect subcommands that are configured with executable handlers. Regular subcommands (without executable handlers) display help correctly when using `help <subcommand>`.

---
Repository: /testbed
