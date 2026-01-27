# Bug Report

### Describe the bug

After a recent update, the `redirect()` method on the response object has completely stopped working. When calling `ctx.redirect(url)` in my routes, I'm getting errors that `redirect is not a function`.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // This throws: ctx.redirect is not a function
  ctx.redirect('/new-path');
});

app.listen(3000);
```

Trying to redirect to an external URL also fails:
```js
app.use(async (ctx) => {
  ctx.redirect('https://example.com');
});
```

### Expected behavior

The redirect method should work as documented and set the appropriate Location header and response body. The response should redirect the user to the specified URL.

### System Info
- Node version: 18.x
- Koa version: latest

This is blocking our application from working properly since we rely heavily on redirects for authentication flows and route handling. Any help would be appreciated!

---
Repository: /testbed
