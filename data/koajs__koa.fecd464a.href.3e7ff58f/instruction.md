# Bug Report

### Describe the bug

After a recent update, the `href` getter on the request object is completely broken. When trying to access `ctx.request.href` or `req.href`, I'm getting undefined or the application crashes entirely.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // This used to work but now returns undefined or crashes
  console.log(ctx.request.href);
  ctx.body = 'Hello World';
});

app.listen(3000);
```

When making a request to `http://localhost:3000/test`, the `href` property is no longer accessible.

### Expected behavior

The `href` getter should return the full URL of the request. For example:
- For `GET http://localhost:3000/test` it should return `http://localhost:3000/test`
- For `GET http://example.com/foo` (proxy requests) it should return `http://example.com/foo`

This was working fine before and is breaking our application that relies on getting the full request URL.

### System Info
- Node version: 14.x
- Koa version: latest

---
Repository: /testbed
