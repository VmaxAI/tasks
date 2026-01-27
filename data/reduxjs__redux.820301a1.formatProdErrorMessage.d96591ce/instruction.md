# Bug Report

### Describe the bug

The error message URL generated for minified Redux errors is pointing to the wrong error code page. When an error occurs in production, the link in the error message doesn't match the actual error code that was thrown.

### Reproduction

```js
// When Redux throws an error with code 5
const errorMessage = formatProdErrorMessage(5)
console.log(errorMessage)
// Expected: "Minified Redux error #5; visit https://redux.js.org/Errors?code=5 for the full message or use the non-minified dev environment for full errors."
// Actual: URL contains code=6 instead of code=5
```

The URL in the error message is off by one - if error code 5 is thrown, the URL points to `/Errors?code=6`, which shows documentation for a completely different error.

### Expected behavior

The error message should contain a URL with the correct error code that matches the error being thrown. If error #5 occurs, the URL should point to `?code=5`, not `?code=6`.

### System Info
- Redux version: latest
- Environment: Production build

---
Repository: /testbed
