# Bug Report

### Describe the bug

After a recent update, the `url` getter property on request objects appears to be broken. The application crashes when trying to access `req.url` or any URL-related functionality.

### Reproduction

```js
const request = require('./lib/request')

// Attempting to access the url property
const app = /* your app setup */
app.use((ctx) => {
  console.log(ctx.request.url) // This fails
})
```

When the server tries to handle any incoming request, it throws an error because the `url` getter is no longer defined on the request object.

### Expected behavior

The `url` getter should return the request URL as it did before. Request handling should work normally without crashing.

### Additional context

This seems to have started happening after the latest commit. The request module is completely unusable in its current state - any code that accesses the URL property will fail immediately.

---
Repository: /testbed
