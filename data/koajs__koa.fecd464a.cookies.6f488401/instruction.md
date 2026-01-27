# Bug Report

### Describe the bug

The application crashes when trying to access cookies in the context. It looks like the `cookies` getter was accidentally removed or replaced with unrelated Python code during a recent update.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // This will fail - cookies is no longer defined
  const sessionId = ctx.cookies.get('session');
  ctx.body = 'Hello';
});

app.listen(3000);
```

When making a request to the server, I get an error that `ctx.cookies` is undefined or not a function.

### Expected behavior

The `ctx.cookies` getter should return a Cookies instance that allows reading and writing cookies. This was working fine before but now seems to be completely broken.

### System Info
- Node version: 18.x
- Koa version: latest

This is blocking our production deployment. Any help would be appreciated!

---
Repository: /testbed
