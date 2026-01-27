# Bug Report

### Describe the bug

After a recent update, the `EffectScope` class seems to be completely broken. The entire implementation has been replaced with what appears to be an unrelated algorithm for finding the smallest range in sorted lists. This is causing the reactivity system to fail completely.

### Reproduction

```js
import { EffectScope } from 'vue'

const scope = new EffectScope()

// Trying to use basic EffectScope functionality
scope.run(() => {
  // This should work but doesn't
})

// These methods are completely missing now
scope.pause()  // TypeError: scope.pause is not a function
scope.stop()   // TypeError: scope.stop is not a function
```

### Expected behavior

The `EffectScope` class should provide the standard reactivity scope management functionality including:
- `run()` method to execute functions within the scope
- `pause()` method to pause effects
- `stop()` method to stop and clean up effects
- Proper parent/child scope relationships

Instead, the class now contains a `smallestRange` function that has nothing to do with effect scopes.

### System Info
- Vue version: Latest from main branch
- Node: 18.x

This appears to be a severe regression that breaks the entire reactivity system. Any application using effect scopes will fail immediately.

---
Repository: /testbed
