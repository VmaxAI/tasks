# Bug Report

### Describe the bug

The `allowExcessArguments()` method is not working as expected. When calling this method with `false` to disable excess arguments, it seems to have no effect and excess arguments are still allowed.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<file>')
  .allowExcessArguments(false)
  .action((file) => {
    console.log('Processing:', file);
  });

// This should throw an error for excess arguments, but doesn't
program.parse(['node', 'script.js', 'file1.txt', 'extra1', 'extra2']);
```

### Expected behavior

When `allowExcessArguments(false)` is called, the program should reject excess arguments and throw an error. The method should also return the command instance for chaining, not a boolean value.

### Additional context

This appears to affect the ability to strictly validate command arguments. Also noticed that chaining after `allowExcessArguments()` doesn't work properly anymore.

---
Repository: /testbed
