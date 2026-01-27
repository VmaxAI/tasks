# Bug Report

### Describe the bug

When using the compatibility mode `filter` API, registering a filter function doesn't work correctly. The filter is not being stored in the context, and attempting to retrieve a registered filter always returns `undefined`.

### Reproduction

```js
import { createApp } from 'vue'

const app = createApp({})

// Register a filter
app.filter('capitalize', (value) => {
  return value.charAt(0).toUpperCase() + value.slice(1)
})

// Try to retrieve the filter
const filter = app.filter('capitalize')
console.log(filter) // Expected: the filter function, Actual: undefined
```

### Expected behavior

1. When calling `app.filter(name, fn)`, the filter should be registered and stored in the context
2. When calling `app.filter(name)` without the second argument, it should return the previously registered filter function
3. The filter should be available for use in templates

### System Info

- Vue version: 3.x (compat mode)
- Using migration build with FILTERS compatibility enabled

This seems like a regression as filters were working in the previous version. The registration appears to succeed (no errors), but the filters are not actually being stored.

---
Repository: /testbed
