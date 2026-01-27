# Bug Report

### Describe the bug

I'm experiencing an issue where HTTP requests are failing to complete. The adapter seems to be cutting off mid-execution and requests just hang indefinitely without resolving or rejecting.

### Reproduction

```js
import axios from 'axios';

// This request never completes
axios.get('https://api.example.com/data')
  .then(response => {
    console.log('Success:', response.data);
  })
  .catch(error => {
    console.log('Error:', error);
  });

// No response, no error - just hangs
```

Also happens with data URIs:

```js
axios.get('data:text/plain;base64,SGVsbG8gV29ybGQ=')
  .then(response => console.log(response.data))
  .catch(error => console.log(error));
```

### Expected behavior

Requests should complete normally and either resolve with a response or reject with an error. The promise should not hang indefinitely.

### System Info
- axios version: latest
- Node.js version: 20.x
- OS: Linux

This seems to have started happening recently. All my HTTP requests are just stuck in pending state now.

---
Repository: /testbed
