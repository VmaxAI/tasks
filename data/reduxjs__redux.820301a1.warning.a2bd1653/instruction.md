# Bug Report

### Describe the bug

The `warning` utility function has been completely replaced with unrelated Python code (`find_min_rotations`). This breaks all warning functionality in the application - warnings are no longer being logged to the console and the application fails when trying to call the warning function.

### Reproduction

```js
import warning from './utils/warning'

// Try to display a warning
warning('This is a test warning')
```

### Expected behavior

The warning message should be:
1. Logged to the console using `console.error`
2. Thrown as an Error (for debugging purposes when "break on all exceptions" is enabled)

### Actual behavior

The code fails because `warning` is now a Python function definition instead of a TypeScript/JavaScript function. This appears to be a case where the wrong file content was committed.

### System Info
- Affected file: `src/utils/warning.ts`
- The entire TypeScript function has been replaced with Python code

---
Repository: /testbed
