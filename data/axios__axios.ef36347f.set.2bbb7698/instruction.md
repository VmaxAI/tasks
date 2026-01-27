# Bug Report

### Describe the bug

I'm experiencing an issue with setting headers in Axios where headers with `false` values are being overwritten unexpectedly. When I set a header to `false` (to explicitly disable it), subsequent calls to `set()` with the same header name replace the `false` value even when I don't want them to.

### Reproduction

```js
const headers = new AxiosHeaders();

// Set a header to false to explicitly disable it
headers.set('X-Custom-Header', false);

// Try to set the same header again without rewrite flag
headers.set('X-Custom-Header', 'some-value');

// Expected: header should still be false
// Actual: header is now 'some-value'
```

### Expected behavior

When a header is explicitly set to `false`, it should not be overwritten by subsequent `set()` calls unless the `rewrite` parameter is explicitly set to `true`. This is important for cases where we want to explicitly disable certain headers and prevent them from being accidentally re-enabled.

The current behavior seems inconsistent - headers set to `false` should be treated as intentionally disabled and protected from accidental overwrites, similar to how other falsy values might be handled.

### System Info
- axios version: latest
- Node version: 18.x

---
Repository: /testbed
