# Bug Report

### Describe the bug

The `EffectScope` class seems to have lost critical functionality. When trying to use effect scopes in my application, I'm getting errors about missing methods and properties that should exist on the scope object.

### Reproduction

```js
import { effectScope } from 'vue'

const scope = effectScope()

// Trying to pause the scope
scope.pause()  // Error: pause is not a function

// Checking if scope is active
console.log(scope.active)  // undefined

// Trying to access parent scope
console.log(scope.parent)  // undefined
```

### Expected behavior

The `EffectScope` class should have:
- A `pause()` method to pause all effects and child scopes
- An `active` getter property to check if the scope is active
- Proper parent/child scope tracking
- A `cleanups` array for cleanup functions

Currently these are all missing or not working, which breaks any code that relies on pausing scopes or checking their active state.

### System Info
- Vue version: 3.x
- Node: 18.x

This is blocking my ability to properly manage effect scopes in my application. Any help would be appreciated!

---
Repository: /testbed
