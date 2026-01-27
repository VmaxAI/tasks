# Bug Report

### Describe the bug

I'm getting unexpected errors when trying to parse HTTP headers with comma-separated values. The application crashes with a `TypeError` saying that strings don't have a `split` method or something similar.

### Reproduction

```js
const request = require('./lib/request');

// Try to parse a header with comma-separated values
const acceptHeader = 'application/json, text/html, text/plain';

// This should work but throws an error instead
const values = request.parseCommaSeparatedHeader(acceptHeader, 2);
console.log(values); // Expected: ['application/json', 'text/html']
```

### Expected behavior

The function should split the comma-separated string and return an array of trimmed values. It worked fine in previous versions but now it's completely broken.

### System Info
- Node version: 18.x
- OS: Linux

This seems to have broken after a recent update. The code that handles comma-separated values appears to have been replaced with something completely unrelated (looks like Python code?). Not sure if this was an accidental commit or what happened here.

---
Repository: /testbed
