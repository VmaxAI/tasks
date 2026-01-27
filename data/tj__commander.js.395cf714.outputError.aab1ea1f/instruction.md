# Bug Report

### Describe the bug

Error messages are being truncated when displayed to the user. The last character of error output is getting cut off, which makes error messages incomplete and sometimes confusing to read.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('test')
  .action(() => {
    program.error('This is an error message!');
  });

program.parse();
```

When running this with `node script.js test`, the output shows:
```
This is an error message
```

Notice the exclamation mark at the end is missing.

### Expected behavior

The complete error message should be displayed including the last character:
```
This is an error message!
```

This affects all error messages being output through the command framework, making debugging harder when the last character contains important information (like punctuation, closing brackets, etc).

### System Info
- Node version: v18.x
- commander version: latest

---
Repository: /testbed
