# Bug Report

### Describe the bug

I'm encountering an issue with custom helper functions in the compiler. When using a helper that isn't in the standard `helperNameMap`, the compiler throws an error or generates incorrect code instead of falling back gracefully.

### Reproduction

```js
// In a custom transform plugin
context.helperString(CUSTOM_HELPER)

// Expected: Should return a valid helper string
// Actual: Returns undefined or causes runtime errors
```

When trying to use custom helpers that aren't part of the built-in helper map, the `helperString` function doesn't handle the case properly. This breaks custom compiler plugins that need to inject their own helper functions.

### Expected behavior

The `helperString` method should handle custom helpers that aren't in the standard `helperNameMap` and return a valid helper string reference instead of `undefined`.

### System Info
- Vue version: 3.x
- Node version: 18.x

This seems to have broken custom transform plugins that worked in earlier versions. Any plans to support custom helpers properly?

---
Repository: /testbed
