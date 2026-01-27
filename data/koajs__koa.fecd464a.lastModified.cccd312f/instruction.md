# Bug Report

### Describe the bug

The `lastModified` setter on response objects appears to be broken. When trying to set the Last-Modified header using `response.lastModified = <value>`, the application crashes or the header is not set correctly.

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

When making a request to the server, the Last-Modified header is not being set and the response behavior is unexpected.

### Expected behavior

The `lastModified` setter should accept either a Date object or a string, convert it to the proper UTC format, and set the Last-Modified response header accordingly.

### Additional context

This was working fine in previous versions. The setter should handle both string dates and Date objects:

```js
ctx.response.lastModified = 'Wed, 13 Jul 2011 08:20:09 GMT';
// or
ctx.response.lastModified = new Date();
```

Both should properly set the Last-Modified header in the response.

---
Repository: /testbed
