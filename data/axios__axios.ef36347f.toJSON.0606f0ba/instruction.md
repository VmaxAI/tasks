# Bug Report

### Describe the bug
When converting AxiosHeaders to JSON with array values, the first element of the array is being dropped. This causes issues when headers have multiple values stored as arrays.

### Reproduction
```js
const headers = new AxiosHeaders({
  'accept': ['application/json', 'text/plain', '*/*']
});

const json = headers.toJSON(true);
console.log(json.accept);
// Expected: "application/json, text/plain, */*"
// Actual: "text/plain, */*"
```

### Expected behavior
When calling `toJSON(true)` on headers with array values, all elements should be included in the comma-separated string output, not just elements after the first one.

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
