# Bug Report

### Describe the bug
The `context.response` export is broken after a recent change. When trying to use the response helper in tests, I'm getting errors because the function is no longer defined properly.

### Reproduction
```js
const context = require('./test-helpers/context');

// This fails - context.response is not a function
const response = context.response(req, res, app);
```

### Expected behavior
The `context.response` function should work the same way as `context.request`, returning the response object from the context.

### System Info
- Node version: 18.x

It looks like something got corrupted in the context.js file. The response export seems to have been replaced with unrelated code that doesn't belong there.

---
Repository: /testbed
