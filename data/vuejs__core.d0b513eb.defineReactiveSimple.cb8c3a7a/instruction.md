# Bug Report

### Describe the bug

I'm experiencing an issue with Vue 2 compatibility mode where reactive properties defined using `Vue.set()` or similar mechanisms are not tracking dependencies correctly. When accessing these reactive properties in computed properties or watchers, the reactivity system doesn't seem to establish the proper dependency relationship.

### Reproduction

```js
import { reactive } from 'vue'

const obj = {}
Vue.set(obj, 'count', 0)

// Create a computed that depends on obj.count
const doubled = computed(() => obj.count * 2)

console.log(doubled.value) // 0

// Update the value
obj.count = 5

// The computed doesn't update as expected
console.log(doubled.value) // Still 0, should be 10
```

### Expected behavior

When a reactive property is accessed, the reactivity system should track it using the property key, so that any computed properties or watchers depending on it will be notified when the property changes.

### System Info
- Vue version: 3.x (compat mode)
- Using Vue 2 compatibility features

---
Repository: /testbed
