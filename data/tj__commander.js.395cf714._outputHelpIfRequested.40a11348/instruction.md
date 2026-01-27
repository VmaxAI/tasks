# Bug Report

### Describe the bug

Help is being displayed even when the help option is NOT provided on the command line. The expected behavior is that help should only be shown when explicitly requested (e.g., with `--help` or `-h`), but currently it's showing up in normal command execution.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-n, --name <name>', 'specify name')
  .action((options) => {
    console.log('Command executed with:', options);
  });

// Run without help flag
program.parse(['node', 'test.js', '--name', 'John']);
```

### Expected behavior

The command should execute normally and print "Command executed with: { name: 'John' }" without displaying help text.

### Actual behavior

Help text is displayed and the program exits, even though no help flag was passed.

This seems to have started happening recently. When I run commands without `--help`, the help output appears anyway and the actual command doesn't execute.

---
Repository: /testbed
