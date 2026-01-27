# Bug Report

### Describe the bug

I'm experiencing an issue with reactive `Set` objects where adding duplicate values triggers unnecessary reactivity updates. When I call `set.add()` with a value that already exists in the Set, the reactive system still fires change notifications even though the Set's state hasn't actually changed.

### Reproduction

```js
import { reactive, watchEffect } from 'vue'

const state = reactive(new Set([1, 2, 3]))

let updateCount = 0
watchEffect(() => {
  console.log('Set size:', state.size)
  updateCount++
})

// Adding a new value - this should trigger an update (expected)
state.add(4)  // updateCount = 2 ✓

// Adding an existing value - this triggers an update but shouldn't
state.add(4)  // updateCount = 3 ✗ (should still be 2)
state.add(4)  // updateCount = 4 ✗ (should still be 2)
```

### Expected behavior

According to the Set specification, calling `add()` with a value that already exists should be a no-op. The reactive system should only trigger updates when the Set's state actually changes (i.e., when a new unique value is added). Re-adding existing values should not cause watchers or computed properties to re-run.

### System Info
- Vue version: 3.x
- Node: 18.x

This is causing performance issues in my application where Sets are frequently updated with potentially duplicate values, leading to many unnecessary re-renders.

---
Repository: /testbed
