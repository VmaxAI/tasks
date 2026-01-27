# Bug Report

### Describe the bug

The `run()` method on `EffectScope` is completely broken after a recent update. When trying to execute a function within an effect scope, nothing happens - the function doesn't run at all and returns `undefined`.

### Reproduction

```js
import { effectScope } from 'vue'

const scope = effectScope()

const result = scope.run(() => {
  console.log('This should execute')
  return 42
})

console.log(result) // Expected: 42, Actual: undefined
// The function never executes
```

### Expected behavior

The `run()` method should:
1. Execute the provided function
2. Return the function's return value
3. Set the scope as active during execution

Currently it just returns `undefined` and doesn't execute anything.

### System Info
- Vue version: 3.x
- Node version: 18.x

This is breaking all my composables that rely on effect scopes. Any idea what might have caused this?

---
Repository: /testbed
