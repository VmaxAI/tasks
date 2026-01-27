# Bug Report

### Describe the bug

I'm experiencing an issue with header filtering in axios. When trying to filter headers using a string filter, the matching logic seems to be inverted - it's checking if the filter string contains the header value instead of checking if the header value contains the filter string.

### Reproduction

```js
const headers = new AxiosHeaders({
  'Content-Type': 'application/json',
  'Authorization': 'Bearer token123'
});

// Trying to filter headers that contain 'json'
// This should match 'Content-Type' header but doesn't work correctly
const filtered = headers.filter((value, header) => {
  // Expected: check if value contains 'json'
  // Actual: seems to check if 'json' contains value
  return value.indexOf('json') !== -1;
});
```

The filtering doesn't return the expected results. If I'm looking for headers whose values contain a certain substring, the behavior is backwards.

### Expected behavior

When filtering headers with a string, it should check if the header **value** contains the filter string, not the other way around. For example, searching for headers containing "json" should match a header with value "application/json".

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
