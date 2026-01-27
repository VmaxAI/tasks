# Bug Report

### Describe the bug

After a recent update, effect scopes are completely broken. When trying to use `effectScope()` to create a new scope and run effects within it, nothing works at all. The entire `EffectScope` class implementation seems to be missing or incomplete.

### Reproduction

```js
import { effectScope, reactive } from 'vue'

const scope = effectScope()
const state = reactive({ count: 0 })

scope.run(() => {
  // Try to run some reactive code
  watchEffect(() => {
    console.log(state.count)
  })
})

// This should work but doesn't
state.count++

// Trying to stop the scope also fails
scope.stop()
```

### Expected behavior

Effect scopes should work as documented:
- `scope.run()` should execute the function and track effects within the scope
- Effects created inside the scope should be reactive
- `scope.stop()` should properly clean up all effects in the scope
- Child scopes should be properly managed

### System Info
- Vue version: 3.x
- Node: 18.x

This is blocking our entire application since we rely heavily on effect scopes for managing reactive state cleanup. Any help would be appreciated!

---
Repository: /testbed
