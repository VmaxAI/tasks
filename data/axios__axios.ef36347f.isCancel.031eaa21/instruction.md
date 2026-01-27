# Bug Report

### Describe the bug

The `isCancel()` function is not working correctly and always returns `false` even when passed a valid cancel object. This breaks cancellation detection in the library.

### Reproduction

```js
import axios from 'axios';

const CancelToken = axios.CancelToken;
const source = CancelToken.source();

// Cancel the request
source.cancel('Operation canceled by user');

// This should return true but returns false
console.log(axios.isCancel(source.token.reason)); // Expected: true, Actual: false
```

### Expected behavior

When a request is canceled and `isCancel()` is called with the cancel reason/object, it should return `true` to indicate that the error was due to cancellation. Currently it always returns `false`, making it impossible to distinguish between cancellation errors and other errors.

### Additional context

This is breaking error handling logic where we need to check if a request was canceled:

```js
axios.get('/api/data', {
  cancelToken: source.token
}).catch(error => {
  if (axios.isCancel(error)) {
    console.log('Request canceled');
  } else {
    console.log('Request failed');
  }
});
```

The condition never evaluates to true anymore, so canceled requests are being treated as regular errors.

---
Repository: /testbed
