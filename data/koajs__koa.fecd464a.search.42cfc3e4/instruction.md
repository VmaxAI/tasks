# Bug Report

### Describe the bug

The `search` setter on the request object appears to be broken or missing. When trying to set the search property, it doesn't work as expected and the querystring is not being updated properly.

### Reproduction

```js
const request = require('./lib/request');

// Try to set the search property
request.search = '?foo=bar';

// Expected: querystring should be set to '?foo=bar'
// Actual: search setter doesn't exist or doesn't work
```

### Expected behavior

Setting `request.search` should update the `querystring` property internally. This was working in previous versions but seems to have regressed.

### Additional context

This is blocking URL query parameter handling in our application. The setter was definitely present before but now seems to be missing from the codebase.

---
Repository: /testbed
