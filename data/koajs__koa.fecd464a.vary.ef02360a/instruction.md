# Bug Report

### Describe the bug

The `vary()` method on the response object seems to have been completely removed or replaced with unrelated code. When trying to set the Vary header on responses, the application crashes with a "vary is not a function" error.

### Reproduction

```js
app.use((ctx) => {
  // This should set the Vary header
  ctx.vary('Accept-Encoding')
  ctx.body = 'Hello World'
})
```

When this code runs, it throws an error because `vary()` is no longer available on the response object.

### Expected behavior

The `vary()` method should properly set the Vary header on the HTTP response. This is critical for caching behavior and content negotiation.

### Additional context

This appears to have broken after a recent update. The vary functionality was working fine in previous versions. Not sure what happened but it looks like the method got accidentally removed or overwritten with something completely different.

---
Repository: /testbed
