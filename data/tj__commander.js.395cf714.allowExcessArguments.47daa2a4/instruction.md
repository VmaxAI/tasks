# Bug Report

### Describe the bug

The `allowExcessArguments()` method is not working as expected. When I call it to enable excess arguments, it seems to have the opposite effect - it disallows them instead. Similarly, when trying to disable excess arguments, they are still allowed.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .allowExcessArguments(true)
  .argument('<file>')
  .action((file) => {
    console.log('file:', file);
  });

// Try parsing with excess arguments
// Expected: should work without errors
// Actual: throws error about excess arguments
program.parse(['node', 'test.js', 'myfile.txt', 'extra', 'args']);
```

Also happens in reverse:

```js
const program2 = new Command();

program2
  .allowExcessArguments(false)
  .argument('<file>')
  .action((file) => {
    console.log('file:', file);
  });

// Try parsing with excess arguments
// Expected: should throw error about excess arguments
// Actual: works fine, no error thrown
program2.parse(['node', 'test.js', 'myfile.txt', 'extra', 'args']);
```

### Expected behavior

When `allowExcessArguments(true)` is called, excess arguments should be allowed without throwing errors. When `allowExcessArguments(false)` is called, excess arguments should trigger an error.

The method also doesn't seem to be chainable anymore - it's not returning the command instance properly.

---
Repository: /testbed
