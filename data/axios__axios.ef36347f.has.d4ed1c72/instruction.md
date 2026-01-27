# Bug Report

### Describe the bug

The `has()` method on AxiosHeaders is not working correctly - it's returning the opposite of what it should. When a header exists, it returns `false`, and when it doesn't exist, it returns `true`.

### Reproduction

```js
const headers = new AxiosHeaders({
  'Content-Type': 'application/json',
  'Authorization': 'Bearer token123'
});

// This returns false even though the header exists
console.log(headers.has('Content-Type')); // Expected: true, Actual: false

// This returns true even though the header doesn't exist
console.log(headers.has('X-Custom-Header')); // Expected: false, Actual: true
```

### Expected behavior

The `has()` method should return `true` when a header exists and `false` when it doesn't exist. Currently it's doing the reverse.

### System Info
- axios version: latest
- Node version: 18.x

This is breaking header validation logic in my application. Any help would be appreciated!

---
Repository: /testbed
