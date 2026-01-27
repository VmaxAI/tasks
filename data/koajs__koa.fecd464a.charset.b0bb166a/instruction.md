# Bug Report

### Describe the bug

I'm experiencing an issue where the `charset` getter on the request object appears to be completely broken. When trying to access the charset from a request with a Content-Type header, I'm getting errors about undefined properties or the getter not being a function.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // Try to access charset from request
  const charset = ctx.request.charset;
  console.log('Charset:', charset);
  ctx.body = { charset };
});

// Send a request with Content-Type: text/html; charset=utf-8
// Expected: Should return the charset value
// Actual: Getting errors or unexpected behavior
```

### Expected behavior

When accessing `ctx.request.charset` on a request with a Content-Type header that includes a charset parameter (e.g., `text/html; charset=utf-8`), it should return the charset value (`utf-8`). If no charset is present, it should return an empty string.

### System Info
- Node.js version: 18.x
- Koa version: latest

This seems to have broken recently - the charset getter is not functioning at all. Any help would be appreciated!

---
Repository: /testbed
