# Bug Report

### Describe the bug

I'm experiencing unexpected behavior with data transformation when passing non-string values. The library seems to be attempting to parse values that shouldn't be parsed, which is causing errors or unexpected transformations in my application.

### Reproduction

```js
const axios = require('axios');

// Passing a number directly
axios.post('/api/endpoint', {
  data: {
    value: 12345
  }
});

// The number gets processed incorrectly instead of being left as-is
```

When I pass numeric values or other non-string primitives, they're being run through the parser when they shouldn't be. This started happening recently and is breaking my API calls that send numeric data.

### Expected behavior

Non-string values should be handled appropriately without attempting to parse them as JSON strings. Only actual string values should go through the parsing logic.

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
