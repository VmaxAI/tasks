# Bug Report

### Describe the bug

Component instances are incorrectly detected as reactive objects when checking with `isReactive()`. This causes issues when trying to determine if a value is a reactive proxy, as component public instances return `true` for `isReactive()` checks even though they shouldn't be treated as reactive objects.

### Reproduction

```js
import { getCurrentInstance, isReactive } from 'vue'

export default {
  setup() {
    const instance = getCurrentInstance()
    
    // This incorrectly returns true
    console.log(isReactive(instance.proxy))
    // Expected: false
    // Actual: true
  }
}
```

### Expected behavior

`isReactive()` should return `false` when checking component public instances, as they are not standard reactive objects even though they use proxies internally.

### Additional context

This affects any code that needs to distinguish between actual reactive objects and component instances, particularly in utility functions or composables that handle different types of values differently.

---
Repository: /testbed
