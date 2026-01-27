# Bug Report

### Describe the bug

After a recent update, reactive state changes are no longer triggering component updates. When I modify reactive properties, the UI doesn't re-render at all. It seems like the reactivity system has completely stopped working.

### Reproduction

```js
import { reactive, effect } from 'vue'

const state = reactive({ count: 0 })

effect(() => {
  console.log('Count:', state.count)
})

// This should trigger the effect but nothing happens
state.count++
```

The effect runs once initially but never runs again when `state.count` is modified. The console only shows "Count: 0" and never logs the updated value.

### Expected behavior

The effect should re-run whenever `state.count` changes, logging the new value to the console. Components that depend on reactive state should also re-render when the state changes.

### System Info
- Vue version: 3.x
- Node: 18.x

This is blocking our entire application from working. Any reactive state changes are completely ignored now.

---
Repository: /testbed
