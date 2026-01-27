# Bug Report

### Describe the bug

The `warning()` utility function is now throwing errors instead of just logging them to the console. This breaks my application when warnings are triggered during development.

### Reproduction

```js
import warning from './utils/warning'

// This now throws an error and crashes the app
warning('Something went wrong')

// Expected: warning should be logged to console but execution continues
// Actual: error is thrown and execution stops
```

### Expected behavior

The warning function should log messages to the console without interrupting code execution. Previously, warnings would appear in the console but the application would continue running normally. Now any warning causes the entire application to crash.

### System Info
- Version: latest
- Environment: Development

This is making it very difficult to debug issues since the app crashes immediately when a warning is encountered instead of just showing the warning message.

---
Repository: /testbed
