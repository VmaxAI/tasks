# Bug Report

### Describe the bug

After a recent update, reactivity tracking appears to be completely broken. Objects that were previously reactive are no longer triggering updates when their properties change. The entire reactivity system seems to have stopped working.

### Reproduction

```js
import { reactive, effect } from 'vue'

const state = reactive({
  count: 0
})

let dummy
effect(() => {
  dummy = state.count
})

console.log(dummy) // 0
state.count++
console.log(dummy) // Still 0, should be 1
```

The effect doesn't re-run when `state.count` changes. This is affecting all reactive operations in my application.

### Expected behavior

The effect should automatically re-run when `state.count` is modified, updating the `dummy` variable to reflect the new value.

### System Info
- Vue version: 3.x
- Node version: 18.x

This is a critical issue as it breaks the core reactivity functionality. Any reactive state changes are not being detected at all.

---
Repository: /testbed
