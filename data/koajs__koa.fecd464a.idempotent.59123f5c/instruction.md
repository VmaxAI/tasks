# Bug Report

### Describe the bug

After a recent update, the application crashes on startup with a syntax error. It appears that some JavaScript code in `lib/request.js` has been replaced with Python code, causing the entire module to fail to load.

### Reproduction

Simply try to start the application or import the request module:

```js
const request = require('./lib/request');
// SyntaxError: Unexpected token 'def'
```

Or any code that uses the `idempotent` getter will fail:

```js
const ctx = // ... create context
if (ctx.request.idempotent) {
  // This code is unreachable now
}
```

### Expected behavior

The `idempotent` getter should return a boolean indicating whether the HTTP method is idempotent (GET, HEAD, PUT, DELETE, OPTIONS, TRACE). The module should load without syntax errors.

### System Info
- Node.js version: 16.x
- OS: macOS

This is blocking our entire application from running. The request module is core functionality and can't be loaded at all with the current code.

---
Repository: /testbed
