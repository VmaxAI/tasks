# Bug Report

### Describe the bug

The `hideHelp()` method on Option objects is not working as expected. When I call `hideHelp(true)` to hide an option from the help output, the option still appears. Similarly, calling `hideHelp(false)` causes the option to be hidden when it should be visible.

### Reproduction

```js
const option = new Option('-d, --debug', 'enable debug mode');

// This should hide the option, but it remains visible
option.hideHelp(true);

// This should show the option, but it gets hidden
option.hideHelp(false);
```

### Expected behavior

- `option.hideHelp(true)` should hide the option from help text
- `option.hideHelp(false)` should make the option visible in help text
- The method should return the Option instance for chaining (as it did before)

### Additional context

This seems to have broken recently. The behavior is completely inverted from what it should be, and the return value has also changed which breaks method chaining.

---
Repository: /testbed
