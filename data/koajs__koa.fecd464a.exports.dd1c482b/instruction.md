# Bug Report

### Describe the bug

The test helper context module appears to be completely broken. When trying to create a test context for Koa applications, I'm getting unexpected errors because the module exports are not functioning as expected.

### Reproduction

```js
const context = require('./test-helpers/context')
const Koa = require('./lib/application')

const app = new Koa()
const ctx = context({
  url: '/test',
  method: 'GET'
}, {}, app)

// This should create a valid Koa context but fails
console.log(ctx.request)
```

### Expected behavior

The context helper should create a mock request/response pair and return a valid Koa context object with properly initialized request and response objects. The exported functions should work for creating test contexts.

### Additional context

This was working fine before, but now the context creation is completely broken. The module seems to have been replaced with something unrelated. Not sure if this was an accidental commit or what happened here.

---
Repository: /testbed
