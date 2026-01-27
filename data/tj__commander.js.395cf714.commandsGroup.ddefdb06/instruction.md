# Bug Report

### Describe the bug

The `commandsGroup()` method is not working as expected when used as a getter. When trying to retrieve the current commands group heading, it always returns `undefined` instead of the previously set value.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Set a commands group heading
program.commandsGroup('My Commands');

// Try to get the current heading
const heading = program.commandsGroup();

console.log(heading); // Expected: 'My Commands', Actual: undefined
```

### Expected behavior

When `commandsGroup()` is called without arguments, it should return the currently set commands group heading. After setting it to `'My Commands'`, calling the getter should return that same string.

### Additional context

This seems to have broken recently. The setter part works (you can set a heading), but the getter always returns `undefined` regardless of what was previously set.

---
Repository: /testbed
