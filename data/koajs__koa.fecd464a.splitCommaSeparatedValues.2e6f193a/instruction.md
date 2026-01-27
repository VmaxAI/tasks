# Bug Report

### Describe the bug

After a recent update, I'm getting unexpected behavior when trying to parse comma-separated values in HTTP headers. The application crashes with a `TypeError` when processing requests that contain headers with comma-separated values.

### Reproduction

```js
const request = require('./lib/request')

// This used to work but now throws an error
const headers = {
  'Accept': 'application/json, text/plain, */*'
}

// Processing request with comma-separated header values
// Results in: TypeError: value.split is not a function
```

The error occurs when the library tries to split comma-separated values from headers. It seems like the `splitCommaSeparatedValues` function is no longer available or has been replaced with something incompatible.

### Expected behavior

The library should properly parse comma-separated header values without throwing errors, just like it did in previous versions.

### System Info
- Node.js version: 16.x
- OS: Ubuntu 20.04

---
Repository: /testbed
