# Bug Report

### Describe the bug

After a recent update, the request query parsing functionality appears to be completely broken. When trying to access `req.query` on incoming requests, I'm getting errors that the property doesn't exist or behaves unexpectedly.

### Reproduction

```js
const Koa = require('koa')
const app = new Koa()

app.use(async ctx => {
  // This should parse the query string
  console.log(ctx.request.query)
  ctx.body = ctx.request.query
})

app.listen(3000)
```

When making a request to `http://localhost:3000?foo=bar&baz=qux`, the query object is not being parsed correctly or is undefined.

### Expected behavior

The `query` getter should parse the query string and return an object like:
```js
{ foo: 'bar', baz: 'qux' }
```

### System Info
- Node version: 14.x
- Koa version: latest

This was working fine before the latest update. Any help would be appreciated!

---
Repository: /testbed
