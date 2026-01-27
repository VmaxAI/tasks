# Bug Report

### Describe the bug

Error messages are being trimmed when output, which causes formatting issues with multi-line error output. Leading and trailing whitespace is being removed from error strings, breaking the intended formatting of help text and error messages.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<name>')
  .action((name) => {
    // trigger an error
  });

// Parse with invalid input to trigger error output
program.parse(['node', 'test']);
```

When an error is displayed, any intentional whitespace formatting (like indentation or blank lines) gets stripped out. This affects the readability of multi-line error messages and help text that rely on proper spacing.

### Expected behavior

Error output should preserve the original formatting including leading/trailing whitespace and newlines. The error writer should output strings exactly as provided without modification.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
