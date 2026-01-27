# Bug Report

### Describe the bug
When parsing HTTP headers, header names are being incorrectly extracted and include the colon character. This causes header lookups to fail and headers to not be properly parsed.

### Reproduction
```js
const rawHeaders = 'content-type: application/json\nauthorization: Bearer token123';
const parsed = parseHeaders(rawHeaders);

console.log(parsed);
// Expected: { 'content-type': 'application/json', 'authorization': 'Bearer token123' }
// Actual: { 'content-type:': 'application/json', 'authorization:': 'Bearer token123' }

// Header lookup fails because keys include the colon
console.log(parsed['content-type']); // undefined
console.log(parsed['content-type:']); // 'application/json'
```

### Expected behavior
Header names should be extracted without the trailing colon character. The parsed object should use clean header names as keys (e.g., `'content-type'` not `'content-type:'`).

### Additional context
This appears to affect all headers being parsed. The colon is being included in the key extraction which breaks standard header name lookups.

---
Repository: /testbed
