# Bug Report

### Describe the bug

The `attachment()` method on response objects appears to be completely broken. When trying to set a file attachment with a filename, I'm getting errors that the method doesn't exist or isn't functioning properly.

### Reproduction

```js
const express = require('express');
const app = express();

app.get('/download', (req, res) => {
  res.attachment('document.pdf');
  res.send('file content');
});
```

When hitting this endpoint, the server throws an error instead of setting the Content-Disposition header correctly.

### Expected behavior

The `attachment()` method should:
1. Set the Content-Disposition header with the provided filename
2. Automatically set the Content-Type based on the file extension if not already set
3. Allow passing additional options for the content disposition

### System Info
- Node version: 18.x
- Express version: Latest

This seems like a critical regression as file downloads are completely non-functional. Any help would be appreciated!

---
Repository: /testbed
