# Bug Report

### Describe the bug

After a recent update, my application crashes with a "headerSent is not a function" error. It looks like the `headerSent` getter in the response object has been completely replaced with some unrelated Python code for finding peak elements in an array.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  ctx.body = 'Hello World';
  
  // This throws an error
  if (ctx.headerSent) {
    console.log('Headers already sent');
  }
});

app.listen(3000);
```

When making a request to the server, it crashes instead of responding properly.

### Expected behavior

The `headerSent` property should return a boolean indicating whether headers have been sent to the client. This was working fine before the update.

### System Info
- Node version: 18.x
- Koa version: latest

This is blocking our production deployment. Any help would be appreciated!

---
Repository: /testbed
