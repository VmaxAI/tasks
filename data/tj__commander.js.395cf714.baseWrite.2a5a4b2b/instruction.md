# Bug Report

### Describe the bug

I'm experiencing an issue with error output formatting. When displaying error messages, empty lines are being removed and all output appears to be trimmed, which breaks the formatting of multi-line error messages.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('test')
  .action(() => {
    program.error('Error message\n\nWith blank lines\n');
  });

program.parse();
```

### Expected behavior

The error output should preserve the original formatting including:
- Empty lines between text
- Leading/trailing whitespace when intentionally included

Currently, the blank lines are being stripped out and the trailing newline is removed, which causes error messages to display incorrectly when they rely on specific formatting.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
