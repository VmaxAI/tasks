# Bug Report

### Describe the bug

Error messages are being trimmed and empty error strings are being suppressed when using the command library. This causes issues when trying to display error output that intentionally includes whitespace or when the error formatting relies on newlines.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('test')
  .action(() => {
    // Error message with intentional whitespace/formatting
    program.error('\n\nImportant Error\n\n');
  });

program.parse();
```

When running this code, the leading and trailing newlines are stripped from the error message, breaking the intended formatting.

### Expected behavior

Error messages should be output exactly as provided without any modification to whitespace. If I pass `'\n\nImportant Error\n\n'` as an error message, it should be displayed with the newlines intact, not trimmed to just `'Important Error'`.

This is particularly problematic when:
- Intentionally formatting error messages with spacing
- Using empty strings for specific formatting purposes
- Relying on newline characters for output layout

### System Info
- Node version: 18.x
- commander version: latest

---
Repository: /testbed
