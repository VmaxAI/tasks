# Bug Report

### Describe the bug

When calling `helpGroup()` without arguments to retrieve the current help group heading, the method returns the Command instance instead of the heading string when no heading has been set.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Get help group before setting it
const heading = program.helpGroup();
console.log('Type:', typeof heading);
console.log('Value:', heading);

// Expected: empty string ''
// Actual: returns the Command object itself
```

### Expected behavior

When `helpGroup()` is called without arguments and no heading has been set, it should return an empty string `''` as indicated by the return type annotation. The method should only return the Command instance when called with an argument (setter mode).

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
