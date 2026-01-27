# Bug Report

### Describe the bug

After updating to the latest version, the `acceptsCharsets()` method is no longer available on the request object. When trying to call `req.acceptsCharsets()`, I get an error that the method is undefined.

### Reproduction

```js
app.get('/test', (req, res) => {
  // This throws: TypeError: req.acceptsCharsets is not a function
  const charset = req.acceptsCharsets('utf-8', 'iso-8859-1');
  res.send('OK');
});
```

### Expected behavior

The `acceptsCharsets()` method should be available on the request object and should return the best matching charset from the provided arguments based on the Accept-Charset header, similar to how `accepts()` works for content types.

### Additional context

This was working fine in previous versions. The method seems to have been removed or replaced with something else. I checked the documentation but it still mentions `acceptsCharsets()` as a valid method.

---
Repository: /testbed
