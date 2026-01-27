# Bug Report

### Describe the bug

I'm experiencing an issue with case-insensitive key lookup in objects. When searching for a key in an object using different casing, the function returns the wrong key or doesn't find the correct match.

### Reproduction

```js
const headers = {
  'Content-Type': 'application/json',
  'Authorization': 'Bearer token',
  'X-Custom-Header': 'value'
};

// Looking for 'content-type' (lowercase)
const result = findKey(headers, 'content-type');
// Expected: 'Content-Type'
// Actual: Returns wrong key or last key in object
```

### Expected behavior

The function should return the original key name from the object when a case-insensitive match is found. For example, searching for `'authorization'` should return `'Authorization'`.

### Additional context

This seems to affect any object with multiple keys. The last key in the object is often returned regardless of whether it matches the search term. This is breaking header lookups in HTTP requests where case-insensitive matching is required.

---
Repository: /testbed
