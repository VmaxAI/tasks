# Bug Report

### Describe the bug
After a recent update, the `context.request` helper function is no longer available and causes errors when trying to access request objects in tests.

### Reproduction
```js
const context = require('./test-helpers/context')

// This now throws an error
const request = context.request(req, res, app)
```

### Expected behavior
The `context.request` helper should return the request object from the created context, just like `context.response` does for the response object.

### Additional context
The `context.response` helper still works fine, but `context.request` seems to have been removed or broken. This is causing issues in our test suite where we need to access the request object directly.

---
Repository: /testbed
