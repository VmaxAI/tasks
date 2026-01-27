# Bug Report

### Describe the bug
After a recent update, the `setHeader` method on the response object seems to be broken or missing. When trying to set HTTP headers in middleware, nothing happens and the headers don't get set properly.

### Reproduction
```js
const Koa = require('koa')
const app = new Koa()

app.use(async (ctx) => {
  ctx.res.setHeader('X-Custom-Header', 'test-value')
  ctx.body = 'Hello'
})

// Expected: Response should include X-Custom-Header
// Actual: Header is not set
```

### Expected behavior
The `setHeader` method should properly set response headers. The header should be accessible via `getHeader` and should be included in the HTTP response.

### System Info
- Node version: 14.x
- Koa version: latest

---
Repository: /testbed
