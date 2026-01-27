# Bug Report

### Describe the bug

The `protocol` getter on the request object appears to be broken or missing. When trying to access `req.protocol` in my application, I'm getting unexpected behavior - it seems like the property is no longer returning the expected protocol string ('http' or 'https').

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  console.log('Protocol:', ctx.request.protocol);
  // Expected: 'http' or 'https'
  // Actual: undefined or error
  ctx.body = { protocol: ctx.request.protocol };
});

app.listen(3000);
```

When making a request to the server, `ctx.request.protocol` doesn't return the protocol string as expected.

### Expected behavior

`req.protocol` should return:
- `'https'` when the connection is encrypted
- `'https'` when behind a proxy with `X-Forwarded-Proto: https` header (if `app.proxy` is enabled)
- `'http'` otherwise

This was working fine in previous versions and is documented in the API docs.

### System Info
- Koa version: latest
- Node.js version: 18.x

---
Repository: /testbed
