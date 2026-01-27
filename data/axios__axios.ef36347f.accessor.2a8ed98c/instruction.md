# Bug Report

### Describe the bug
After a recent update, custom header accessors are not being created properly. When trying to use header accessors that should be dynamically added, they're not available on the AxiosHeaders prototype.

### Reproduction
```js
const { AxiosHeaders } = require('axios');

// Try to add a custom header accessor
AxiosHeaders.accessor('X-Custom-Header');

const headers = new AxiosHeaders();

// This should work but the accessor is not available
headers['x-custom-header'] = 'test-value';
console.log(headers['x-custom-header']); // Expected: 'test-value', Actual: undefined
```

### Expected behavior
The `accessor()` method should create getter/setter properties on the AxiosHeaders prototype for the specified header names. After calling `AxiosHeaders.accessor('X-Custom-Header')`, I should be able to get and set that header using the normalized property name.

### System Info
- axios version: latest
- Node.js version: 18.x

This seems to have broken after a recent change. The default headers like 'Content-Type' and 'Authorization' still work fine, but any custom headers added via `accessor()` don't get their accessors created.

---
Repository: /testbed
