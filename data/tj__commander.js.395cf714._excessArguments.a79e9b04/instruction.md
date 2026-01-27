# Bug Report

### Describe the bug

The error message for excess arguments is displaying incorrect information. When too many arguments are provided to a command, the error message shows the expected count instead of the actual received count.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .name('myapp')
  .argument('<file>', 'file to process')
  .action((file) => {
    console.log('Processing:', file);
  });

// Try to parse with too many arguments
program.parse(['node', 'myapp', 'file1.txt', 'file2.txt', 'file3.txt']);
```

### Expected behavior

The error message should show:
```
error: too many arguments. Expected 1 argument but got 3.
```

### Actual behavior

The error message incorrectly shows the expected count twice instead of showing the actual received count.

### System Info
- commander.js version: latest
- Node.js version: 18.x

This makes it confusing for users to understand what went wrong when they provide extra arguments.

---
Repository: /testbed
