# Bug Report

### Describe the bug
The `response` export from the context helper module seems to be broken or missing. When trying to use `context.response()` to create a response object for testing, I'm getting unexpected behavior.

### Reproduction
```js
const context = require('./test-helpers/context');

// This doesn't work as expected
const res = context.response(req, res, app);
```

### Expected behavior
Should be able to call `context.response()` just like `context.request()` to get the response object from the context. Both methods should work symmetrically.

### System Info
- Node version: Latest
- Running on: macOS

---
Repository: /testbed
