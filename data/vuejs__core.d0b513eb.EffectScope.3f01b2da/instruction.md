# Bug Report

### Describe the bug

I'm encountering an issue where effect scopes appear to be completely broken. When trying to use `effectScope()`, the application crashes immediately. It seems like the entire `EffectScope` class implementation is missing or corrupted.

### Reproduction

```js
import { effectScope, ref } from 'vue'

const scope = effectScope()

scope.run(() => {
  const counter = ref(0)
  // ... do something
})

// This crashes the application
scope.stop()
```

Even basic operations like creating an effect scope and running a function inside it fail completely. The scope object doesn't have the expected methods.

### Expected behavior

Effect scopes should work normally - allowing you to create a scope, run effects within it, and stop/clean up all effects when needed. Child scopes should be properly managed and cleaned up when the parent scope is stopped.

### System Info
- Vue version: 3.x
- Node version: 18.x

This is blocking our entire application as we rely heavily on effect scopes for managing reactive state in composables. Any help would be greatly appreciated!

---
Repository: /testbed
