# Bug Report

### Describe the bug

Help is being displayed even when the help option is not requested. When running commands without the help flag, the program unexpectedly shows help output and exits instead of executing the command normally.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-n, --name <name>', 'specify name')
  .action((options) => {
    console.log('Command executed with name:', options.name);
  });

// This should execute the command normally
program.parse(['node', 'script.js', '--name', 'test']);
```

### Expected behavior

The command should execute normally and print "Command executed with name: test". Instead, the help text is displayed and the program exits without running the action.

### Additional context

This seems to affect all commands - even when valid arguments are provided, help is shown instead of executing the intended command. The help should only be displayed when explicitly requested with `-h` or `--help`.

---
Repository: /testbed
