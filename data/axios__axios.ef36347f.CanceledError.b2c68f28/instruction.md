# Bug Report

### Describe the bug

I'm experiencing an issue with canceled requests - they're being reported with the wrong error name and error code. When I cancel a request, instead of getting a `CanceledError` with the appropriate cancel code, I'm getting an `AxiosError` with what appears to be a bad request error code.

### Reproduction

```js
const controller = new AbortController();

axios.get('/api/data', {
  signal: controller.signal
}).catch(error => {
  console.log(error.name); // Expected: 'CanceledError', Actual: 'AxiosError'
  console.log(error.code); // Expected: ERR_CANCELED, Actual: ERR_BAD_REQUEST
});

controller.abort();
```

### Expected behavior

When a request is canceled:
- The error name should be `CanceledError`
- The error code should be `ERR_CANCELED` (not `ERR_BAD_REQUEST`)

This is breaking my error handling logic since I can't properly distinguish between canceled requests and actual bad requests anymore.

### System Info
- axios version: latest
- Node version: 18.x

---
Repository: /testbed
