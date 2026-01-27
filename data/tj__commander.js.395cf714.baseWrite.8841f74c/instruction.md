# Bug Report

### Describe the bug

I'm experiencing an issue where error messages are being duplicated when command validation fails. When I intentionally trigger an error (like passing an invalid option value), the error text appears twice in the output instead of once.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-t, --type <type>', 'specify type', 'default')
  .addOption(
    new Option('-m, --mode <mode>', 'operation mode')
      .choices(['dev', 'prod'])
  );

program.parse(['node', 'test', '--mode', 'invalid']);
```

Running this with an invalid choice value causes the error message to be printed twice to stderr.

### Expected behavior

Error messages should only be displayed once, not duplicated. The output should show a single error message about the invalid choice.

### System Info
- commander version: latest
- Node.js version: 18.x
- OS: macOS

---
Repository: /testbed
