# Bug Report

### Describe the bug

When trying to use a valid subcommand, the help message is displayed instead of executing the subcommand. It seems like the command parser is treating valid subcommands as if they don't exist.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('serve')
  .description('Start the server')
  .action(() => {
    console.log('Server started');
  });

program.parse(['node', 'test', 'serve']);
```

### Expected behavior

The subcommand should execute normally and print "Server started". Instead, the help message is shown as if the subcommand wasn't found.

### System Info
- commander.js version: latest
- Node version: 18.x

This is blocking our CLI tool from working properly. Any help would be appreciated!

---
Repository: /testbed
