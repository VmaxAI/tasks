# Bug Report

### Describe the bug

When calling `toJSON()` on AxiosHeaders with array values, the method is checking `utils.isArray()` on the wrong variable. It's checking `obj[header]` instead of the original `value`, which causes array headers to not be properly joined into comma-separated strings when the `asStrings` parameter is true.

### Reproduction

```js
const headers = new AxiosHeaders({
  'x-custom-header': ['value1', 'value2', 'value3']
});

const json = headers.toJSON(true);
console.log(json['x-custom-header']);
// Expected: 'value1, value2, value3'
// Actual: ['value1', 'value2', 'value3']
```

### Expected behavior

When `toJSON(true)` is called with array header values, they should be joined into a comma-separated string. The method should check if the original `value` is an array, not the `obj[header]` which hasn't been set yet.

### System Info
- axios version: latest
- Node version: 18.x

---
Repository: /testbed
