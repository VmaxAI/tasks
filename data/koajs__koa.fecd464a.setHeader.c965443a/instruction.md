# Bug Report

### Describe the bug

I'm experiencing an issue where `setHeader` is not working at all in my Koa application. When I try to set response headers, nothing happens and the headers are not being set on the response object.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  ctx.set('Content-Type', 'application/json');
  ctx.set('X-Custom-Header', 'test-value');
  
  // Headers are not being set properly
  console.log(ctx.response.headers); // Expected headers are missing
  
  ctx.body = { message: 'Hello' };
});

app.listen(3000);
```

### Expected behavior

Headers should be set correctly on the response object when using `ctx.set()` or when setting headers directly. The response should include the specified headers.

### Additional context

This seems to have broken recently. Previously headers were working fine but now they're completely missing from responses. The application runs without errors but the headers just don't get applied.

---
Repository: /testbed
