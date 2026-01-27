# Bug Report

### Describe the bug

When creating a new axios instance using `axios.create()` with custom configuration, the config precedence seems to be reversed. The default config is overriding the instance-specific config instead of the other way around.

### Reproduction

```js
const instance = axios.create({
  baseURL: 'https://api.example.com',
  timeout: 5000
});

// The baseURL and timeout from the instance config should take precedence
// but they're being overridden by the default config
```

For example, if I set a custom `baseURL` when creating an instance, it gets replaced by the default axios config. This makes it impossible to properly configure individual instances.

### Expected behavior

When calling `axios.create(config)`, the provided config should override the default config, not the other way around. Instance-specific settings should have higher priority than defaults.

### System Info
- axios version: latest
- Node.js version: 18.x

---
Repository: /testbed
