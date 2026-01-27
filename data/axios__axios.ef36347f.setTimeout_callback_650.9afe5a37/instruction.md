# Bug Report

### Describe the bug

Request timeouts are not being triggered properly. When a request exceeds the configured timeout value, it just hangs indefinitely instead of throwing a timeout error. The timeout handler doesn't seem to be executing when it should.

### Reproduction

```js
const axios = require('axios');

axios.get('https://httpbin.org/delay/10', {
  timeout: 2000
})
.then(response => {
  console.log('Success:', response.status);
})
.catch(error => {
  console.log('Error:', error.message);
  // Expected: timeout error after 2 seconds
  // Actual: request never times out
});
```

### Expected behavior

The request should be aborted after 2 seconds and reject with a timeout error. Instead, the request continues running and never triggers the timeout handler.

### System Info
- axios version: latest
- Node.js version: 18.x
- OS: Linux

---
Repository: /testbed
