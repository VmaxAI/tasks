# Bug Report

### Describe the bug

The `append()` method on response objects is completely broken. When trying to append values to response headers, the server crashes or the method is not found.

### Reproduction

```js
const express = require('express')
const app = express()

app.get('/test', (req, res) => {
  // This should append a header value
  res.append('Set-Cookie', 'cookie1=value1')
  res.append('Set-Cookie', 'cookie2=value2')
  res.send('Hello')
})
```

### Expected behavior

The `append()` method should add header values, allowing multiple values for the same header field. When called multiple times with the same field name, it should concatenate the values into an array.

For example:
- First call: `res.append('Set-Cookie', 'cookie1=value1')` should set the header
- Second call: `res.append('Set-Cookie', 'cookie2=value2')` should append to existing value, resulting in an array of both cookies

### System Info
- Node version: 18.x
- Express version: latest

This is blocking our production deployment as we rely heavily on setting multiple cookie headers. Any help would be appreciated!

---
Repository: /testbed
