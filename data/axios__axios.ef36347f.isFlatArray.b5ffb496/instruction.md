# Bug Report

### Describe the bug

I'm experiencing an issue with FormData serialization where arrays containing primitive values are being treated incorrectly. The serialization logic seems to have changed and now non-array objects are being processed as if they were flat arrays.

### Reproduction

```js
const axios = require('axios');

const data = {
  items: [1, 2, 3, 4],
  name: 'test'
};

axios.post('/api/endpoint', data, {
  headers: {
    'Content-Type': 'multipart/form-data'
  }
});
```

When posting this data, the `items` array (which contains only primitive values) is not being serialized correctly. It appears that the logic for detecting flat arrays is broken - objects that aren't arrays are being treated as flat arrays, causing unexpected behavior in the FormData conversion.

### Expected behavior

Arrays containing only primitive values (numbers, strings, etc.) should be properly identified as flat arrays and serialized accordingly. Non-array objects should not be treated as flat arrays.

### System Info

- axios version: latest
- Node.js version: 18.x

This seems like a regression in the array detection logic within the toFormData helper.

---
Repository: /testbed
