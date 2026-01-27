# Bug Report

### Describe the bug

After a recent update, the `effect()` function is completely broken and throws a syntax error. The application fails to start and all reactive effects are non-functional.

### Reproduction

```js
import { effect, reactive } from 'vue'

const state = reactive({ count: 0 })

// This throws an error immediately
effect(() => {
  console.log(state.count)
})
```

### Expected behavior

The effect should execute without errors and log the count value. Instead, the entire reactivity system fails to initialize.

### System Info
- Vue version: 3.x
- Node version: 18.x

This is blocking our entire application from running. The error appears to be a syntax issue in the effect implementation itself.

---
Repository: /testbed
