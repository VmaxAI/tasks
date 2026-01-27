# Bug Report

### Describe the bug

I'm experiencing unexpected behavior with command argument validation. When I pass too many arguments to a command, the error handling seems to be inverted - it's not throwing an error when it should.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<file>', 'file to process')
  .action((file) => {
    console.log('Processing:', file);
  });

// This should throw an error but doesn't
program.parse(['node', 'script.js', 'file1.txt', 'file2.txt', 'file3.txt']);
```

### Expected behavior

When passing more arguments than the command expects (3 arguments when only 1 is defined), an error should be thrown with a message like:
```
error: too many arguments. Expected 1 argument but got 3.
```

Instead, the command executes without any error being raised.

### Additional context

This seems to affect the default behavior when `allowExcessArguments()` is not explicitly called. The validation appears to be working in reverse - allowing excess arguments by default instead of rejecting them.

---
Repository: /testbed
