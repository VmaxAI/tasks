# Bug Report

### Describe the bug

After a recent update, I'm getting errors when trying to access the `type` property on response objects. The application crashes with "Cannot read property 'split' of undefined" or similar errors when trying to get the content type from responses.

### Reproduction

```js
const express = require('express')
const app = express()

app.get('/test', (req, res) => {
  res.set('Content-Type', 'application/json; charset=utf-8')
  
  // This should return 'application/json' but throws an error instead
  const contentType = res.type
  console.log(contentType)
  
  res.send({ success: true })
})
```

When I try to access `res.type`, the server crashes instead of returning the content type.

### Expected behavior

The `type` getter should return the content type without the parameters (e.g., 'application/json' from 'application/json; charset=utf-8'). It should return an empty string if no Content-Type header is set.

This was working fine in previous versions but broke recently. Not sure what changed but it's blocking our deployment.

---
Repository: /testbed
