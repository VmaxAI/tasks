# Bug Report

### Describe the bug

After a recent update, the `type` getter on the request object is completely broken. When trying to access `request.type` to get the Content-Type of an incoming request, I'm getting errors about undefined functions.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // This used to work fine
  console.log(ctx.request.type);
  ctx.body = 'Hello';
});

app.listen(3000);
```

When making a POST request with `Content-Type: application/json; charset=utf-8`, the server crashes instead of returning `application/json`.

### Expected behavior

The `request.type` property should return the media type portion of the Content-Type header (without parameters like charset). For example:
- `Content-Type: application/json; charset=utf-8` should return `application/json`
- `Content-Type: text/html` should return `text/html`
- No Content-Type header should return an empty string

### System Info
- Node.js version: 16.x
- Koa version: latest

This is breaking my application in production. Any help would be appreciated!

---
Repository: /testbed
