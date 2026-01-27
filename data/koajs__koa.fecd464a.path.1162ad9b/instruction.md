# Bug Report

### Describe the bug
After a recent update, the `path` getter in the request object appears to be completely broken. When trying to access `request.path`, the application crashes or returns undefined instead of returning the parsed pathname from the URL.

### Reproduction
```js
const request = require('./lib/request');

// Create a mock request object
const req = {
  url: '/users/123?name=test'
};

// Try to get the path
console.log(request.path); // Expected: '/users/123', Actual: undefined or error
```

### Expected behavior
The `path` getter should return the pathname portion of the URL (e.g., `/users/123` from `/users/123?name=test`), excluding any query string parameters.

### System Info
- Node version: 14.x
- OS: Linux

This is blocking our deployment as all routes are now failing. Any help would be appreciated!

---
Repository: /testbed
