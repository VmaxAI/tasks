# Bug Report

### Describe the bug

The `accepts()` method on the request object appears to be completely broken. When trying to use content negotiation in my application, I'm getting errors that `this.accepts` is not a function.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // This throws an error
  const type = ctx.accepts('json', 'html');
  
  if (type === 'json') {
    ctx.body = { data: 'test' };
  } else {
    ctx.body = '<html>test</html>';
  }
});

app.listen(3000);
```

When making a request with `Accept: application/json` header, the server crashes instead of returning JSON.

### Expected behavior

The `accepts()` method should work for content negotiation, allowing the application to determine the preferred response format based on the Accept header.

### System Info
- Node version: 18.x
- Koa version: latest

This was working fine before, not sure what happened. Any help would be appreciated!

---
Repository: /testbed
