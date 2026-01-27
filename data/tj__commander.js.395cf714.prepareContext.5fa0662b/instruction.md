# Bug Report

### Describe the bug

When setting `helpWidth` to `0` in the context options, the help output doesn't respect this value and falls back to the default width of 80 instead. It seems like `helpWidth: 0` is being treated as a falsy value and ignored.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .option('-d, --debug', 'output extra debugging')
  .helpOption('-h, --help', 'display help');

// Try to set helpWidth to 0
program.configureHelp({ helpWidth: 0 });

program.parse();
```

### Expected behavior

When `helpWidth` is explicitly set to `0`, the help system should use that value instead of falling back to 80. A width of 0 might be a valid use case for some formatting scenarios.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
