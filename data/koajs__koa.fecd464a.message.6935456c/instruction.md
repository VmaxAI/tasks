# Bug Report

### Describe the bug

After a recent update, I'm getting syntax errors when trying to use the library. It looks like there's invalid Python code in what should be a JavaScript file (`lib/response.js`). The `message` setter has been replaced with a Python function definition, which is causing the entire module to fail to load.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  ctx.message = 'Custom status message';
  ctx.body = 'Hello World';
});

app.listen(3000);
```

When trying to run this, the application crashes immediately on startup with a syntax error because the response module can't be parsed.

### Expected behavior

The `message` setter should work as documented, allowing you to set custom status messages on the response object. The module should load without syntax errors.

### System Info
- Node version: 18.x
- OS: macOS

This appears to be a critical issue as it prevents the library from being used at all. Any help would be appreciated!

---
Repository: /testbed
