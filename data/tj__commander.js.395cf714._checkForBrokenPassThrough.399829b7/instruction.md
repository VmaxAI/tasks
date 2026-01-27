# Bug Report

### Describe the bug

I'm encountering an issue where `passThroughOptions` validation is incorrectly throwing an error even when the configuration is valid. The error message says `passThroughOptions cannot be used for '...' without turning on enablePositionalOptions for parent command(s)` but this happens even when I've properly configured `enablePositionalOptions` on the command itself (not using parent commands).

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .name('myapp')
  .enablePositionalOptions()
  .passThroughOptions();

// This throws an error but shouldn't
program.parse(process.argv);
```

The error is thrown even though `enablePositionalOptions()` is called on the same command that uses `passThroughOptions()`.

### Expected behavior

When `enablePositionalOptions()` and `passThroughOptions()` are both set on the same command (without a parent command), it should work without throwing an error. The validation should only fail if there's a parent command that doesn't have `enablePositionalOptions` enabled.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
