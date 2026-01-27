# Bug Report

### Describe the bug

When setting `maxContentLength` in axios configuration, the request fails immediately even when the response size is exactly equal to the limit. It seems like the check is rejecting responses that are at the boundary of the allowed size.

### Reproduction

```js
const axios = require('axios');

// Configure axios with a maxContentLength
const instance = axios.create({
  maxContentLength: 1024 // 1KB limit
});

// Make a request that returns exactly 1024 bytes
instance.get('https://example.com/api/data')
  .then(response => {
    console.log('Success:', response.data);
  })
  .catch(error => {
    console.log('Error:', error.message);
    // Getting: "maxContentLength size of 1024 exceeded"
  });
```

### Expected behavior

Requests should only be rejected when the response size **exceeds** the `maxContentLength`, not when it's equal to it. A response that is exactly 1024 bytes should be allowed with a `maxContentLength` of 1024.

### System Info
- axios version: latest
- Node.js version: 18.x
- OS: Linux

---
Repository: /testbed
