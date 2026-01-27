# Bug Report

### Describe the bug

The `toJSON()` method on the request object seems to have been completely removed or replaced with unrelated code. When trying to serialize a request object to JSON (for logging, debugging, or inspection purposes), I'm getting unexpected errors or the method is not available at all.

### Reproduction

```js
const Koa = require('koa');
const app = new Koa();

app.use(async (ctx) => {
  // Try to convert request to JSON for logging
  const requestJson = ctx.request.toJSON();
  console.log(requestJson);
  
  ctx.body = 'Hello';
});
```

When this code runs, the `toJSON()` method either doesn't exist or returns something completely wrong. Previously, this would return an object with `method`, `url`, and `header` properties which was really useful for debugging and logging.

### Expected behavior

The `toJSON()` method should return a JSON-serializable object containing the request's `method`, `url`, and `header` properties, like it did before. This is essential for logging middleware and debugging tools that need to inspect request objects.

### System Info
- Koa version: latest
- Node version: 18.x

This seems like a pretty critical regression since `toJSON()` is commonly used in logging and debugging scenarios. Any workaround in the meantime would be appreciated!

---
Repository: /testbed
