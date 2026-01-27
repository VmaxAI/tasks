# Bug Report

### Describe the bug

After a recent update, the response object's `length` property is completely broken. When trying to access `response.length`, I'm getting undefined or errors instead of the expected content length value.

### Reproduction

```js
const response = {
  headers: {
    'content-length': '1234'
  },
  body: 'test content'
}

// This should return the content length but doesn't work anymore
console.log(response.length) // undefined or error
```

Also tried with different body types:

```js
// With Buffer
response.body = Buffer.from('hello world')
console.log(response.length) // Should return 11, but broken

// With JSON object
response.body = { foo: 'bar' }
console.log(response.length) // Should calculate JSON string length, but broken
```

### Expected behavior

The `length` getter should:
1. Return the parsed Content-Length header value if present
2. Calculate length from body content (string, Buffer, or JSON) if no header is set
3. Return undefined for streams

This was working fine before the latest update. Now it seems like the entire length calculation logic has been replaced with something completely unrelated.

### System Info
- Node version: 18.x
- Framework: Koa/Express middleware

---
Repository: /testbed
