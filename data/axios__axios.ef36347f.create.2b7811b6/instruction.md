# Bug Report

### Issue with instance.create() not respecting custom configuration

I'm experiencing an issue where creating a new axios instance using `instance.create()` doesn't properly apply the custom configuration passed to it. The new instance seems to ignore the configuration parameter and just uses the default config instead.

### Reproduction

```js
const customInstance = axios.create({
  baseURL: 'https://api.example.com',
  timeout: 5000
});

// Create another instance with different config
const anotherInstance = customInstance.create({
  baseURL: 'https://api.different.com',
  timeout: 10000
});

// Expected: anotherInstance should use 'https://api.different.com'
// Actual: anotherInstance uses 'https://api.example.com' (parent's config)
console.log(anotherInstance.defaults.baseURL); // Wrong baseURL
console.log(anotherInstance.defaults.timeout);  // Wrong timeout
```

### Expected behavior

When calling `.create()` on an existing axios instance with new configuration, the new instance should merge the parent's defaults with the provided config, not just duplicate the parent's configuration.

### Actual behavior

The new instance created via `.create()` completely ignores the `instanceConfig` parameter and just copies the parent instance's configuration.

This makes it impossible to create variations of an axios instance with different settings, which was working in previous versions.

---
Repository: /testbed
