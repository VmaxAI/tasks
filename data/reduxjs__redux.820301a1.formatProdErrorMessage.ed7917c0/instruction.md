# Bug Report

### Describe the bug

I'm getting malformed error messages when using the minified production build of Redux. The error code appears to be duplicated in the message, and the link to the error documentation points to the wrong error code.

### Reproduction

When an error is thrown in production mode, the error message looks like this:

```
Minified Redux error #11; visit https://redux.js.org/Errors?code=2 for the full message or use the non-minified dev environment for full errors.
```

Expected format:
```
Minified Redux error #1; visit https://redux.js.org/Errors?code=1 for the full message or use the non-minified dev environment for full errors.
```

The error code is being duplicated (e.g., "error #11" instead of "error #1"), and the documentation URL has an incremented code value that doesn't match the actual error.

### Expected behavior

The error message should display the correct error code without duplication, and the documentation link should point to the matching error code page.

### System Info
- Redux version: latest
- Environment: production build (minified)

---
Repository: /testbed
