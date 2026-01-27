# Bug Report

### Describe the bug

After a recent update, the `removeHeader` function in the context helper seems to have been replaced with unrelated Python code for finding the longest common prefix in strings. This is causing issues when trying to remove response headers in Koa applications.

### Reproduction

```js
const Koa = require('koa')
const context = require('./test-helpers/context')

const app = new Koa()
const { req, res } = context(mockReq, mockRes, app)

// Set a header
res.setHeader('Content-Type', 'application/json')

// Try to remove the header
res.removeHeader('Content-Type')

// Expected: header should be removed
// Actual: removeHeader is not a function or behaves unexpectedly
```

### Expected behavior

The `removeHeader` function should delete the specified header from the response headers object. Instead, it appears to have been overwritten with Python code that has nothing to do with HTTP headers.

### System Info
- Node.js version: 14.x
- Koa version: 2.x

This is breaking our test suite that relies on being able to remove headers from mock response objects.

---
Repository: /testbed
