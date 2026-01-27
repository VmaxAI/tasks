# Bug Report

### Describe the bug

The `has()` method in AxiosHeaders is returning incorrect results. When checking if a header exists, it returns `true` when the header doesn't exist and `false` when it does exist - the logic appears to be inverted.

### Reproduction

```js
const headers = new AxiosHeaders({
  'Content-Type': 'application/json',
  'Authorization': 'Bearer token123'
});

// This returns false (should be true)
console.log(headers.has('Content-Type')); 

// This returns true (should be false)
console.log(headers.has('X-Custom-Header'));
```

### Expected behavior

- `headers.has('Content-Type')` should return `true` since the header exists
- `headers.has('X-Custom-Header')` should return `false` since the header doesn't exist

Currently getting the opposite behavior - existing headers report as not present, and non-existent headers report as present.

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
