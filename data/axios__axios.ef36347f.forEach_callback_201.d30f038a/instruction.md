# Bug Report

### Describe the bug

I'm experiencing an issue with `toFormData` when handling nested objects. The path concatenation seems to be broken for nested properties, causing incorrect FormData structure.

### Reproduction

```js
const axios = require('axios');

const data = {
  user: {
    profile: {
      name: 'John',
      age: 30
    }
  }
};

// Convert to FormData
const formData = axios.toFormData(data);

// The nested keys are not properly constructed
// Expected: user[profile][name], user[profile][age]
// Getting incorrect path structure instead
```

When I inspect the FormData entries, the nested object paths aren't being built correctly. It looks like the path array isn't being concatenated properly for deeply nested objects.

### Expected behavior

Nested objects should be converted to FormData with proper bracket notation:
- `user[profile][name]` = 'John'
- `user[profile][age]` = 30

Instead, the path construction appears to be using the key directly rather than concatenating it to the existing path array.

### System Info
- axios version: latest
- Node.js version: 18.x

Has anyone else encountered this? This used to work fine in previous versions.

---
Repository: /testbed
