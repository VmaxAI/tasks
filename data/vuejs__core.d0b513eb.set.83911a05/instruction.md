# Bug Report

### Describe the bug

After a recent update, I'm getting a strange error when trying to modify properties on readonly reactive objects. Instead of the expected warning message, the application crashes with a `TypeError` saying that the `set` method is not defined or something similar.

### Reproduction

```js
import { readonly, reactive } from 'vue'

const state = reactive({
  count: 0,
  user: {
    name: 'John'
  }
})

const readonlyState = readonly(state)

// This should show a warning but instead crashes
readonlyState.count = 10
```

### Expected behavior

When attempting to set a property on a readonly object, it should:
1. Display a warning in development mode (like it used to)
2. Prevent the modification
3. Not crash the application

The warning message should be something like: `Set operation on key "count" failed: target is readonly.`

### System Info
- Vue version: 3.x
- Environment: Development mode

This was working fine before, not sure what changed but it's breaking my application now when I accidentally try to mutate readonly state.

---
Repository: /testbed
