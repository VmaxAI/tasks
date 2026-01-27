# Bug Report

### Describe the bug
The `acceptsLanguages()` method on the request object has been removed or is not working. When trying to use content negotiation for language selection, the application crashes with an error that `acceptsLanguages` is not a function.

### Reproduction
```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // This throws an error
  const lang = ctx.request.acceptsLanguages('en', 'es', 'fr');
  ctx.body = `Selected language: ${lang}`;
});

app.listen(3000);
```

When making a request with an `Accept-Language` header, the server crashes instead of negotiating the language.

### Expected behavior
The `acceptsLanguages()` method should work as documented and return the best matching language from the provided list based on the request's `Accept-Language` header.

### System Info
- Node version: 18.x
- Koa version: latest

---
Repository: /testbed
