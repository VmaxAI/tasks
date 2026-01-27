# Bug Report

### Describe the bug

The warning utility function is throwing uncaught errors instead of just logging warnings. This is causing the application to crash when warnings are triggered, which is not the expected behavior for a warning system.

### Reproduction

```js
import warning from './utils/warning'

// This throws an uncaught error and crashes the app
warning('This is a warning message')

// Expected: Should log a warning to console but NOT crash
```

### Expected behavior

The warning function should:
1. Log the warning message to the console
2. NOT throw an uncaught error that crashes the application
3. Warnings should be non-fatal - they should alert developers but allow the app to continue running

### Current behavior

The function is throwing an error that propagates up and crashes the application. Warnings should be informational only and not break execution flow.

### System Info
- Version: latest
- Environment: Development

---
Repository: /testbed
