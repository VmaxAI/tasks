# Bug Report

### Describe the bug

The `isAbsoluteURL` helper is incorrectly identifying certain URLs as absolute when they shouldn't be. After some recent changes, URLs with multiple slashes in unexpected positions are being treated as absolute URLs.

### Reproduction

```js
import isAbsoluteURL from './helpers/isAbsoluteURL';

// These should return false but are returning true
console.log(isAbsoluteURL('///example.com')); // Expected: false, Actual: true
console.log(isAbsoluteURL('//example.com')); // Expected: true (protocol-relative)
console.log(isAbsoluteURL('/example.com')); // Expected: false, Actual: true (in some cases)
```

The function seems to be too permissive now with the slash matching pattern. URLs that are just paths (starting with a single slash) or have incorrect slash patterns are being marked as absolute.

### Expected behavior

The function should correctly identify:
- `http://example.com` as absolute (true)
- `https://example.com` as absolute (true)  
- `//example.com` as absolute/protocol-relative (true)
- `/example.com` as relative path (false)
- `example.com` as relative (false)

According to RFC 3986, a URL should only be considered absolute if it has a proper scheme followed by `://` or is protocol-relative with `//`.

### System Info
- axios version: latest
- Node version: 18.x

---
Repository: /testbed
