# Bug Report

### Describe the bug

When there's a configuration validation error in my Docusaurus site, the error message formatting appears broken. The accumulated error messages are not displaying properly - I'm only seeing a period (`.`) instead of the actual error details, and it seems like the wrong error types are being included in the output.

### Reproduction

1. Create a Docusaurus config with invalid/unknown configuration options
2. Try to build or start the dev server
3. Observe the validation error message

For example, with a config like:
```js
module.exports = {
  title: 'My Site',
  unknownOption: 'test',
  anotherBadOption: 123,
  // ... other config
}
```

### Expected behavior

The validation error should show a clear, formatted list of all configuration errors with proper messages. Instead, the error output seems incomplete or incorrectly formatted - showing just a period and potentially filtering out the wrong error types.

### System Info
- Docusaurus version: latest
- Node version: 18.x

---
Repository: /testbed
