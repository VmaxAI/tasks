# Bug Report

### Describe the bug

The `origin` property on the request object is broken and returns `undefined` instead of the expected origin header value. This appears to be causing issues when trying to handle CORS requests or any logic that depends on checking the request origin.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  console.log(ctx.request.origin); // Should print the origin header
  ctx.body = { origin: ctx.request.origin };
});

app.listen(3000);
```

When making a request with an `Origin` header:
```bash
curl -H "Origin: https://example.com" http://localhost:3000
```

### Expected behavior

The `ctx.request.origin` should return `'https://example.com'` (or `null` if no origin header is present), but instead it's returning `undefined`.

### System Info
- Node version: 16.x
- Koa version: latest

This is breaking our CORS middleware that relies on checking the request origin. Any help would be appreciated!

---
Repository: /testbed
