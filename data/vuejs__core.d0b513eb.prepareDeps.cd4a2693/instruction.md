# Bug Report

### Describe the bug

I'm experiencing an issue with reactive effects where the first dependency in a subscriber's dependency chain is not being properly invalidated during re-evaluation. This causes stale data to persist when effects are re-run.

### Reproduction

```js
import { reactive, effect } from '@vue/reactivity'

const state = reactive({
  count: 0,
  multiplier: 2
})

let result = 0
effect(() => {
  // Both dependencies should be tracked
  result = state.count * state.multiplier
})

console.log(result) // 0

// Update the first tracked dependency
state.count = 5
console.log(result) // Expected: 10, but may show stale value

// Update the second tracked dependency
state.multiplier = 3
console.log(result) // Works correctly: 15
```

The issue seems to occur specifically with the first dependency that gets tracked in an effect. Subsequent dependencies work as expected, but the initial one doesn't get properly marked for invalidation.

### Expected behavior

All dependencies tracked by an effect should be properly invalidated and re-evaluated when their values change, regardless of their position in the dependency chain.

### System Info
- @vue/reactivity version: latest
- Node version: 18.x

---
Repository: /testbed
