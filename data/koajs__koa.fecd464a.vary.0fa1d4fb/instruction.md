# Bug Report

### Describe the bug

The `vary()` method on the response object is completely broken and doesn't work at all. When trying to set the Vary header on responses, the application crashes or the method is not available.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // This doesn't work anymore
  ctx.vary('Accept-Encoding');
  ctx.body = 'Hello World';
});

app.listen(3000);
```

### Expected behavior

The `vary()` method should properly set the Vary HTTP header on the response. This is essential for proper caching behavior when responses vary based on request headers.

### System Info
- Node version: 18.x
- Koa version: latest

This seems to have broken in a recent update. The vary method was working fine before.

---
Repository: /testbed
