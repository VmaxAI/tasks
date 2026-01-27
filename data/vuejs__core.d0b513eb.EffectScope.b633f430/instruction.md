# Bug Report

### Describe the bug

After a recent update, effect scopes are completely broken. When trying to use `effectScope()`, the application crashes immediately. It looks like the `EffectScope` class implementation got corrupted or truncated somehow.

### Reproduction

```js
import { effectScope } from 'vue'

const scope = effectScope()

scope.run(() => {
  // Any code here causes a crash
  console.log('test')
})
```

### Expected behavior

The effect scope should execute the function passed to `run()` without errors. Effect scopes should work as they did before, allowing proper cleanup and management of reactive effects.

### Additional context

This appears to affect all effect scope functionality including:
- Creating new scopes
- Running functions within a scope
- Stopping scopes
- Nested scopes

The application won't even start up if effect scopes are used anywhere in the codebase. This is a critical issue that blocks usage of the library.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
