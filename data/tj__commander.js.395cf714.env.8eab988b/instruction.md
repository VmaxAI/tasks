# Bug Report

### Describe the bug

The `env()` method on `Option` is not working correctly. When I try to set an environment variable name for an option, the behavior is completely broken - it seems to overwrite the option name instead and doesn't return the option instance for chaining.

### Reproduction

```js
const option = new Option('-p, --port <number>', 'port number');
option.env('PORT');

// The option name gets overwritten instead of setting envVar
// Also can't chain methods anymore since it doesn't return this
```

### Expected behavior

The `env()` method should:
1. Set the `envVar` property to the provided name
2. Return the `Option` instance to allow method chaining

Currently it's setting the wrong property and returning the wrong value, breaking both the functionality and the fluent interface pattern used throughout the library.

### System Info
- Node version: 18.x
- Library version: latest

---
Repository: /testbed
