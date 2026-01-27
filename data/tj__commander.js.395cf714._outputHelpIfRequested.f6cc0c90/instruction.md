# Bug Report

### Describe the bug

When using the help option (e.g., `-h` or `--help`), the program exits immediately without actually displaying the help text. The help content is not printed to the console before the process terminates.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .name('my-app')
  .description('A sample application')
  .version('1.0.0')
  .option('-d, --debug', 'enable debug mode')
  .option('-v, --verbose', 'verbose output');

program.parse(process.argv);
```

Run with:
```bash
node my-app.js --help
```

### Expected behavior

The help text should be displayed showing all available options, commands, and usage information before the program exits. Currently, the process just exits without printing anything.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
