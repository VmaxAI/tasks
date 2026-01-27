# Bug Report

### Describe the bug
After a recent update, the `origin` property on request objects is no longer accessible. When trying to access `ctx.request.origin` or `req.origin`, I'm getting `undefined` instead of the expected origin header value.

### Reproduction
```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  console.log(ctx.request.origin); // Returns undefined
  console.log(ctx.origin); // Also undefined
  
  ctx.body = {
    origin: ctx.request.origin
  };
});

app.listen(3000);
```

When making a request with an Origin header:
```bash
curl -H "Origin: https://example.com" http://localhost:3000
```

Expected response:
```json
{"origin": "https://example.com"}
```

Actual response:
```json
{"origin": null}
```

### Expected behavior
The `origin` getter should return the value of the `Origin` header from the request, or `null` if the header is not present. This was working fine in previous versions.

### System Info
- Node version: v18.x
- Koa version: Latest
- OS: Linux

This is breaking CORS handling in my application. Any help would be appreciated!

---
Repository: /testbed
