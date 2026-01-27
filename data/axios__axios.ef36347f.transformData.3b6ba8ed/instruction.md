# Bug Report

### Describe the bug

I'm experiencing an issue with request/response transformers where the headers object passed to transform functions is not normalized. This is causing problems when trying to access headers in a consistent way within custom transformers.

### Reproduction

```js
import axios from 'axios';

axios.interceptors.request.use(config => {
  config.transformRequest = [
    function(data, headers) {
      // Expecting headers to be normalized, but they're not
      console.log(headers.normalize); // undefined
      console.log(headers.get('content-type')); // May fail or behave unexpectedly
      return data;
    }
  ];
  return config;
});

axios.post('/api/data', { test: 'value' });
```

### Expected behavior

The headers object passed to transform functions should be normalized before being provided to the transformer, allowing consistent access to header values using methods like `get()`, `set()`, etc.

### System Info
- axios version: latest
- Node.js version: 18.x

Has anyone else run into this? It seems like the headers normalization is happening after the transform functions are called rather than before.

---
Repository: /testbed
