# Bug Report

### Describe the bug

After a recent update, the test helper context creation is broken. When trying to use `context()` to create a test context, getting errors about `res.getHeader` not being defined or not being a function.

### Reproduction

```js
const context = require('./test-helpers/context')
const Koa = require('koa')

const app = new Koa()
const ctx = context({ url: '/' }, {}, app)

// Trying to access response headers fails
const contentType = ctx.res.getHeader('content-type')
// TypeError: res.getHeader is not a function
```

### Expected behavior

The `res.getHeader` method should be available on the response object and should return the header value when called with a header name.

### System Info
- Node version: 14.x
- Koa version: 2.x

This seems to have broken after the latest changes to the context helper. The response object is missing the `getHeader` method which is needed for header retrieval in tests.

---
Repository: /testbed
