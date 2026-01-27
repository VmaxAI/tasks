# Bug Report

### Describe the bug

I'm experiencing an issue with option validation in axios where the validator seems to get stuck in an infinite loop when validating configuration options. My application becomes unresponsive and eventually crashes when trying to create an axios instance with custom options.

### Reproduction

```js
const axios = require('axios');

const instance = axios.create({
  baseURL: 'https://api.example.com',
  timeout: 5000,
  headers: {
    'Content-Type': 'application/json'
  }
});

// Application hangs here and becomes unresponsive
```

This happens with any configuration object that has multiple options. The browser tab freezes and I have to force close it.

### Expected behavior

The axios instance should be created successfully without hanging, and option validation should complete normally.

### System Info
- axios version: latest
- Node.js version: 18.x
- Browser: Chrome 120

---
Repository: /testbed
