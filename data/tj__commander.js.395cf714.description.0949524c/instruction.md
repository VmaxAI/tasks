# Bug Report

### Describe the bug

When calling `.description()` with only the first argument (description string) and no second argument (argsDescription), the method returns the current description instead of setting it. This breaks the ability to set just the description without providing argsDescription.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// This should set the description but instead returns undefined
program.description('My program description');

console.log(program.description()); // Expected: 'My program description', Actual: undefined
```

### Expected behavior

When calling `.description(str)` with only the description string, it should:
1. Set the description to the provided string
2. Return the command instance for chaining

The method should only return the current description when called with no arguments at all: `.description()`

### Additional context

This appears to affect the common use case where you want to set a description without needing to provide argument descriptions. The two-argument form should be optional.

---
Repository: /testbed
