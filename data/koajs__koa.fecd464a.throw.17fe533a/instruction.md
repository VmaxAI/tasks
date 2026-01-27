# Bug Report

### Describe the bug

The `ctx.throw()` method appears to be completely broken. When I try to use it in my Koa middleware, I get an error saying that `ctx.throw` is not a function. This is a critical issue as error handling is fundamental to any application.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // This throws: ctx.throw is not a function
  ctx.throw(400, 'Bad Request');
});

app.listen(3000);
```

When I make a request to the server, instead of getting a proper 400 error response, the application crashes with:

```
TypeError: ctx.throw is not a function
```

### Expected behavior

`ctx.throw()` should create and throw an HTTP error with the specified status code and message. This has been working fine in all previous versions.

### System Info
- Koa version: latest
- Node version: 18.x

This is blocking our deployment. Any help would be appreciated!

---
Repository: /testbed
