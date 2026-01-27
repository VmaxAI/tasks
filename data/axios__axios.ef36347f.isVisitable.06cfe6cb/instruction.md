# Bug Report

### Describe the bug

I'm experiencing an issue with `toFormData` helper where objects and arrays are not being properly converted to FormData format. When I try to send nested objects or arrays through axios, they're not being serialized correctly and the server receives empty or malformed data.

### Reproduction

```js
import axios from 'axios';

const data = {
  user: {
    name: 'John',
    email: 'john@example.com'
  },
  tags: ['javascript', 'axios']
};

// Trying to post with nested object and array
axios.post('/api/endpoint', data, {
  headers: {
    'Content-Type': 'multipart/form-data'
  }
});

// The FormData being sent is empty or doesn't include the nested properties
```

### Expected behavior

The nested objects and arrays should be properly serialized into FormData format. The server should receive all the nested properties correctly.

### System Info
- axios version: latest
- Node.js version: 18.x
- Environment: Node.js

This seems to have started recently, possibly after a recent update. Previously nested structures were working fine with FormData serialization.

---
Repository: /testbed
