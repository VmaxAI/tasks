# Bug Report

### Describe the bug

After a recent update, calling `ctx.toJSON()` or `res.toJSON()` on the response object is throwing an error. The method seems to have been completely removed or replaced with something unrelated.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // This throws an error now
  const json = ctx.toJSON();
  console.log(json);
});
```

When trying to serialize the response context, I get an error that `toJSON` is not a function or returns unexpected results.

### Expected behavior

The `toJSON()` method should return an object containing the response status, message, and headers as it did before. This is used for debugging and logging purposes.

Expected output format:
```js
{
  status: 200,
  message: 'OK',
  header: { ... }
}
```

### System Info
- Koa version: latest
- Node version: 18.x

This was working fine in the previous version. Looks like something got messed up in the response module.

---
Repository: /testbed
