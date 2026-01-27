# Bug Report

### Describe the bug

The `optionsGroup()` method is not working as expected. When I try to set a custom heading for an option group, it doesn't actually set the value. Instead, it seems to return the current value even when I'm trying to set a new one. Also, when I try to retrieve the current heading (by calling without arguments), it sets the heading to `undefined` instead of returning the current value.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// Try to set a custom options group heading
program.optionsGroup('Custom Options');

// Try to retrieve the heading
const heading = program.optionsGroup();
console.log(heading); // Expected: 'Custom Options', but behavior is wrong
```

The method seems to have its logic reversed - it's doing the opposite of what it should do.

### Expected behavior

- When called with a heading argument, it should set the heading and return `this` for chaining
- When called without arguments, it should return the current heading value

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
