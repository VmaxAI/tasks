# Bug Report

### Describe the bug

Help is being displayed when it shouldn't be. After updating, the help output is showing up every time I run my CLI command, even when I'm not passing the `--help` or `-h` flag. This makes it impossible to use the command normally.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-d, --debug', 'enable debug mode')
  .action(() => {
    console.log('Command executed');
  });

program.parse(process.argv);
```

When running:
```bash
node mycli.js --debug
```

### Expected behavior

The command should execute normally and print "Command executed". Instead, the help text is being displayed and the command exits.

### Actual behavior

Help text is displayed even though `--help` was not requested. The command never executes.

This seems to have started happening recently - the logic for detecting when help is requested appears to be inverted somehow.

---
Repository: /testbed
