# Bug Report

### Describe the bug
The `charset` getter on request objects is completely broken. When trying to access `req.charset`, the application crashes or returns undefined instead of returning the charset from the Content-Type header.

### Reproduction
```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // Try to access charset
  console.log(ctx.request.charset);
  // Expected: 'utf-8' or '' if not present
  // Actual: undefined or crashes
  
  ctx.body = 'Hello';
});

// Send a request with Content-Type: text/html; charset=utf-8
// The charset property doesn't work
```

### Expected behavior
The `charset` getter should parse the Content-Type header and return the charset parameter if present, or an empty string if not present. For example, with `Content-Type: text/html; charset=utf-8`, it should return `'utf-8'`.

### Additional context
This was working fine before, but now accessing the charset property doesn't behave as expected. It seems like the getter implementation might have been accidentally modified or removed.

---
Repository: /testbed
