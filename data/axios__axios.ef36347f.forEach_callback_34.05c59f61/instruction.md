# Bug Report

### Describe the bug

When parsing HTTP headers with duplicate header names that should be ignored (like `age`, `authorization`, `content-length`, etc.), the parser is not properly filtering them out. The duplicate values are being concatenated together instead of being ignored as expected.

### Reproduction

```js
const parseHeaders = require('./parseHeaders');

const rawHeaders = `content-type: application/json
age: 100
age: 200
authorization: Bearer token1
authorization: Bearer token2`;

const parsed = parseHeaders(rawHeaders);

console.log(parsed.age); // Expected: "100", Actual: "100, 200"
console.log(parsed.authorization); // Expected: "Bearer token1", Actual: "Bearer token1, Bearer token2"
```

### Expected behavior

For headers listed in `ignoreDuplicateOf` (age, authorization, content-length, content-type, etag, expires, from, host, if-modified-since, if-unmodified-since, last-modified, location, max-forwards, proxy-authorization, referer, retry-after, user-agent), only the first occurrence should be kept and subsequent duplicates should be ignored.

The parsed object should contain:
- `age: "100"` (not `"100, 200"`)
- `authorization: "Bearer token1"` (not `"Bearer token1, Bearer token2"`)

### Additional context

This seems to have broken recently. The duplicate header filtering logic doesn't appear to be working correctly anymore.

---
Repository: /testbed
