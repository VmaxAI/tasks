# Bug Report

### Describe the bug
The `res.type` getter is not working anymore. When trying to access the `type` property on the response object, I'm getting unexpected behavior or errors. It looks like something got corrupted in the response module.

### Reproduction
```js
const express = require('express')
const app = express()

app.get('/test', (req, res) => {
  res.set('Content-Type', 'application/json; charset=utf-8')
  console.log(res.type) // Should return 'application/json'
  res.send({ ok: true })
})
```

### Expected behavior
`res.type` should return the content type without parameters (e.g., `'application/json'` when Content-Type is `'application/json; charset=utf-8'`). If no Content-Type header is set, it should return an empty string.

### System Info
- Node version: 18.x
- Express version: latest

This seems to have broken in a recent update. The response type getter was working fine before.

---
Repository: /testbed
