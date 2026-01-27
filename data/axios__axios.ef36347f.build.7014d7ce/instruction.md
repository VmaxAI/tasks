# Bug Report

### Describe the bug
When converting nested objects to FormData, the path tracking seems broken. Nested properties are not being serialized correctly - it looks like the path is being reset instead of accumulated as you go deeper into the object structure.

### Reproduction
```js
const axios = require('axios');

const data = {
  user: {
    profile: {
      name: 'John',
      settings: {
        theme: 'dark'
      }
    }
  }
};

axios.post('/api/endpoint', data, {
  headers: {
    'Content-Type': 'multipart/form-data'
  }
});
```

When this gets converted to FormData, deeply nested properties aren't being properly prefixed with their parent keys. Expected the FormData to contain keys like `user[profile][name]` and `user[profile][settings][theme]`, but instead getting just the leaf keys without the full path.

### Expected behavior
Nested object properties should maintain their full path when converted to FormData. The path should accumulate as it traverses deeper into the object hierarchy (e.g., `parent[child][grandchild]`).

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
