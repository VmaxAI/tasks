# Bug Report

### Describe the bug

I'm experiencing an issue with the Vue global config where accessing config properties always returns `undefined` instead of their actual values. This seems to affect all legacy config options when running in compatibility mode.

### Reproduction

```js
import { createApp } from 'vue'

const app = createApp({})

// Set a config value
app.config.someConfigOption = 'myValue'

// Try to read it back
console.log(app.config.someConfigOption) // Expected: 'myValue', Actual: undefined

// Even subsequent reads return undefined
console.log(app.config.someConfigOption) // Still undefined
```

### Expected behavior

When setting and reading config properties, the getter should return the stored value, not `undefined`. The first access should return the value that was set, and subsequent accesses should continue to return that value.

### System Info
- Vue version: 3.x (compat mode)
- Node version: 18.x

This is blocking our migration from Vue 2 to Vue 3 as we rely on reading these config values at runtime.

---
Repository: /testbed
