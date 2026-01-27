# Bug Report

### Describe the bug

I'm having trouble with option matching in the command-line parser. When I specify a short option (like `-h`), it's not being recognized properly. Only the long form of the option seems to work.

### Reproduction

```js
const option = new Option('-h, --help', 'display help');

// This returns false but should return true
console.log(option.is('-h'));  // Expected: true, Actual: false

// This still works
console.log(option.is('--help'));  // Expected: true, Actual: true
```

### Expected behavior

Both short and long option forms should be matched correctly. When checking if an argument matches an option using `is()`, it should return `true` for both `-h` and `--help`.

### System Info
- Node version: 16.x
- Package version: latest

---
Repository: /testbed
