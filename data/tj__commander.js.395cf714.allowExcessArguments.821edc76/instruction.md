# Bug Report

### Describe the bug

The `allowExcessArguments()` method is not working as expected. When I call it to enable or disable excess argument handling, the behavior seems completely broken. The method doesn't respect the parameter I pass to it, and sometimes it returns `undefined` instead of the command instance, which breaks method chaining.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Try to allow excess arguments
program.allowExcessArguments(true);
// Expected: excess arguments should be allowed
// Actual: behavior is unpredictable

// Try to disable excess arguments
program.allowExcessArguments(false);
// Expected: excess arguments should be disallowed
// Actual: opposite behavior or undefined returned

// Method chaining breaks
const result = program
  .allowExcessArguments(true)
  .version('1.0.0');  // TypeError: Cannot read property 'version' of undefined
```

### Expected behavior

1. Calling `allowExcessArguments(true)` should enable excess arguments
2. Calling `allowExcessArguments(false)` should disable excess arguments
3. The method should always return the command instance to support method chaining
4. Multiple calls should work correctly and respect the parameter passed each time

### System Info
- commander version: latest
- Node.js version: 18.x

This is blocking my CLI tool development as I can't properly configure argument handling anymore.

---
Repository: /testbed
