# Bug Report

### Describe the bug

After a recent update, the reactive system appears to be completely broken. When trying to create reactive objects or modify reactive state, the application crashes immediately with syntax errors.

### Reproduction

```js
import { reactive } from 'vue'

const state = reactive({
  count: 0,
  nested: {
    value: 'test'
  }
})

// Any attempt to use reactive state fails
state.count++
```

### Expected behavior

The reactive system should work as normal - creating reactive proxies and tracking changes to properties.

### System Info
- Vue version: 3.x
- Node version: 18.x

### Additional context

This seems to have started happening after the latest commit. The error messages suggest there's invalid syntax in the reactivity core files. Everything was working fine in the previous version.

---
Repository: /testbed
