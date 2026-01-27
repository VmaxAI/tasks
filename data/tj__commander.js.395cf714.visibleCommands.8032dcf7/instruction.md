# Bug Report

### Describe the bug

After updating to the latest version, the help command is not displaying any subcommands. When I run `--help` on a command that has multiple subcommands, the help output shows no available commands even though they exist and work when called directly.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('serve')
  .description('start the server');

program
  .command('build')
  .description('build the project');

program.parse();
```

When running `node app.js --help`, the output shows no subcommands listed, but running `node app.js serve` or `node app.js build` works fine.

### Expected behavior

The help output should list all available subcommands (serve, build, etc.) that are not explicitly hidden. Previously this worked correctly and showed all the commands.

### Additional context

This seems to have started after a recent update. The commands themselves still work when called directly, it's just the help display that's broken. Also noticed that if I explicitly hide a command with `._hidden = true`, that command now appears in the help output which is the opposite of what should happen.

---
Repository: /testbed
