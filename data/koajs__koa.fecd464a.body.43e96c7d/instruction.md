# Bug Report

### Describe the bug

The response body getter appears to be completely broken - when trying to access `res.body`, I'm getting undefined or errors instead of the actual response body content. This seems to have happened suddenly and is breaking my entire application.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  ctx.body = 'Hello World';
  console.log(ctx.response.body); // Should print 'Hello World'
});

app.listen(3000);
```

When I make a request to the server, the body getter doesn't return the value that was set. The response is completely empty or throws an error.

### Expected behavior

`ctx.response.body` should return the value that was previously assigned to `ctx.body`. The getter should work properly and return the stored body content.

### System Info
- Node version: 18.x
- Koa version: latest

This is blocking production deployment, any help would be appreciated!

---
Repository: /testbed
