# Bug Report

### Describe the bug

I'm experiencing an issue with option matching where long-form options are not being recognized correctly. When I try to use the long form of a command-line option (e.g., `--verbose`), it doesn't match as expected, but the short form (e.g., `-v`) works fine.

### Reproduction

```js
const option = new Option('-v, --verbose', 'enable verbose output');

// This returns false but should return true
console.log(option.is('--verbose')); // Expected: true, Actual: false

// Short form still works
console.log(option.is('-v')); // Works correctly: true
```

### Expected behavior

Both short and long forms of an option should be matched correctly when calling `is()`. If I define an option with both `-v` and `--verbose`, then `option.is('--verbose')` should return `true`.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
