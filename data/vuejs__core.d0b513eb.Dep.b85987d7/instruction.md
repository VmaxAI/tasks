# Bug Report

### Describe the bug

After a recent update, reactivity tracking appears to be completely broken. When modifying reactive state, components are not re-rendering at all. It seems like the dependency tracking system is not working.

### Reproduction

```js
import { reactive, effect } from 'vue'

const state = reactive({ count: 0 })

effect(() => {
  console.log('Count:', state.count)
})

// This should trigger the effect, but nothing happens
state.count = 1
```

The effect callback is only called once during initialization, but subsequent changes to `state.count` don't trigger any updates.

Same issue with computed properties:

```js
import { reactive, computed } from 'vue'

const state = reactive({ count: 0 })
const doubled = computed(() => state.count * 2)

console.log(doubled.value) // Works initially
state.count = 5
console.log(doubled.value) // Still shows old value, not 10
```

### Expected behavior

- Effects should re-run when their dependencies change
- Computed properties should recalculate when their source data changes
- Components should re-render when reactive state is modified

This is a critical issue as it breaks the core functionality of the reactivity system.

### System Info
- Vue version: 3.x (latest)
- Node: 18.x

---
Repository: /testbed
