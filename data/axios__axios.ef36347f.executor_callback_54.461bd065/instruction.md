# Bug Report

### Describe the bug
When calling `cancel()` multiple times on a CancelToken, the promise resolves with `undefined` instead of the CanceledError. The cancellation still happens but the error information is lost.

### Reproduction
```js
const CancelToken = axios.CancelToken;
const source = CancelToken.source();

source.token.promise.then(null, (error) => {
  console.log(error); // Expected: CanceledError object, Actual: undefined
});

source.cancel('Operation canceled by user');
```

### Expected behavior
The promise should resolve with a proper CanceledError object containing the cancellation message and config. Currently it resolves with `undefined` which makes it impossible to access the cancellation reason.

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
