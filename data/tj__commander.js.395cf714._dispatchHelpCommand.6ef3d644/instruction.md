# Bug Report

### Describe the bug

When trying to get help for a subcommand using the help command (e.g., `program help subcommand`), it's not working correctly. The help output either doesn't display or displays incorrectly for executable subcommands.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('serve')
  .description('Start the server')
  .option('-p, --port <number>', 'Port number')
  .action(() => {});

program
  .command('deploy', 'Deploy application')  // executable subcommand
  .description('Deploy the application');

// Try to get help for the subcommand
// This should display help for the 'deploy' command
program.parse(['node', 'test', 'help', 'deploy']);
```

### Expected behavior

The help command should properly display help information for both regular and executable subcommands. When running `program help <subcommand>`, it should show the help text for that specific subcommand.

### Additional context

This seems to affect executable subcommands in particular. Regular subcommands might work, but executable ones fail to show help properly when using the help command syntax.

---
Repository: /testbed
