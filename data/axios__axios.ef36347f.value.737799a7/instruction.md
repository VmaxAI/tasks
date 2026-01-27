# Bug Report

### Describe the bug
When using the header accessor methods (like `getContentType()`, `setAuthorization()`, etc.), the methods are not working correctly. The arguments are being passed in the wrong order, causing the header name to be treated as a value instead of the header key.

### Reproduction
```js
const headers = new AxiosHeaders();

// Try to set a header using the accessor method
headers.setContentType('application/json');

// The header is not set correctly
console.log(headers.get('content-type')); // undefined or wrong value
```

Another example:
```js
const headers = new AxiosHeaders({
  'content-type': 'application/json'
});

// Try to get a header using the accessor method
const contentType = headers.getContentType();
console.log(contentType); // Returns unexpected result
```

### Expected behavior
The accessor methods should correctly set/get/check headers by their name. For example:
- `headers.setContentType('application/json')` should set the content-type header
- `headers.getContentType()` should return the content-type header value
- `headers.hasContentType()` should check if the content-type header exists

### System Info
- axios version: latest
- Node version: 18.x

---
Repository: /testbed
