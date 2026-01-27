# Bug Report

### Describe the bug

I'm getting incorrect parameter names in the error message when `MissingParamError` is thrown. Instead of showing the actual missing parameter names, the error message displays array indices.

### Reproduction

```js
const error = new MissingParamError(['userId', 'token']);
console.log(error.message);
// Expected: Missing params "userId", "token" make sure you pass the parameters in URL
// Actual: Missing params "0", "1" make sure you pass the parameters in URL
```

Also noticed that when I pass a single missing parameter with a secondary message, the secondary message is not being set:

```js
const error = new MissingParamError(['apiKey'], 'Please check your configuration');
console.log(error.secondaryMessage);
// Expected: 'Please check your configuration'
// Actual: undefined
```

### Expected behavior

The error message should display the actual parameter names (e.g., "userId", "token") instead of their array indices (e.g., "0", "1"). Additionally, the `secondaryMessage` should be set regardless of how many parameters are missing.

### System Info
- Node version: 18.x
- Package version: latest

---
Repository: /testbed
