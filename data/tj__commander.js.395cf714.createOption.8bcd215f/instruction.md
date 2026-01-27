# Bug Report

### Describe the bug

I'm experiencing an issue with the `createOption` method where it's not handling arguments correctly. When I try to create an option with just flags (no description), the behavior is unexpected.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// This doesn't work as expected anymore
const option = program.createOption('-v, --verbose');
console.log(option); // Expected: Option object, Actual: string '-v, --verbose'
```

When calling `createOption` with only the flags parameter, instead of getting an Option object back, I'm getting the flags string itself returned.

### Expected behavior

The method should return a proper Option object even when only flags are provided (description is optional). Previously this worked fine and would create an Option with just the flags set.

### System Info
- commander version: latest
- Node.js: v18.x

---
Repository: /testbed
