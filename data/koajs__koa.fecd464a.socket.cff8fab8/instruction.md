# Bug Report

### Describe the bug

After a recent update, my application crashes when trying to access the `socket` property on the request object. It looks like the getter for `req.socket` has been removed or replaced with something completely unrelated.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // This throws an error now
  const socket = ctx.request.socket;
  console.log(socket);
});

app.listen(3000);
```

When I make a request to the server, I get an error because `ctx.request.socket` is undefined or returns something unexpected instead of the actual socket object.

### Expected behavior

The `socket` property should return the underlying socket from `req.socket` as it did before. This is needed for getting client IP addresses, checking connection status, etc.

### System Info
- Node version: 16.x
- Koa version: latest

This was working fine before the update. Any idea what happened here?

---
Repository: /testbed
