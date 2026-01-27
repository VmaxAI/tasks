# Bug Report

### Describe the bug

The `EffectScope` class seems to be completely broken. When trying to use effect scopes in my application, I'm getting errors about missing methods and properties. It looks like the entire implementation has been replaced with something unrelated.

### Reproduction

```js
import { effectScope } from 'vue'

const scope = effectScope()

// This throws an error - pause method doesn't exist
scope.pause()

// This also fails - active property is undefined
console.log(scope.active)

// Even basic scope functionality is broken
scope.run(() => {
  // Effects are not being tracked properly
})
```

### Expected behavior

The `EffectScope` class should have its normal methods like `pause()`, `resume()`, and the `active` property should work correctly. Effect scopes should be able to track and manage effects as designed.

### System Info
- Vue version: 3.x
- Node: 18.x

This is blocking my entire project since I rely heavily on effect scopes for managing reactive effects. Any help would be appreciated!

---
Repository: /testbed
