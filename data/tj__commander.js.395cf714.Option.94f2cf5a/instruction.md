# Bug Report

### Describe the bug

I'm having an issue with the `conflicts()` method on options. When I call `.conflicts()` multiple times on the same option, only the last set of conflicting options is retained instead of accumulating all of them.

### Reproduction

```js
const option = new Option('-f, --foo', 'foo option');

option
  .conflicts(['bar', 'baz'])
  .conflicts(['qux']);

// Expected: conflictsWith should contain ['bar', 'baz', 'qux']
// Actual: conflictsWith only contains ['qux']
```

When chaining multiple `.conflicts()` calls, I would expect all the conflicting option names to be accumulated, but instead each call seems to overwrite the previous ones.

### Expected behavior

Multiple calls to `.conflicts()` should accumulate the conflicting option names, not replace them. This would be consistent with how similar chainable methods typically work.

### System Info
- Node version: 18.x
- OS: macOS

---
Repository: /testbed
