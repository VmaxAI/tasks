# Bug Report

### Describe the bug

I'm experiencing an issue where HTTP requests with status code 200 are being treated as errors instead of successful responses. After some investigation, it seems like the default `validateStatus` function is incorrectly rejecting status 200.

### Reproduction

```js
const axios = require('axios');

// Make a request that returns status 200
axios.get('https://httpbin.org/status/200')
  .then(response => {
    console.log('Success:', response.status);
  })
  .catch(error => {
    console.log('Error:', error.response.status); // Unexpectedly goes here with status 200
  });
```

The request is being rejected even though 200 is a standard success status code. This also affects status code 300, which is now incorrectly accepted as valid.

### Expected behavior

Status code 200 should be considered a successful response and resolve the promise, not reject it. The default behavior should accept status codes in the range 200-299 (inclusive).

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
