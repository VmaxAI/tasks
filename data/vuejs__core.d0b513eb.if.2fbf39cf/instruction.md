# Bug Report

### Describe the bug

The `onEffectCleanup` function is not executing properly when called within a reactive effect. The cleanup callback gets registered but doesn't run when the effect is cleaned up or re-executed.

### Reproduction

```js
import { effect, ref, onEffectCleanup } from '@vue/reactivity'

const count = ref(0)
let cleanupExecuted = false

effect(() => {
  console.log('Effect running, count:', count.value)
  
  onEffectCleanup(() => {
    cleanupExecuted = true
    console.log('Cleanup executed')
  })
})

// Trigger effect re-run
count.value++

// Expected: cleanupExecuted should be true
// Actual: cleanupExecuted is false - cleanup didn't run
console.log('Cleanup executed?', cleanupExecuted)
```

### Expected behavior

When an effect re-runs or is stopped, the cleanup function registered via `onEffectCleanup` should be invoked. In the example above, `cleanupExecuted` should be `true` after the effect re-runs.

### Additional context

This seems to have broken recently. The cleanup function is being registered but never actually called. This affects any code that relies on cleanup logic, like clearing timers, removing event listeners, or cleaning up subscriptions within effects.

---
Repository: /testbed
