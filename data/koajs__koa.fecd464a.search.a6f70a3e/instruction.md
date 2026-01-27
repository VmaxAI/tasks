# Bug Report

### Describe the bug

The `search` setter on the request object appears to be broken. When trying to set the search/query string on a request, it's not working as expected and causing issues with URL manipulation.

### Reproduction

```js
const request = require('./lib/request');

// Try to set the search property
request.search = '?foo=bar&baz=qux';

// The querystring should be updated but it's not working
console.log(request.querystring); // Expected: 'foo=bar&baz=qux'
```

### Expected behavior

Setting `request.search` should update the `querystring` property accordingly. This is a standard way to manipulate query parameters in the request object.

### Additional context

This seems to have broken recently. The setter for the `search` property doesn't seem to be functioning at all. Any code that relies on setting `request.search` to modify query strings will fail.

---
Repository: /testbed
