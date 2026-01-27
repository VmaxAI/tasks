# Bug Report

### Describe the bug

When displaying error messages, trailing newlines are being removed unexpectedly. This causes errors to appear on the same line as subsequent output, making the console output difficult to read.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<file>')
  .action((file) => {
    // Trigger an error with a message that has trailing newline
    throw new Error('File not found\n');
  });

program.parse();
```

When an error occurs, the error message gets printed without its trailing newline, causing the next prompt or output to appear on the same line as the error message instead of on a new line.

### Expected behavior

Error messages should preserve their original formatting, including trailing whitespace and newlines. The error output should maintain the same format as provided, so that subsequent console output appears on a new line.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
