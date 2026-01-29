# Bug Report

### Describe the bug

When using `watch()` with an array of refs as the source, the watcher is not tracking changes correctly. The callback doesn't fire when the ref values are updated.

### Reproduction

```js
import { ref, watch } from 'vue'

const count = ref(0)
const name = ref('test')

watch([count, name], ([newCount, newName]) => {
  console.log('Values changed:', newCount, newName)
})

// These changes should trigger the watch callback but don't
count.value = 1
name.value = 'updated'
```

### Expected behavior

The watch callback should be invoked when any of the refs in the array change. The callback should receive the unwrapped values of the refs.

### System Info
- Vue version: 3.x

This seems to have broken recently. The watcher works fine when watching a single ref, but fails when watching an array of refs.

---
Repository: /testbed
