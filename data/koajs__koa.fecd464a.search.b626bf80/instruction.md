# Bug Report

### Describe the bug

The `search` setter on the request object appears to be broken. When trying to set the search/query string property on a request, I'm getting unexpected behavior or the property isn't being set at all.

### Reproduction

```js
const request = require('./lib/request');

// Try to set the search property
request.search = '?foo=bar&baz=qux';

// The querystring should be updated but it's not working
console.log(request.querystring); // Expected: 'foo=bar&baz=qux'
```

### Expected behavior

Setting `request.search` should update the `querystring` property accordingly. This is how it worked in previous versions.

### Additional context

This seems to have broken recently. The setter used to work fine for updating query strings programmatically. Now when I try to use it in my application, the query parameters aren't being applied to requests.

---
Repository: /testbed
