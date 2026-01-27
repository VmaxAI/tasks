# Bug Report

### Describe the bug

The `optionsGroup()` method is not working as expected when called without arguments. Instead of returning the current heading value, it's setting the heading to `undefined` and returning that value.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Set an options group heading
program.optionsGroup('Advanced Options');

// Try to get the current heading
const currentHeading = program.optionsGroup();

console.log('Current heading:', currentHeading);
// Expected: 'Advanced Options'
// Actual: undefined
```

### Expected behavior

When `optionsGroup()` is called without arguments, it should return the currently set heading (getter behavior). When called with an argument, it should set the heading and return the Command instance for chaining (setter behavior).

### Additional context

This appears to be a regression - the method should support both getter and setter patterns like other similar methods in the API. The current behavior breaks the ability to retrieve the configured options group heading.

---
Repository: /testbed
