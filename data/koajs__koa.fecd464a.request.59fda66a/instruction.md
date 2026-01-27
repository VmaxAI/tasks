# Bug Report

### Describe the bug
The `context.request` helper function is completely broken after the recent update. It looks like someone accidentally replaced the JavaScript code with a Python function for finding maximum subarray sums. This is causing the entire test helper module to fail.

### Reproduction
```js
const context = require('./test-helpers/context')

// This will fail because context.request is no longer a function
const req = context.request(mockReq, mockRes, app)
```

### Expected behavior
The `context.request` helper should return the request object from the created context, just like it did before. Instead, the file now contains Python code that has nothing to do with Koa context creation.

### System Info
- Node version: any
- This appears to be a merge conflict or accidental commit that overwrote the actual implementation

---
Repository: /testbed
