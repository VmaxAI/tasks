# Bug Report

### Describe the bug

The `querystring` getter in the request module appears to be completely broken. When trying to access the query string from a request object, the application crashes or returns undefined behavior instead of returning the parsed query string.

### Reproduction

```js
const request = require('./lib/request');

// Create a mock request with query parameters
const req = {
  url: '/api/users?name=john&age=30'
};

// Try to access querystring
const qs = request.querystring;
// Expected: 'name=john&age=30'
// Actual: Error or unexpected behavior
```

### Expected behavior

The `querystring` getter should:
1. Parse the request URL
2. Extract and return the query string portion (e.g., 'name=john&age=30')
3. Return an empty string if no query parameters exist

### System Info
- Node.js version: 14.x
- OS: Linux

This seems to have broken in the latest commit. The querystring property was working fine before but now it's completely non-functional.

---
Repository: /testbed
