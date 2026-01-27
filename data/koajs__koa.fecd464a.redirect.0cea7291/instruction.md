# Bug Report

### Describe the bug

The `redirect()` method appears to be completely broken or missing. When trying to redirect requests in my Koa application, I'm getting errors that the redirect function doesn't exist or isn't working as expected.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // This should redirect to the homepage
  ctx.redirect('/');
});

app.listen(3000);
```

When I try to access any route, instead of getting redirected, the application either crashes or doesn't respond properly.

### Expected behavior

The `ctx.redirect()` method should:
1. Set the Location header to the provided URL
2. Set an appropriate redirect status code (302 by default)
3. Send a redirect response body

This was working fine before, but suddenly stopped working. I'm not sure what changed, but it seems like the redirect functionality has been completely removed or replaced with something unrelated.

### System Info
- Koa version: latest
- Node.js version: 18.x

---
Repository: /testbed
