# Bug Report

### Describe the bug

After a recent update, the application crashes on startup with a syntax error. The server fails to initialize and throws an error about unexpected token/syntax when trying to create the context for incoming requests.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  ctx.body = 'Hello World';
});

app.listen(3000);
```

When trying to start the server, it immediately fails with a syntax error. The application worked fine before the latest changes.

### Expected behavior

The server should start normally and handle requests without any syntax errors. The `createContext` method should properly initialize the context object with request and response properties.

### System Info
- Node version: 14.x
- Koa version: latest
- OS: macOS

This is blocking deployment to production. Any help would be appreciated!

---
Repository: /testbed
