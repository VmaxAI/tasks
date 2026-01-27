# Bug Report

### Describe the bug

The `helpGroup()` method is not working as expected - it's not setting the help group heading when I pass a value, and it's not returning the command instance for chaining.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Try to set help group heading
program.helpGroup('My Commands');

// This should return the command for chaining but doesn't work
program
  .helpGroup('Another Group')
  .command('test');

// Try to get the heading - returns undefined instead of the set value
console.log(program.helpGroup()); // Expected: 'My Commands', Actual: undefined
```

### Expected behavior

1. When calling `helpGroup(heading)` with a string argument, it should set the heading and return the command instance for method chaining
2. When calling `helpGroup()` without arguments, it should return the currently set heading (or empty string if not set)

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
