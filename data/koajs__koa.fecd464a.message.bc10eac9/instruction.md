# Bug Report

### Describe the bug

After a recent update, the response message property is completely broken. When trying to access `res.message` or any status message from the response object, I'm getting errors about undefined properties or the application just crashes.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  ctx.status = 404;
  console.log(ctx.message); // This should work but doesn't
  ctx.body = 'Hello World';
});

app.listen(3000);
```

When I make a request to the server, it fails to retrieve the status message. The `message` getter seems to be missing or broken.

### Expected behavior

The `ctx.message` property should return the appropriate status message for the current status code (e.g., "Not Found" for 404, "OK" for 200, etc.). This was working fine in previous versions.

### System Info
- Node.js version: 18.x
- Koa version: latest

This is blocking our production deployment. Any help would be appreciated!

---
Repository: /testbed
