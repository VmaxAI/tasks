# Bug Report

### Describe the bug

The `stringify` function in `search-params.js` appears to be completely broken. When I try to use it to convert an object to a query string, I'm getting errors about undefined functions or completely unexpected behavior.

### Reproduction

```js
const { stringify } = require('./lib/search-params')

const params = {
  name: 'test',
  id: 123,
  tags: ['foo', 'bar']
}

const result = stringify(params)
console.log(result)
// Expected: name=test&id=123&tags=foo&tags=bar
// Actual: Error or unexpected output
```

### Expected behavior

The function should convert JavaScript objects into URL-encoded query strings, handling both simple key-value pairs and arrays properly.

### Additional context

This seems to have broken recently. The stringify function was working fine before but now it's not functioning at all. Not sure what changed but it's blocking my work.

---
Repository: /testbed
