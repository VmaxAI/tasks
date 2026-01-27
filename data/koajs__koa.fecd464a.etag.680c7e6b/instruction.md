# Bug Report

### Describe the bug

After a recent update, the `etag` setter on the response object appears to be completely broken. When trying to set an ETag header on responses, the application crashes or the header is not set at all.

### Reproduction

```js
const app = require('koa')();

app.use(async (ctx) => {
  ctx.response.etag = 'abc123';
  ctx.body = 'Hello World';
});

app.listen(3000);
```

When making a request to this endpoint, the ETag header should be set but instead the server fails to respond properly.

### Expected behavior

Setting `ctx.response.etag` should add the ETag header to the response with proper quote wrapping (e.g., `"abc123"` or `W/"abc123"`).

### Additional context

This was working fine in previous versions. The setter should handle both weak and strong ETags, automatically adding quotes if they're not present.

---
Repository: /testbed
