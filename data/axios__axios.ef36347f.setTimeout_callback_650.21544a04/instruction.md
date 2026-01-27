# Bug Report

### Describe the bug

Request timeouts are not working properly - when a request exceeds the configured timeout value, it doesn't get aborted and the timeout error is never triggered. The request just hangs indefinitely instead of timing out as expected.

### Reproduction

```js
const axios = require('axios');

// Configure a request with a 1 second timeout
axios.get('http://example.com/slow-endpoint', {
  timeout: 1000
})
.then(response => {
  console.log('Success:', response.data);
})
.catch(error => {
  console.log('Error:', error.message);
  // Expected: "timeout of 1000ms exceeded"
  // Actual: Request never times out
});
```

### Expected behavior

When a request takes longer than the specified timeout value, it should be aborted and reject with a timeout error. The promise should be rejected with an AxiosError containing the timeout message.

### Actual behavior

The request continues indefinitely without timing out. The timeout callback appears to be registered but never fires, so the request is never aborted.

### System Info

- axios version: latest
- Node.js version: v18.x
- OS: Linux

---
Repository: /testbed
