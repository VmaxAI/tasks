# Bug Report

### Describe the bug

When using variadic options with default values, the order of values is reversed. New values are being prepended to the array instead of appended, which breaks the expected left-to-right ordering of command-line arguments.

### Reproduction

```js
const program = new Command();
program
  .option('-n, --number <value...>', 'numbers', [1, 2, 3])
  .parse(['node', 'test', '-n', '4', '-n', '5']);

console.log(program.opts().number);
// Expected: [1, 2, 3, 4, 5]
// Actual: [5, 4, 1, 2, 3]
```

The values are appearing in reverse order - the most recently specified values appear first in the array, followed by the default values. This is counterintuitive since command-line arguments are typically processed left-to-right.

### Expected behavior

Values should be concatenated in the order they appear on the command line, with defaults appearing first and new values appended in sequence.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
