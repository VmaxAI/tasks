# Bug Report

### Describe the bug

After a recent update, effect scopes are not stopping properly. When calling `scope.stop()`, the scope remains active and effects/cleanups are not being executed. This causes memory leaks and prevents proper cleanup of reactive effects.

### Reproduction

```js
import { effectScope, ref, watchEffect } from 'vue'

const scope = effectScope()

scope.run(() => {
  const count = ref(0)
  watchEffect(() => {
    console.log('Count:', count.value)
  })
})

// This should stop all effects and cleanups
scope.stop()

// But the scope is still active
console.log(scope._active) // Expected: false, Actual: true
```

### Expected behavior

When `stop()` is called on an effect scope:
1. All effects should be stopped
2. All cleanup functions should be executed
3. Child scopes should be stopped recursively
4. The scope should be marked as inactive (`_active = false`)
5. Parent-child references should be cleaned up to prevent memory leaks

### System Info

- Vue version: 3.x
- Node: 18.x

The scope cleanup is critical for avoiding memory leaks in applications that dynamically create and destroy scopes. This is blocking our production deployment.

---
Repository: /testbed
