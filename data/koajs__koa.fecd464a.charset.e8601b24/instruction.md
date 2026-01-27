# Bug Report

### Describe the bug

After a recent update, the `charset` getter on the request object is completely broken. When trying to access `req.charset`, I'm getting errors about undefined properties or the application just crashes.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // This should return the charset from Content-Type header
  const charset = ctx.request.charset;
  console.log('Charset:', charset);
  ctx.body = { charset };
});

app.listen(3000);
```

When I send a request with a Content-Type header like `text/plain; charset=utf-8`, the application crashes instead of returning the charset value.

### Expected behavior

The `charset` property should parse the Content-Type header and return the charset parameter (e.g., 'utf-8'), or an empty string if no charset is specified. This was working fine in previous versions.

### System Info
- Koa version: latest
- Node version: 18.x

This seems like a pretty critical regression since charset parsing is a common operation when handling requests with different encodings.

---
Repository: /testbed
