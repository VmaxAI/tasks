# Bug Report

### Describe the bug

When canceling a request, the error object returned has incorrect properties. The `code` property shows `ERR_BAD_REQUEST` instead of `ERR_CANCELED`, and the `name` property is set to `'AxiosError'` instead of `'CanceledError'`.

This makes it difficult to properly identify and handle canceled requests in application code, as the error type doesn't match what's expected for a cancellation.

### Reproduction

```js
const axios = require('axios');
const CancelToken = axios.CancelToken;
const source = CancelToken.source();

axios.get('/some-endpoint', {
  cancelToken: source.token
}).catch(error => {
  console.log('Error name:', error.name); // Expected: 'CanceledError', Actual: 'AxiosError'
  console.log('Error code:', error.code); // Expected: 'ERR_CANCELED', Actual: 'ERR_BAD_REQUEST'
});

source.cancel('Request canceled by user');
```

### Expected behavior

- `error.name` should be `'CanceledError'`
- `error.code` should be `'ERR_CANCELED'`

This is breaking existing error handling logic that checks for these specific properties to differentiate between canceled requests and actual errors.

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
