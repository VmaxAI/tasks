# Bug Report

### Describe the bug

I'm having an issue with command-line option matching. When I define an option with both short and long forms (like `-v` and `--verbose`), the option is not being recognized properly when I try to use either form.

### Reproduction

```js
const option = new Option('-v, --verbose', 'enable verbose output');

// This doesn't work as expected
console.log(option.is('-v'));      // Should be true
console.log(option.is('--verbose')); // Should be true
```

When I try to use the short form `-v`, it's not matching correctly. Same issue with the long form `--verbose`. It seems like the option matching logic is broken.

### Expected behavior

Both the short and long forms of an option should be recognized when checking if an argument matches the option. If I define an option as `-v, --verbose`, then both `option.is('-v')` and `option.is('--verbose')` should return `true`.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
