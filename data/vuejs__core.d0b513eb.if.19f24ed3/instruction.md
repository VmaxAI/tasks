# Bug Report

### Describe the bug

I'm encountering an issue with `onEffectCleanup()` where the cleanup function is not being invoked correctly. When I register a cleanup function inside an effect, it doesn't execute as expected when the effect re-runs or is stopped.

### Reproduction

```js
import { effect, ref, onEffectCleanup } from '@vue/reactivity'

const count = ref(0)
let cleanupCalled = false

effect(() => {
  count.value
  
  onEffectCleanup(() => {
    cleanupCalled = true
    console.log('Cleanup executed')
  })
})

// Trigger effect re-run
count.value++

// Expected: cleanupCalled should be true
// Actual: cleanupCalled is false, cleanup never runs
console.log('Cleanup was called:', cleanupCalled)
```

### Expected behavior

The cleanup function should be called when the effect re-runs or when the effect is stopped. In the example above, changing `count.value` should trigger the cleanup function before the effect runs again.

### System Info
- @vue/reactivity version: latest
- Node version: 18.x

---
Repository: /testbed
