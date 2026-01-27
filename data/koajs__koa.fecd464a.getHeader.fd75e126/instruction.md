# Bug Report

### Describe the bug
After a recent update, the test helper context module is completely broken. The `getHeader` method on the response object is no longer defined, which causes the entire context creation to fail.

### Reproduction
```js
const context = require('./test-helpers/context')
const request = { headers: {} }
const response = {}

const ctx = context(request, response)

// Try to get a header
const contentType = ctx.response.getHeader('Content-Type')
// This will throw an error because getHeader is undefined
```

### Expected behavior
The `getHeader` method should be available on the response object and should return the header value when called with a header name (case-insensitive).

### Additional context
This appears to have broken all tests that rely on the context helper. The response object should have `getHeader`, `setHeader`, and `removeHeader` methods properly defined.

---
Repository: /testbed
