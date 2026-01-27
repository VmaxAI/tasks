# Bug Report

### Describe the bug

After a recent update, calling `flushHeaders()` on a response object causes the application to crash with a syntax error. The method appears to be completely broken and the server won't start.

### Reproduction

```js
const express = require('express')
const app = express()

app.get('/test', (req, res) => {
  res.set('X-Custom-Header', 'value')
  res.flushHeaders()  // This causes the server to crash
  // ... rest of the response
})

app.listen(3000)
```

### Expected behavior

The `flushHeaders()` method should flush any set headers to the client and allow the response body to be sent afterwards, as documented. The server should not crash.

### System Info
- Node version: 18.x
- Express version: latest

This is blocking our deployment as we use `flushHeaders()` extensively for streaming responses. Any help would be appreciated!

---
Repository: /testbed
