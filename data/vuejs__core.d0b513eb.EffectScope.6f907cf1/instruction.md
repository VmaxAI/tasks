# Bug Report

### Describe the bug

After a recent update, the `EffectScope` class appears to be completely broken. When trying to use effect scopes in my application, I'm getting errors about missing methods and properties.

### Reproduction

```js
import { effectScope } from 'vue'

const scope = effectScope()

// Try to run something in the scope
scope.run(() => {
  // ... some reactive code
})

// Later, try to clean up
scope.stop()
```

### Expected behavior

The effect scope should work normally - allowing me to run code within the scope context and properly clean up effects when calling `stop()`. This was working fine in the previous version.

### Additional context

This seems to have broken suddenly. The scope object exists but none of the methods seem to be available anymore. I'm also seeing issues with nested scopes not being tracked properly.

---
Repository: /testbed
