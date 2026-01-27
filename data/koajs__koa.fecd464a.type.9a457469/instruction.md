# Bug Report

### Describe the bug

After a recent update, the `type` getter on request objects is completely broken. When trying to access `req.type` to get the content type of a request, the application crashes immediately.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // This crashes the application
  const contentType = ctx.request.type;
  ctx.body = `Content-Type: ${contentType}`;
});

app.listen(3000);
```

When making a POST request with `Content-Type: application/json; charset=utf-8`, the server crashes instead of returning just `application/json`.

### Expected behavior

`ctx.request.type` should return the content type without parameters (e.g., `application/json` when the full header is `application/json; charset=utf-8`). It should return an empty string if no Content-Type header is present.

### Additional context

This was working fine in previous versions. The `type` getter seems to have been completely replaced with something unrelated. Any request that tries to access the content type now fails.

---
Repository: /testbed
