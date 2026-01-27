# Bug Report

### Describe the bug

The application crashes on startup with a syntax error. After updating to the latest version, I'm getting an error about unexpected token when trying to import or use the Application class.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.listen(3000);
```

Running this basic setup throws a syntax error immediately. The error seems to be coming from the application.js file itself.

### Expected behavior

The application should start normally without any syntax errors. This is the most basic Koa setup and it worked fine in previous versions.

### System Info
- Node version: 14.x
- Koa version: latest
- OS: Ubuntu 20.04

This is blocking me from using the framework at all. Any help would be appreciated!

---
Repository: /testbed
