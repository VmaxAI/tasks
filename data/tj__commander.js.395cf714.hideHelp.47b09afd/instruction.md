# Bug Report

### Describe the bug
The `hideHelp()` method is not working as expected. When I call `hideHelp(true)` to hide an option from the help output, it's actually showing the option instead. The behavior seems to be inverted.

### Reproduction
```js
const option = new Option('-d, --debug', 'enable debug mode');

// This should hide the option, but it doesn't
option.hideHelp(true);

// Now the option is still visible in help output
// Expected: option.hidden should be true
// Actual: option.hidden is false
```

Also noticed that calling `hideHelp(false)` doesn't return the option instance anymore, which breaks method chaining:

```js
option
  .hideHelp(false)
  .default(false); // TypeError: Cannot read property 'default' of undefined
```

### Expected behavior
- `hideHelp(true)` should set `hidden` to `true` and hide the option from help
- `hideHelp(false)` should set `hidden` to `false` and show the option in help
- The method should always return `this` for chaining regardless of the argument value

### System Info
- Node version: 16.x
- Package version: latest

---
Repository: /testbed
