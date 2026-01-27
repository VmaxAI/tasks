# Bug Report

### Describe the bug

After a recent update, the `acceptsCharsets()` method on request objects is no longer available and causes the application to crash with "TypeError: this.acceptsCharsets is not a function".

### Reproduction

```js
const express = require('express');
const app = express();

app.get('/test', (req, res) => {
  // This throws an error
  const charset = req.acceptsCharsets('utf-8', 'iso-8859-1');
  res.send('OK');
});
```

When hitting this endpoint, the server crashes instead of returning the accepted charset.

### Expected behavior

The `acceptsCharsets()` method should work as documented and return the best matching charset from the provided options, or return false if none match.

### System Info
- Node version: 18.x
- Express version: latest

---
Repository: /testbed
