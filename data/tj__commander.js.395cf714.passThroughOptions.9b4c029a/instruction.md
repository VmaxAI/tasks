# Bug Report

### Describe the bug

I'm experiencing an issue with `passThroughOptions()` where it seems to be doing the opposite of what it should. When I call `passThroughOptions(true)`, unknown options are NOT being passed through, and when I call `passThroughOptions(false)`, they ARE being passed through.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .passThroughOptions(true)
  .option('-k, --known <value>', 'a known option');

// Parse with an unknown option
program.parse(['node', 'test.js', '--known', 'value', '--unknown', 'option']);

// Expected: unknown options should be passed through
// Actual: unknown options are NOT passed through (error is thrown)
```

Also noticed that the method seems to be returning something unexpected - chaining doesn't work properly anymore.

### Expected behavior

When `passThroughOptions(true)` is called, unknown options should be allowed and passed through. When `passThroughOptions(false)` is called (or by default), unknown options should cause an error.

The method should also return the command instance for proper chaining.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
