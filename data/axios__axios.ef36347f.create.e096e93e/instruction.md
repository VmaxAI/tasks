# Bug Report

### Describe the bug

When creating a new axios instance using `axios.create()` with custom configuration, the custom config seems to be ignored and only the default configuration is used. This is causing issues when trying to set custom baseURL, headers, or other instance-specific settings.

### Reproduction

```js
const instance = axios.create({
  baseURL: 'https://api.example.com',
  timeout: 5000,
  headers: {
    'Authorization': 'Bearer token123'
  }
});

// The instance doesn't use the custom config
// Instead it falls back to axios defaults
console.log(instance.defaults.baseURL); // Expected: 'https://api.example.com', Actual: undefined or default value
console.log(instance.defaults.timeout); // Expected: 5000, Actual: default timeout
```

### Expected behavior

The newly created instance should merge the provided configuration with the default configuration, and use the custom settings when making requests.

### System Info
- axios version: latest
- Node.js version: 18.x

This is breaking our application as we rely on multiple axios instances with different base URLs and authentication headers for different API endpoints.

---
Repository: /testbed
