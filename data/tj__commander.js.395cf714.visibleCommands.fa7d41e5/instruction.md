# Bug Report

### Describe the bug

When displaying help output for commands with subcommands, all the subcommands are missing from the help text. Only hidden commands are being shown instead of the visible ones.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('build')
  .description('Build the project');

program
  .command('test')
  .description('Run tests');

program
  .command('deploy')
  .description('Deploy to production')
  .hideHelp(); // This one is hidden

program.parse();
```

When running `node app.js --help`, the output only shows the hidden `deploy` command, but `build` and `test` commands are not listed in the help output.

### Expected behavior

The help output should display all visible subcommands (`build` and `test`) and exclude hidden ones (`deploy`). Hidden commands should not appear in the help text.

### Additional context

This seems to have started recently. The help system appears to be filtering commands in reverse - showing hidden ones instead of visible ones.

---
Repository: /testbed
