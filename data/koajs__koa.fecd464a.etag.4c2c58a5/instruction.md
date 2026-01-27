# Bug Report

### Describe the bug

After a recent update, the `etag` getter on the response object seems to have been completely removed or replaced with unrelated code. When trying to access `res.etag` in my Express application, I'm getting unexpected behavior - it's no longer returning the ETag header value.

### Reproduction

```js
const express = require('express');
const app = express();

app.get('/test', (req, res) => {
  res.set('ETag', '"123456"');
  
  // This should return the ETag header value
  console.log(res.etag); // Expected: '"123456"'
  
  res.send('test');
});
```

### Expected behavior

`res.etag` should return the value of the ETag header (e.g., `'"123456"'`), just like it did in previous versions. The getter should retrieve the header using `this.get('ETag')`.

### Additional context

Looking at the response object, it seems like the `etag` getter property is missing entirely. This is breaking existing code that relies on reading the ETag value from the response object.

---
Repository: /testbed
