# Bug Report

### Describe the bug

I'm experiencing an issue where option flags are being assigned to the wrong properties. When defining command options with both short and long flags, they seem to be swapped - the short flag gets assigned to the `long` property and vice versa.

### Reproduction

```js
const option = new Option('-v, --verbose', 'enable verbose mode');

// Expected:
// option.short === '-v'
// option.long === '--verbose'

// Actual:
// option.short === '--verbose'
// option.long === '-v'
```

This causes commands to not recognize the flags correctly when parsing arguments.

### Expected behavior

The `short` property should contain the short flag (e.g., `-v`) and the `long` property should contain the long flag (e.g., `--verbose`). The flags should be correctly assigned based on their format, not swapped.

### Additional context

Also noticed that when using `.choices()` on an option, the validation seems to check the wrong value. It appears to be validating against the previous value instead of the current argument being parsed, which allows invalid choices to pass through.

---
Repository: /testbed
