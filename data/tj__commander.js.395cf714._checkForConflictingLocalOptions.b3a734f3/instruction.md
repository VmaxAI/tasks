# Bug Report

### Describe the bug

Conflicting options are no longer being detected properly. When I use two options that are supposed to conflict with each other, the program doesn't throw an error and both options are processed together, which leads to unexpected behavior.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-a, --option-a', 'First option')
  .option('-b, --option-b', 'Second option')
  .conflictsWith('option-a', 'option-b');

program.parse(['-a', '-b'], { from: 'user' });
// Expected: Error about conflicting options
// Actual: No error thrown, both options are set
```

### Expected behavior

When two conflicting options are used together, an error should be thrown indicating that these options cannot be used simultaneously. Instead, both options are being accepted without any warning or error.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
