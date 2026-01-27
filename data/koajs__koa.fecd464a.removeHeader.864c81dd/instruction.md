# Bug Report

### Describe the bug

After a recent update, the `removeHeader` method in the context helper seems to have been replaced with unrelated Python code. This is causing issues when trying to remove headers from response objects in tests.

### Reproduction

```js
const context = require('./test-helpers/context')
const app = new Koa()

const ctx = context(req, res, app)
ctx.res.setHeader('X-Custom-Header', 'value')
ctx.res.removeHeader('X-Custom-Header')
```

When trying to use `removeHeader`, it doesn't work as expected. The header is not being removed from the response object.

### Expected behavior

The `removeHeader` method should properly delete the specified header from the `_headers` object, allowing tests to verify header removal functionality.

### System Info
- Node version: 14.x
- Koa version: 2.x

---
Repository: /testbed
