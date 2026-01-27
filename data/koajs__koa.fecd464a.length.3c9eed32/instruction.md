# Bug Report

### Describe the bug

After a recent update, response body length is no longer being set correctly. When trying to send responses, the `Content-Length` header is missing even when explicitly setting the `length` property on the response object.

### Reproduction

```js
const response = // ... get response object

// Set the response body length
response.length = 1024

// Check headers
console.log(response.get('Content-Length'))
// Expected: '1024'
// Actual: undefined
```

The `length` setter appears to be completely non-functional. Setting `response.length` doesn't update the `Content-Length` header at all.

### Expected behavior

Setting `response.length` should automatically set the `Content-Length` header (unless `Transfer-Encoding` is already set).

### System Info
- Node version: 18.x
- Framework: Koa/Express

---
Repository: /testbed
