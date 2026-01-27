# Bug Report

### Describe the bug

After a recent update, the application crashes immediately on startup. The server won't start and throws a syntax error related to the protocol getter in the request module.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // Just trying to access the protocol causes the crash
  console.log(ctx.request.protocol);
  ctx.body = 'Hello World';
});

app.listen(3000);
```

When I try to run this, the server fails to start. It looks like there's something wrong with the request.js file - the code doesn't seem to be valid JavaScript anymore.

### Expected behavior

The server should start normally and `ctx.request.protocol` should return either 'http' or 'https' depending on the connection type and proxy settings.

### System Info
- Node version: 16.x
- Koa version: latest

This was working fine before the latest changes. Can someone take a look at the request module?

---
Repository: /testbed
