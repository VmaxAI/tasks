# Bug Report

### Describe the bug
After a recent update, the `lastModified` setter on the response object appears to be broken or missing. When trying to set the Last-Modified header using the property setter, the application crashes or the header is not set properly.

### Reproduction
```js
const Koa = require('koa');
const app = new Koa();

app.use(ctx => {
  // This should set the Last-Modified header
  ctx.response.lastModified = new Date();
  ctx.body = 'Hello World';
});

app.listen(3000);
```

When making a request to the server, the Last-Modified header is not being set and the response behaves unexpectedly.

### Expected behavior
The `lastModified` setter should accept either a Date object or a string, convert it to the proper format, and set the Last-Modified HTTP header on the response.

### Additional context
This was working fine in previous versions. The setter should handle both Date objects and date strings, automatically converting them to UTC string format for the header.

---
Repository: /testbed
