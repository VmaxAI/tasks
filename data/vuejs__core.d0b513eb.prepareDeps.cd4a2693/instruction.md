# Bug Report

### Describe the bug

I'm experiencing an issue with reactivity where computed properties and effects are not re-running when their dependencies change. It seems like the dependency tracking is broken in certain scenarios.

### Reproduction

```js
import { reactive, computed, effect } from 'vue'

const state = reactive({ count: 0 })

const doubled = computed(() => state.count * 2)

console.log(doubled.value) // 0

state.count = 1

console.log(doubled.value) // Still shows 0, should be 2
```

Similarly with effects:

```js
const state = reactive({ value: 'initial' })

effect(() => {
  console.log('Effect running:', state.value)
})

// Effect runs once with 'initial'

state.value = 'updated'

// Effect doesn't re-run, even though the dependency changed
```

### Expected behavior

Computed properties should recalculate and effects should re-run when their reactive dependencies are modified.

### System Info

- Vue version: 3.x (latest from main branch)
- Node: v18.x

This is blocking my work on a project. Any help would be appreciated!

---
Repository: /testbed
