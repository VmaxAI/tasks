# Bug Report

### Describe the bug

The `accepts()` method on the request object is completely broken and not working at all. When trying to use `req.accepts()` to check content negotiation, I'm getting errors that the method doesn't exist or isn't a function.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // This fails - accepts is not a function
  const type = ctx.request.accepts('json', 'html');
  
  if (type === 'json') {
    ctx.body = { data: 'json response' };
  } else {
    ctx.body = '<html>html response</html>';
  }
});

app.listen(3000);
```

When making a request with `Accept: application/json` header, the server crashes instead of properly negotiating the content type.

### Expected behavior

The `accepts()` method should work normally and return the best match from the provided types based on the Accept header. This is a core feature for content negotiation and was working fine before.

### System Info
- Node version: 16.x
- Koa version: latest

This seems like a pretty critical regression since accepts() is used in a lot of middleware for content negotiation. Any help would be appreciated!

---
Repository: /testbed
