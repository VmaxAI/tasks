# Bug Report

### Describe the bug

The `path` getter on the request object appears to be broken or missing. When trying to access `req.path` in my application, I'm getting unexpected behavior - it's not returning the pathname as expected.

### Reproduction

```js
const request = require('./lib/request');

// Create a mock request object
const req = {
  url: '/users/123?name=test'
};

// Try to get the path
const pathname = request.path;
// Expected: '/users/123'
// Actual: undefined or error
```

### Expected behavior

The `path` getter should return the pathname portion of the URL (e.g., `/users/123`) without the query string, just like it did in previous versions.

### Additional context

This was working fine before, but after pulling the latest changes it seems like the `path` property is no longer accessible on request objects. My routes are failing because they rely on `req.path` to determine which handler to use.

---
Repository: /testbed
