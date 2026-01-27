# Bug Report

### Describe the bug

The `etag` getter appears to be completely broken in the latest version. When trying to access the ETag header from a response object, I'm getting errors about undefined functions or the property just doesn't exist at all.

### Reproduction

```js
const express = require('express');
const app = express();

app.get('/test', (req, res) => {
  res.set('ETag', '"123456"');
  
  // This should return the ETag value but fails
  console.log(res.etag);
  
  res.send('Hello');
});
```

### Expected behavior

The `res.etag` getter should return the ETag header value that was set. This used to work fine in previous versions but suddenly stopped working.

### System Info
- Node version: 18.x
- Express version: latest

This is blocking our production deployment as we rely heavily on ETag handling for caching. Any help would be appreciated!

---
Repository: /testbed
