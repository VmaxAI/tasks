# Bug Report

### Describe the bug

The `hideHelp()` method is not working correctly when called with `false` to show the help text. When I try to unhide an option that was previously hidden, the method doesn't return the Option instance, which breaks method chaining.

### Reproduction

```js
const option = new Option('-d, --debug', 'enable debug mode');

// Hide the option
option.hideHelp(true);  // works fine, returns option instance

// Try to unhide it later
const result = option.hideHelp(false);  // returns undefined instead of option instance

// This breaks chaining
option.hideHelp(false).default(true);  // TypeError: Cannot read property 'default' of undefined
```

### Expected behavior

The `hideHelp()` method should always return the Option instance to maintain chainability, regardless of whether the argument is `true` or `false`.

### System Info
- Node version: 18.x
- Package version: latest

---
Repository: /testbed
