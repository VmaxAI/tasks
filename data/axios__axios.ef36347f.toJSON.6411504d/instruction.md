# Bug Report

### Describe the bug
When serializing headers with `toJSON()` method, array values are being converted incorrectly. Instead of joining array elements with `', '` (comma and space), they're being converted using `.toString()` which produces a different output format.

### Reproduction
```js
const headers = new AxiosHeaders({
  'Accept': ['application/json', 'text/plain']
});

const json = headers.toJSON(true);
console.log(json.Accept);
// Current output: "application/json,text/plain" (no space after comma)
// Expected output: "application/json, text/plain" (with space after comma)
```

### Expected behavior
When `asStrings` is true, array header values should be joined with `', '` (comma followed by a space) to match standard HTTP header formatting conventions. The current behavior produces comma-separated values without spaces, which differs from the expected HTTP header format.

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
