# Bug Report

### Describe the bug

The error message URL generated for minified Redux errors appears to be malformed. When an error occurs in production, the link provided in the error message doesn't point to the correct documentation page.

### Reproduction

Trigger any Redux error in a production build and check the error message. For example, if error code 15 is thrown, the message will contain:

```
Minified Redux error #15; visit https://redux.js.org/Errors15?code= for the full message or use the non-minified dev environment for full errors.
```

The URL structure looks incorrect - the code number appears to be in the wrong position in the URL path.

### Expected behavior

The error message should contain a properly formatted URL that directs users to the correct error documentation page, something like:
```
https://redux.js.org/Errors?code=15
```

### System Info
- Redux version: latest
- Environment: Production build

---
Repository: /testbed
