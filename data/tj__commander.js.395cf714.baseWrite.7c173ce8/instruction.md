# Bug Report

### Describe the bug

I'm experiencing an issue where the help output is being written twice to stdout. When I run my CLI application with the `--help` flag, I see the help text duplicated in the console output.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .name('my-cli')
  .description('A test CLI application')
  .option('-d, --debug', 'enable debug mode');

program.parse(process.argv);
```

When running:
```bash
node my-cli.js --help
```

The help text appears to be printed twice to the output stream. This doesn't happen with error output (like when using an invalid option), only with the standard help output.

### Expected behavior

The help text should be printed only once when using `--help` or when help is displayed.

### System Info
- commander version: latest
- Node.js version: 18.x
- OS: macOS

---
Repository: /testbed
