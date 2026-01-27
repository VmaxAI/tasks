# Bug Report

### Describe the bug

When using Vue 2 compatibility mode with reactive properties, setting a property value and immediately reading it back returns the old value instead of the newly set value. The reactivity system triggers updates correctly, but the getter returns stale data during the same synchronous execution.

### Reproduction

```js
const obj = {}
Vue.set(obj, 'count', 0)

obj.count = 5
console.log(obj.count) // Expected: 5, Actual: 0

// After a tick, the value is correct
setTimeout(() => {
  console.log(obj.count) // Shows: 5
}, 0)
```

### Expected behavior

When setting a reactive property, the getter should immediately return the new value, not the old cached value. The property should be readable with the updated value in the same synchronous context.

### System Info
- Vue version: 3.x (compat mode)
- Node version: 18.x

---
Repository: /testbed
