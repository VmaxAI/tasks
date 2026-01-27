# Bug Report

### Describe the bug

The HTTP language syntax highlighting is completely broken. When trying to use the HTTP language mode, I'm getting errors and the content-type matching doesn't work at all.

### Reproduction

```js
// Try to use HTTP syntax highlighting with content types
const httpCode = `
POST /api/data HTTP/1.1
Content-Type: application/json

{"key": "value"}
`;

// Syntax highlighting fails and content type patterns aren't matched
```

### Expected behavior

The HTTP language mode should properly handle content-type matching with suffixes (like `application/json`, `application/ld+json`, etc.) and apply appropriate syntax highlighting.

### Additional context

This seems to have broken recently - the content type suffix pattern matching that was working before is now completely non-functional. The `getSuffixPattern` function that handles matching content types with suffixes appears to have been replaced with something completely unrelated.

---
Repository: /testbed
