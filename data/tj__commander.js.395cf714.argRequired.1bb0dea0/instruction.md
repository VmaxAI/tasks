# Bug Report

### Describe the bug

I'm experiencing unexpected behavior with the `argRequired()` method. When I call it multiple times on the same argument, it seems to toggle the required state instead of keeping it as required.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .argument('<file>')
  .argRequired()
  .argRequired();

// The argument becomes optional after calling argRequired() twice
// Expected: argument should remain required
```

### Expected behavior

Calling `argRequired()` should always set the argument as required, regardless of how many times it's called. The method should be idempotent - calling it once or multiple times should have the same effect.

### Additional context

This is causing issues in my code where I have helper functions that ensure arguments are required, but if they're called multiple times (e.g., through different code paths), the argument ends up being optional instead of required.

---
Repository: /testbed
