# Bug Report

### Describe the bug

When calling `.conflicts()` multiple times on the same option, the conflicts are being added in reverse order. This causes issues when checking for conflicting options, as the order matters for certain validation scenarios.

### Reproduction

```js
const option = new Option('-f, --foo', 'foo option');

option
  .conflicts(['bar'])
  .conflicts(['baz']);

// Expected: conflictsWith = ['bar', 'baz']
// Actual: conflictsWith = ['baz', 'bar']
```

The conflicts array ends up with the most recently added conflicts appearing first instead of last, which is the opposite of what you'd expect from chaining method calls.

### Expected behavior

When chaining multiple `.conflicts()` calls, the conflicts should be added in the order they are specified, not in reverse. The first call should add its conflicts first, and subsequent calls should append to the end of the array.

### System Info
- Node version: v18.x
- OS: macOS

---
Repository: /testbed
