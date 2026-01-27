# Bug Report

### Describe the bug
After a recent update, reactive state changes are no longer triggering updates. When I modify reactive properties, the UI doesn't re-render and computed values don't recalculate. It seems like the entire reactivity system has stopped working.

### Reproduction
```js
import { reactive, computed, watchEffect } from 'vue'

const state = reactive({
  count: 0
})

const doubled = computed(() => state.count * 2)

watchEffect(() => {
  console.log('Count:', state.count)
})

// This should trigger the watchEffect and update computed
state.count++

// Expected: watchEffect runs and logs "Count: 1"
// Expected: doubled.value should be 2
// Actual: Nothing happens, no updates are triggered
```

### Expected behavior
Modifying reactive properties should trigger:
- watchEffect callbacks to run
- computed values to recalculate
- components to re-render

But currently nothing is being triggered when reactive state changes.

### System Info
- Vue version: 3.x
- This started happening after the latest update

---
Repository: /testbed
