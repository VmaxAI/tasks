# Bug Report

### Describe the bug

When passing `null` to a function that accepts plugin lists, the code throws an unexpected TypeError instead of handling it gracefully. The condition check seems to be broken and doesn't properly filter out null values.

### Reproduction

```js
// This should be handled gracefully but throws an error
processor.use(null);

// Expected: null should be ignored (no-op)
// Actual: TypeError is thrown
```

### Expected behavior

Passing `null` as a plugin parameter should be treated as a no-op and not throw an error. The function should handle null/undefined values gracefully similar to how it worked before.

### System Info
- remark version: 15.0.1
- Node version: Latest

---
Repository: /testbed
