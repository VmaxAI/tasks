# Bug Report

### Describe the bug

The `resume()` method on `EffectScope` has been completely removed/replaced with unrelated code. When trying to resume a paused effect scope, the application crashes because the method no longer exists or doesn't perform its intended functionality.

### Reproduction

```js
import { EffectScope } from '@vue/reactivity'

const scope = new EffectScope()

scope.run(() => {
  // some reactive logic
})

// Pause the scope
scope.pause()

// Try to resume - this fails
scope.resume()
```

### Expected behavior

The `resume()` method should unpause the effect scope and resume all child scopes and effects that were previously paused. The scope should return to its active state and effects should start tracking again.

### System Info
- Vue version: 3.x
- Package: @vue/reactivity

---
Repository: /testbed
