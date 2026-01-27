# Bug Report

### Describe the bug

The `querystring` getter on the request object appears to be broken or missing. When trying to access `ctx.querystring` or `this.querystring` in a Koa application, I'm getting unexpected behavior - it seems like the property is not functioning as expected.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async ctx => {
  // Trying to access querystring
  console.log(ctx.querystring);
  ctx.body = ctx.querystring;
});

app.listen(3000);
```

When making a request to `http://localhost:3000?foo=bar&baz=qux`, the querystring property doesn't return the expected value `foo=bar&baz=qux`.

### Expected behavior

The `querystring` getter should return the raw query string from the URL (without the leading `?`). For example, a request to `/?name=john&age=30` should return `name=john&age=30`.

### System Info
- Koa version: latest
- Node version: 18.x

---
Repository: /testbed
