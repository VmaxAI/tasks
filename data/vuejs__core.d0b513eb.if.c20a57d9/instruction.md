# Bug Report

### Describe the bug

After a recent update, reactive effects are no longer being notified properly when dependencies change. The reactivity system seems to have completely broken - components aren't updating when state changes, and computed properties aren't recalculating.

### Reproduction

```js
import { reactive, effect } from 'vue'

const state = reactive({ count: 0 })

effect(() => {
  console.log('Count:', state.count)
})

// This should trigger the effect, but nothing happens
state.count++
```

Expected: The effect callback should run and log the new count value
Actual: Nothing happens, the effect is never triggered

### Additional context

This appears to affect all reactive effects across the board. Even simple examples that were working before are now completely broken. The reactivity system doesn't seem to be tracking or notifying effects at all.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
