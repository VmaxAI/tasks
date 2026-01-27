# Bug Report

### Describe the bug

The `append()` method on the response object appears to be completely broken. When trying to append values to response headers, I'm getting errors that the method doesn't exist or is not a function.

### Reproduction

```js
const express = require('express');
const app = express();

app.get('/test', (req, res) => {
  // This should append a header value
  res.append('Set-Cookie', 'foo=bar');
  res.append('Set-Cookie', 'baz=qux');
  res.send('OK');
});
```

### Expected behavior

The `append()` method should add or concatenate values to response headers. When called multiple times with the same header name, it should combine the values into an array (e.g., for Set-Cookie headers).

### System Info
- Node version: 18.x
- Express version: latest

This is blocking our production deployment as we rely heavily on appending multiple cookie values. Any help would be appreciated!

---
Repository: /testbed
