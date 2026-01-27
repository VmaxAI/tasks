# Bug Report

### Describe the bug

The `enablePositionalOptions()` method seems to be behaving in reverse - when I call it with `true` (or no argument since it defaults to `true`), positional options are actually disabled, and when I call it with `false`, they get enabled. This is the opposite of what the method name and documentation suggest.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// This should enable positional options, but actually disables them
program.enablePositionalOptions(true);

// This should disable positional options, but actually enables them  
program.enablePositionalOptions(false);
```

### Expected behavior

When calling `enablePositionalOptions(true)` or `enablePositionalOptions()`, positional options should be enabled. When calling `enablePositionalOptions(false)`, they should be disabled.

The current behavior appears to be inverted from what's expected based on the method name and parameter.

### Additional context

This seems like it might be a regression - the method is doing the opposite of what it's supposed to do. Also noticed that when positional options are disabled (by passing `true`), the method doesn't return `this` for chaining, which breaks the fluent API pattern used throughout Commander.

---
Repository: /testbed
