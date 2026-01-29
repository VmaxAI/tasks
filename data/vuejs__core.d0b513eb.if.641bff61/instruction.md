# Bug Report

### Describe the bug

I'm experiencing an issue with `watch()` where the `depth` option doesn't seem to be working correctly. When I set `depth: 0` to only watch the top-level properties of an object, the watcher still triggers on nested property changes. Similarly, objects marked with `ReactiveFlags.SKIP` are being traversed when they shouldn't be.

### Reproduction

```js
import { reactive, watch } from 'vue'

const state = reactive({
  count: 0,
  nested: {
    value: 1
  }
})

// This should only watch top-level properties (depth: 0)
watch(
  () => state,
  (newVal) => {
    console.log('Changed:', newVal)
  },
  { deep: true, depth: 0 }
)

// Changing nested property still triggers the watcher
state.nested.value = 2  // This shouldn't trigger with depth: 0
```

### Expected behavior

When `depth: 0` is specified, the watcher should only track changes to immediate properties of the watched object, not nested properties. The traversal should stop at depth 0 and not go deeper into the object tree.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
