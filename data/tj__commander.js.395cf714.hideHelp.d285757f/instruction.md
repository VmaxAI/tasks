# Bug Report

### Describe the bug

The `hideHelp()` method on Option objects is not working as expected. When I call `hideHelp(true)` to hide an option from the help output, it actually shows the option instead. The behavior seems to be inverted.

### Reproduction

```js
const { Option } = require('commander');

const option = new Option('-d, --debug', 'enable debug mode');

// Try to hide the option from help
option.hideHelp(true);

// Expected: option.hidden should be true
// Actual: option.hidden is false
console.log(option.hidden); // prints false instead of true
```

Also, when trying to chain methods after `hideHelp()`, I'm getting errors because it's not returning the Option instance anymore.

```js
option
  .hideHelp(true)
  .default(false); // TypeError: Cannot read property 'default' of undefined
```

### Expected behavior

- `hideHelp(true)` should set `hidden` to `true`
- `hideHelp(false)` should set `hidden` to `false`
- The method should return the Option instance to allow method chaining

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
