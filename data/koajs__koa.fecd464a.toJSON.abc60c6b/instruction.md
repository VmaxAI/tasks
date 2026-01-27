# Bug Report

### Describe the bug

The `toJSON()` method on the request object appears to be completely broken. When trying to serialize a request to JSON (for logging or debugging purposes), I'm getting unexpected errors or the method just doesn't exist.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // Try to serialize the request
  const requestJson = ctx.request.toJSON();
  console.log(requestJson);
  
  ctx.body = 'Hello';
});
```

When running this code, the `toJSON()` method either throws an error or returns something completely unexpected instead of the request details (method, url, header).

### Expected behavior

The `toJSON()` method should return an object containing the request's method, url, and header properties, which can be used for logging or debugging purposes.

Expected output:
```js
{
  method: 'GET',
  url: '/some-path',
  header: { /* request headers */ }
}
```

### System Info
- Koa version: latest
- Node version: 18.x

This seems like it might have been accidentally broken in a recent commit. The method was working fine before.

---
Repository: /testbed
