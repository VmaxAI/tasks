# Bug Report

### Describe the bug

I'm experiencing an issue where response headers cannot be removed properly. When trying to remove a header from the response object, it doesn't seem to work anymore.

### Reproduction

```js
const context = require('./test-helpers/context')
const Koa = require('koa')

const app = new Koa()
const ctx = context({ url: '/' }, {}, app)

// Set a header
ctx.response.set('X-Custom-Header', 'value')

// Try to remove it
ctx.response.remove('X-Custom-Header')

// Header is still present
console.log(ctx.response.get('X-Custom-Header')) // Expected: undefined, Actual: 'value'
```

### Expected behavior

The `removeHeader` method should properly delete headers from the response object. After calling `remove()` on a header, attempting to get that header should return `undefined`.

### System Info

- Node version: 18.x
- Koa version: latest

This seems to have broken recently. The header removal functionality was working before but now headers persist even after calling remove.

---
Repository: /testbed
