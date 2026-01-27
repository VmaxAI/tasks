# Bug Report

### Describe the bug

I'm experiencing an issue with `toFormData` where plain objects are not being properly converted to FormData. It seems like the conversion is skipping over regular objects and only processing arrays.

### Reproduction

```js
import toFormData from 'axios/lib/helpers/toFormData';

const data = {
  user: {
    name: 'John',
    email: 'john@example.com'
  },
  tags: ['tag1', 'tag2']
};

const formData = toFormData(data);

// Expected: FormData should contain user.name and user.email entries
// Actual: Only the tags array is being processed, nested objects are ignored
```

When I try to convert an object with nested plain objects to FormData, the nested objects are not being traversed. Arrays work fine, but any nested object properties are being skipped entirely.

### Expected behavior

Both plain objects and arrays should be recursively visited and converted to FormData entries. Nested objects should be flattened into the FormData with proper key naming (e.g., `user[name]`, `user[email]`).

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
