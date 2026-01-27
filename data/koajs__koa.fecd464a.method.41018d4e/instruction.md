# Bug Report

### Describe the bug

After a recent update, I'm getting a `TypeError` when trying to set the HTTP method on a request object. The setter for the `method` property seems to be missing or broken.

### Reproduction

```js
const request = require('./lib/request');

// Try to set the request method
request.method = 'POST';  // TypeError: Cannot set property method of #<Object> which has only a getter
```

### Expected behavior

Setting `request.method` should update the underlying `req.method` property without throwing an error. This was working fine in previous versions.

### System Info
- Node.js version: 14.x
- OS: Linux

---
Repository: /testbed
