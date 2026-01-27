# Bug Report

### Describe the bug

When defining an option with a default value but no custom parser function, the default value is not being set correctly. The option ends up with `undefined` as its default instead of the provided value.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .option('-p, --port <number>', 'port number', 3000);

program.parse(['node', 'test']);

console.log(program.opts().port);
// Expected: 3000
// Actual: undefined
```

The issue occurs when you pass a default value as the third parameter without providing a custom parser function. The default value should be applied to the option, but it's being ignored.

### Expected behavior

When an option is defined with a default value (and no parser function), that default value should be used when the option is not provided by the user.

### Additional context

This seems to affect options where:
1. A default value is provided
2. No custom parser/validator function is specified
3. The user doesn't provide a value for the option at runtime

---
Repository: /testbed
