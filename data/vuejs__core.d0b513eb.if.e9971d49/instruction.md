# Bug Report

### Describe the bug

The compiler is not properly validating expressions in browser builds during development. It seems like the validation logic that should run in `__DEV__` mode for browser environments is being skipped, which could lead to invalid expressions being compiled without proper error reporting.

### Reproduction

```js
// In a browser dev build, this should trigger validation errors
// but currently passes through without validation

<template>
  <div>{{ invalidExpression() }}</div>
</template>
```

When compiling templates with potentially invalid expressions in the browser during development, the validation that should catch issues early is not being executed. This means errors that should be caught at compile time might only surface at runtime.

### Expected behavior

Expression validation should run in development mode for browser builds to catch invalid syntax and provide helpful error messages during development. The validator should be active when both `__BROWSER__` and `__DEV__` flags are true.

### System Info
- Vue version: 3.x
- Environment: Browser (development build)

---
Repository: /testbed
