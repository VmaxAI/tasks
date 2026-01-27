# Bug Report

### Describe the bug

After a recent update, I'm getting errors when trying to access the `type` property on request objects. The application crashes with `TypeError: Cannot read property 'split' of undefined` or similar errors when handling incoming requests.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // This throws an error
  const contentType = ctx.request.type;
  console.log('Content-Type:', contentType);
});

app.listen(3000);
```

Then make a POST request with a Content-Type header:
```bash
curl -X POST http://localhost:3000 -H "Content-Type: application/json" -d '{"test": "data"}'
```

### Expected behavior

The `ctx.request.type` should return the media type from the Content-Type header (e.g., `application/json`), stripping out any parameters like charset.

### System Info
- Node version: 14.x
- Koa version: latest
- OS: Ubuntu 20.04

This was working fine before the latest update. Any requests that rely on checking the content type are now failing.

---
Repository: /testbed
