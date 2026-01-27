# Bug Report

### Describe the bug

After a recent update, array mutation methods like `push`, `pop`, `splice`, `shift`, `unshift` are completely broken and causing runtime errors. The application crashes when trying to use any of these methods on reactive arrays.

### Reproduction

```js
import { reactive } from 'vue'

const state = reactive({
  items: [1, 2, 3]
})

// This causes a runtime error
state.items.push(4)

// Same with other mutation methods
state.items.splice(0, 1)
state.items.pop()
```

### Expected behavior

Array mutation methods should work normally on reactive arrays without throwing errors. These are standard JavaScript array operations that should be supported.

### System Info
- Vue version: 3.x
- Node: 18.x

This is a critical issue as it breaks basic array functionality. Any help would be appreciated!

---
Repository: /testbed
