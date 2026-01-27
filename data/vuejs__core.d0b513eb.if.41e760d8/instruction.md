# Bug Report

### Describe the bug

Reactivity updates are not triggering at all after a recent change. When modifying reactive properties, the UI doesn't re-render and computed values don't update. It seems like the entire reactivity system has stopped working.

### Reproduction

```js
import { reactive, watchEffect } from 'vue'

const state = reactive({
  count: 0
})

watchEffect(() => {
  console.log('Count:', state.count)
})

// This should trigger the watchEffect, but nothing happens
state.count = 1
```

Expected: Console should log "Count: 1"
Actual: Nothing happens, the watchEffect doesn't run

This also affects computed properties:

```js
import { reactive, computed } from 'vue'

const state = reactive({
  firstName: 'John',
  lastName: 'Doe'
})

const fullName = computed(() => {
  return `${state.firstName} ${state.lastName}`
})

console.log(fullName.value) // 'John Doe'

state.firstName = 'Jane'
console.log(fullName.value) // Still 'John Doe', should be 'Jane Doe'
```

### Expected behavior

Reactive properties should trigger updates when modified. Watchers and computed properties should respond to changes.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
