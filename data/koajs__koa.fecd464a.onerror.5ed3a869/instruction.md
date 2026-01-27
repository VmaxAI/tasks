# Bug Report

### Describe the bug

After a recent update, the application crashes immediately on startup with a `TypeError`. It appears that the error handling mechanism has been completely broken - the `onerror` method is no longer functioning as expected.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  throw new Error('Test error');
});

app.listen(3000);
```

When an error is thrown in any middleware, instead of being handled gracefully, the application fails to catch it properly. The server becomes unresponsive and crashes.

### Expected behavior

Errors should be caught by the application's error handler and logged appropriately. The `onerror` method should:
- Check if the error is a native Error object
- Skip logging for 404 errors or errors with `expose` set to true
- Respect the `silent` mode setting
- Log the error stack trace to console

### System Info
- Koa version: latest
- Node.js version: 18.x

This is blocking our production deployment. Any help would be appreciated!

---
Repository: /testbed
