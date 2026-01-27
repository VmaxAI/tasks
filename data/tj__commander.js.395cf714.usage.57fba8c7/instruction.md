# Bug Report

### Describe the bug

When trying to set a custom usage string for a command, the method doesn't actually update the usage. The custom usage string is ignored and the command continues to use the auto-generated usage format.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .name('my-cli')
  .usage('custom usage string');

console.log(program.usage());
// Expected: 'custom usage string'
// Actual: returns the Command object instead of the custom string
```

The usage string is never actually stored, so calling `.usage()` without arguments doesn't return the custom value that was set.

### Expected behavior

When calling `.usage(str)` with a string argument, it should store that custom usage string and return the command for chaining. When calling `.usage()` without arguments, it should return the previously set custom usage string.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
