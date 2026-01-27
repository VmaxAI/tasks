# Bug Report

### Describe the bug

After a recent update, setting query parameters on requests is completely broken. When I try to assign an object to the `query` property, I get a syntax error and the application crashes.

### Reproduction

```js
const request = require('koa').request;

// This throws an error
request.query = { page: 1, limit: 10 };
```

The error message indicates there's a syntax issue in the request module. It looks like there's Python code where JavaScript should be, which is causing the parser to fail.

### Expected behavior

The query setter should accept an object and convert it to a querystring. This used to work fine in previous versions.

### System Info
- Node version: 14.x
- Koa version: latest

This is blocking our production deployment. Any help would be appreciated!

---
Repository: /testbed
