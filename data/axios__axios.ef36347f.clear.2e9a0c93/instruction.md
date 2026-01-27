# Bug Report

### Describe the bug

The `clear()` method on AxiosHeaders is behaving incorrectly when called with a matcher argument. Instead of clearing headers that match the provided matcher, it seems to be doing the opposite - clearing headers that DON'T match.

### Reproduction

```js
const headers = new AxiosHeaders({
  'Content-Type': 'application/json',
  'Authorization': 'Bearer token',
  'X-Custom-Header': 'value'
});

// Try to clear only Content-Type header
headers.clear((value, key) => key === 'Content-Type');

// Expected: Only Content-Type should be removed
// Actual: Authorization and X-Custom-Header are removed instead
console.log(headers.toJSON());
// Shows: { 'Content-Type': 'application/json' }
// Should show: { 'Authorization': 'Bearer token', 'X-Custom-Header': 'value' }
```

### Expected behavior

When calling `clear()` with a matcher function, it should remove headers that match the condition, not the ones that don't match. The current behavior is inverted from what would be expected.

Also, calling `clear()` without any arguments doesn't seem to clear all headers anymore.

### System Info
- axios version: latest
- Node version: 18.x

---
Repository: /testbed
