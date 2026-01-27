# Bug Report

### Describe the bug

I'm experiencing an issue where response transformers don't seem to be chaining properly. When I have multiple transformers defined, only the first one appears to execute, and subsequent transformers receive the original data instead of the transformed data from the previous transformer.

### Reproduction

```js
const axios = require('axios');

const instance = axios.create({
  transformResponse: [
    function(data) {
      // First transformer - parse JSON
      return JSON.parse(data);
    },
    function(data) {
      // Second transformer - should receive parsed object
      // but receives original string instead
      console.log(typeof data); // Expected: 'object', Actual: 'string'
      return {
        ...data,
        transformed: true
      };
    }
  ]
});

instance.get('/api/data')
  .then(response => {
    console.log(response.data);
    // Expected: { ...parsedData, transformed: true }
    // Actual: just the parsed JSON without the 'transformed' property
  });
```

### Expected behavior

Each transformer in the chain should receive the output of the previous transformer. The transformations should be applied sequentially, with each transformer building on the result of the previous one.

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
