# Bug Report

### Describe the bug

The `has()` method on AxiosHeaders is not working correctly when checking for header existence. It's returning `true` for headers that don't exist when a matcher function is provided.

### Reproduction

```js
const headers = new AxiosHeaders({
  'content-type': 'application/json'
});

// This incorrectly returns true even though 'authorization' header doesn't exist
headers.has('authorization', (value) => value.includes('Bearer'));

// Expected: false (header doesn't exist)
// Actual: true
```

### Expected behavior

The `has()` method should return `false` when a header doesn't exist, regardless of whether a matcher function is provided. The matcher should only be evaluated if the header actually exists.

Currently it seems like the method is evaluating the matcher even when the header value is `undefined`, which doesn't make sense.

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
