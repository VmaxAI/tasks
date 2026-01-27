# Bug Report

### Describe the bug

The `acceptsLanguages()` method on the request object has been completely removed/replaced, causing any code that relies on language negotiation to break. When trying to call `req.acceptsLanguages()`, the method is no longer available.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // This will fail - acceptsLanguages is not a function
  const lang = ctx.request.acceptsLanguages('en', 'es', 'fr');
  ctx.body = `Preferred language: ${lang}`;
});

app.listen(3000);
```

When making a request with `Accept-Language: fr-FR,fr;q=0.9,en;q=0.8` header, the server crashes instead of returning the preferred language.

### Expected behavior

The `acceptsLanguages()` method should work as documented and return the best matching language from the provided list based on the `Accept-Language` header. It should support both single language checks and multiple language negotiation.

### System Info

- Node version: 18.x
- Koa version: latest

This is breaking our i18n implementation that depends on automatic language detection. Any help would be appreciated!

---
Repository: /testbed
