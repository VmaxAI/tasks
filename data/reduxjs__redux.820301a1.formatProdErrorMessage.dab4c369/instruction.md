# Bug Report

### Describe the bug

The error message URL generated in production builds is pointing to the wrong error code. When an error occurs, the link in the error message directs users to a different error page than the actual error that was thrown.

### Reproduction

```js
// Trigger any Redux error in production mode, for example error code 15
// The error message will show:
// "Minified Redux error #15; visit http://redux.js.org/Errors?code=16 for the full message..."

// The URL shows code=16 instead of code=15
```

### Expected behavior

The error message URL should match the actual error code that was thrown. If error #15 occurs, the link should point to `http://redux.js.org/Errors?code=15`, not `code=16`.

### System Info
- Redux version: latest
- Environment: Production build

---
Repository: /testbed
