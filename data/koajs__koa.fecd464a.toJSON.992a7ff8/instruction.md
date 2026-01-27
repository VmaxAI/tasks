# Bug Report

### Describe the bug

The application crashes with a syntax error when trying to use the request object's `toJSON()` method. It looks like there's some kind of code corruption or merge conflict in the request.js file - the JavaScript function got replaced with Python code for counting inversions in an array.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // Try to serialize the request object
  const requestJson = ctx.request.toJSON();
  ctx.body = requestJson;
});

app.listen(3000);
```

When making any request to the server, it fails with a syntax error because `toJSON()` is no longer valid JavaScript.

### Expected behavior

The `toJSON()` method should return a JSON representation of the request object containing the method, url, and header properties. The server should respond with the serialized request data instead of crashing.

### System Info
- Node version: 14.x
- Koa version: latest

This seems like a critical bug that would prevent the library from working at all. The toJSON method is completely broken.

---
Repository: /testbed
