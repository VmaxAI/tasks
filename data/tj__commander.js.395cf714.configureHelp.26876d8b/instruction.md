# Bug Report

### Describe the bug

The `configureHelp()` method is not working correctly when trying to retrieve the current help configuration. When called without arguments, it sets the configuration to `undefined` instead of returning the existing configuration object.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Set initial help configuration
program.configureHelp({
  sortSubcommands: true,
  sortOptions: false
});

// Try to retrieve the configuration
const config = program.configureHelp();

console.log(config); // Expected: { sortSubcommands: true, sortOptions: false }
                     // Actual: undefined
```

After calling `configureHelp()` without arguments, the stored configuration is lost and subsequent calls return `undefined`.

### Expected behavior

When `configureHelp()` is called without arguments, it should return the currently stored help configuration object without modifying it. This is the getter behavior that allows users to inspect the current configuration.

### Additional context

This appears to be a regression as the method is documented to work as both a getter (when called without arguments) and a setter (when called with a configuration object). The getter functionality is now broken.

---
Repository: /testbed
