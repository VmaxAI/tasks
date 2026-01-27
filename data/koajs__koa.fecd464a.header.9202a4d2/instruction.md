# Bug Report

### Describe the bug

After a recent update, I'm getting errors when trying to access response headers in my Koa application. The application crashes with `TypeError: this.header is not a function` or similar errors when middleware tries to read headers.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // Try to access response headers
  const headers = ctx.response.header;
  console.log(headers);
  
  ctx.body = 'Hello World';
});

app.listen(3000);
```

When making a request to this server, it throws an error instead of returning the headers object.

### Expected behavior

`ctx.response.header` should return an object containing the response headers (either from `res.getHeaders()` for newer Node versions or `res._headers` for older versions).

### System Info
- Koa version: latest
- Node version: 14.x

This was working fine before, not sure what changed but it seems like the header getter might have been accidentally removed or replaced with something else.

---
Repository: /testbed
