# Bug Report

### Describe the bug

The `accept` getter on the request object appears to be broken. When trying to access `req.accept` or use any of its methods like `accepts()`, the application crashes or behaves unexpectedly.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // This should work but doesn't
  const acceptsJSON = ctx.accepts('json');
  ctx.body = { accepts: acceptsJSON };
});

app.listen(3000);
```

When making a request to the server with an Accept header, the code fails to properly negotiate content types.

### Expected behavior

The `accept` property should return a proper accepts object that can be used to negotiate content types based on the request's Accept header. Methods like `ctx.accepts('json')`, `ctx.accepts('html')` should work as documented.

### System Info
- Node version: 14.x
- Koa version: latest

This seems like it might be related to a recent code change. The accept getter is critical for content negotiation in APIs.

---
Repository: /testbed
