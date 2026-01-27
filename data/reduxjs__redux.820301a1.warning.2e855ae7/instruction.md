# Bug Report

### Describe the bug

The `warning()` utility function is now throwing errors instead of just logging warnings to the console. This breaks error handling in production environments where warnings should be non-fatal.

### Reproduction

```js
import warning from './utils/warning'

try {
  // Some code that triggers a warning
  warning('This is a warning message')
  console.log('Execution continues')
} catch (e) {
  console.log('Error was thrown:', e.message)
}
```

### Expected behavior

The warning should be logged to the console but execution should continue normally. Warnings are meant to alert developers during development without breaking the application flow.

### Actual behavior

An error is thrown and caught by the outer try-catch, interrupting normal execution. This causes issues in production where warnings might be triggered but shouldn't crash the application.

### System Info
- Version: latest
- Environment: Node.js and browser

---
Repository: /testbed
