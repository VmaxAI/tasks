# Bug Report

### Describe the bug

The `accept` getter on the request object appears to be broken or missing. When trying to access content negotiation through `ctx.request.accept`, the application crashes or behaves unexpectedly.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // Trying to use accept for content negotiation
  const type = ctx.request.accept.types('json', 'html');
  ctx.body = { type };
});

app.listen(3000);
```

When making a request to this endpoint, the server fails to handle the accept header properly.

### Expected behavior

The `accept` property should return an accepts object that can be used for content negotiation. It should work like:

```js
ctx.request.accept.types('json', 'html') // should return preferred type
ctx.request.accept.charsets() // should return accepted charsets
```

### System Info
- Node version: 18.x
- Koa version: latest

This seems like a regression - content negotiation was working fine before. Any help would be appreciated!

---
Repository: /testbed
