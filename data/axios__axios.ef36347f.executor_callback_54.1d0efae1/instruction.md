# Bug Report

### Describe the bug

I'm experiencing an issue with `CancelToken` where cancellation doesn't work properly. When I try to cancel a request using `CancelToken`, the request continues to execute and the cancellation callback is never triggered.

### Reproduction

```js
const CancelToken = axios.CancelToken;
const source = CancelToken.source();

axios.get('/api/data', {
  cancelToken: source.token
}).then(response => {
  console.log('Request completed:', response);
}).catch(error => {
  if (axios.isCancel(error)) {
    console.log('Request canceled:', error.message);
  }
});

// Try to cancel the request
source.cancel('Operation canceled by user');

// Expected: catch block should execute with cancel error
// Actual: Request continues and completes normally
```

### Expected behavior

When `source.cancel()` is called, the request should be canceled immediately and the promise should reject with a cancel error. The catch block should execute and `axios.isCancel(error)` should return true.

### Actual behavior

The cancellation doesn't happen. The request completes normally as if cancel was never called. It seems like the cancel token is not properly detecting or handling the cancellation request.

### System Info

- axios version: latest
- Node version: 18.x
- Environment: Both browser and Node.js

---
Repository: /testbed
