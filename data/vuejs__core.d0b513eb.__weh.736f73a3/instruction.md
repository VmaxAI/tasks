# Bug Report

### Lifecycle hooks causing tracking issues

I've noticed some strange behavior with lifecycle hooks after a recent update. It seems like reactive dependencies are being tracked inside lifecycle hooks when they shouldn't be, which is causing some unexpected side effects.

### Reproduction

```js
import { ref, watchEffect, onMounted } from 'vue'

export default {
  setup() {
    const count = ref(0)
    
    onMounted(() => {
      // This shouldn't create a reactive dependency
      // but it seems to be tracked now
      console.log(count.value)
    })
    
    watchEffect(() => {
      count.value++
    })
    
    return { count }
  }
}
```

When the component mounts, the `watchEffect` triggers repeatedly because the access to `count.value` inside `onMounted` is being tracked as a dependency. This creates an infinite loop situation.

### Expected behavior

Reactive tracking should be disabled inside lifecycle hooks to prevent them from accidentally creating dependencies. The hooks should be able to access reactive values without those accesses being tracked by effects.

### System Info
- Vue version: 3.x
- Node: 18.x

This is causing issues in production where lifecycle hooks interact with reactive state. Any help would be appreciated!

---
Repository: /testbed
