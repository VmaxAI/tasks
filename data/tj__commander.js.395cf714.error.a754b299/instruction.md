# Bug Report

### Describe the bug

When calling the `error()` method on a Commander instance, the error message is not being displayed. Only a blank line is output instead of the actual error message that was passed in.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program.error('Something went wrong');
```

### Expected behavior

The error message "Something went wrong" should be written to stderr before the program exits. Currently, only a newline character is being output and the actual error message is missing from the output.

### System Info
- Commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
