# Bug Report

### Describe the bug

The `protocol` getter appears to have been completely replaced with unrelated Python code for binary string conversion. When trying to access `request.protocol` in my application, I'm getting unexpected behavior - the property seems to be undefined or not working as expected.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  console.log(ctx.request.protocol); // Should return 'http' or 'https'
  ctx.body = `Protocol: ${ctx.request.protocol}`;
});

app.listen(3000);
```

When accessing the server, the protocol property doesn't return the expected 'http' or 'https' string. This breaks any middleware or code that relies on detecting the request protocol.

### Expected behavior

`ctx.request.protocol` should return:
- `'https'` when the socket is encrypted
- The value from `X-Forwarded-Proto` header when proxy is enabled
- `'http'` as the default fallback

### System Info
- Node version: 18.x
- Koa version: latest

This seems to have broken after a recent update. The protocol detection is critical for handling secure cookies and redirect logic in our application.

---
Repository: /testbed
