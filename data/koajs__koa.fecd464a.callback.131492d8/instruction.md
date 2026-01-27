# Bug Report

### Describe the bug

The application crashes immediately when trying to start the server. After updating to the latest version, calling `app.callback()` results in a syntax error. The server won't start at all and throws an error about unexpected syntax.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  ctx.body = 'Hello World';
});

// This throws an error
app.listen(3000);
```

When running this basic setup, the application fails to start. It looks like there's something wrong with the callback method that gets invoked when the server starts listening.

### Expected behavior

The server should start normally and handle requests. This exact same code worked fine in the previous version.

### System Info
- Node.js version: 18.x
- Koa version: latest
- OS: Ubuntu 22.04

---
Repository: /testbed
