# Bug Report

### Describe the bug

I'm experiencing an issue where reactive dependencies are not being tracked correctly. When I create computed properties or effects that depend on reactive state, the dependencies don't seem to be updating properly and I'm getting stale values or missing updates.

### Reproduction

```js
import { reactive, computed, effect } from '@vue/reactivity'

const state = reactive({ count: 0 })

const double = computed(() => state.count * 2)

console.log(double.value) // 0

state.count = 5

console.log(double.value) // Expected: 10, but getting incorrect value
```

Also seeing issues with effects not running when they should:

```js
const state = reactive({ value: 1 })

let result = 0
effect(() => {
  result = state.value * 2
})

console.log(result) // 2

state.value = 10
// Effect doesn't seem to re-run properly
console.log(result) // Expected: 20, but not updating correctly
```

### Expected behavior

Computed properties and effects should properly track their dependencies and update when the reactive state changes. The dependency tracking system should maintain the correct order of subscriptions.

### System Info
- @vue/reactivity version: latest
- Node.js version: 18.x

This seems to have started happening recently. The reactivity system appears to be broken in some fundamental way with how it manages subscriptions.

---
Repository: /testbed
