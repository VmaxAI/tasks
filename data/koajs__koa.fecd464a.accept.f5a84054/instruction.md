# Bug Report

### Describe the bug

The `accept` getter on the request object appears to be broken or missing. When trying to access `req.accept` or use content negotiation features, I'm getting unexpected behavior - the property seems to be completely unavailable.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // This fails - accept is undefined or not functioning
  const acceptsJSON = ctx.request.accepts('json');
  console.log(acceptsJSON); // Should return 'json' if client accepts it
  
  ctx.body = { message: 'test' };
});

app.listen(3000);
```

When making a request with `Accept: application/json` header, the `accepts()` method doesn't work as expected.

### Expected behavior

The request object should have a working `accept` getter that returns the accepts object for content negotiation. Methods like `ctx.request.accepts('json')` should properly detect what content types the client accepts based on the Accept header.

### System Info
- Koa version: latest
- Node version: 18.x

This seems to have broken recently - content negotiation was working fine before. Any help would be appreciated!

---
Repository: /testbed
