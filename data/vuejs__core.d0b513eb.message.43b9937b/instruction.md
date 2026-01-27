# Bug Report

### Describe the bug

When triggering a deprecation warning for `PRIVATE_APIS` in the compatibility layer, the warning message appears malformed with incorrect quote placement and syntax.

### Reproduction

```js
import { configureCompat } from 'vue'

// Configure compat mode
configureCompat({
  MODE: 2
})

// Try to access a Vue 2 private API that triggers the deprecation warning
// The warning message will have malformed quotes
```

### Expected behavior

The deprecation warning should display a properly formatted message like:
```
"somePrivateAPI" is a Vue 2 private API that no longer exists in Vue 3. If you are seeing this warning only due to a dependency, you can suppress this warning via { PRIVATE_APIS: 'suppress-warning' }.
```

### Actual behavior

The warning message appears with broken syntax and misplaced quotes, making it difficult to read and understand.

### System Info
- Vue version: 3.x

---
Repository: /testbed
