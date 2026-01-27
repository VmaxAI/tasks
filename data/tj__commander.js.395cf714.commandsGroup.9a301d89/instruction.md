# Bug Report

### Describe the bug

The `commandsGroup()` method is not working correctly when trying to set a custom group heading for commands. When I call `commandsGroup('My Commands')` to set a heading, it returns the heading string instead of the Command instance, breaking method chaining.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

// This should allow method chaining but returns a string instead
const result = program
  .commandsGroup('Custom Commands')
  .version('1.0.0');  // TypeError: Cannot read property 'version' of undefined

console.log(typeof result);  // Expected: 'object', Actual: 'string'
```

Also, when trying to retrieve the current commands group heading:

```js
const program = new Command();
program.commandsGroup('My Group');

// This should return the heading but returns the Command instance
const heading = program.commandsGroup();
console.log(heading);  // Expected: 'My Group', Actual: Command instance
```

### Expected behavior

- When setting a commands group heading with `commandsGroup('heading')`, it should return the Command instance to allow method chaining
- When getting the commands group heading with `commandsGroup()` (no arguments), it should return the current heading string

The getter and setter behaviors seem to be swapped.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
