# Bug Report

### Describe the bug

Reactivity is completely broken after a recent change. When trying to add, delete, or modify properties on reactive objects (including Maps), the reactive system fails to trigger updates. This affects all reactive operations including array modifications and Map operations.

### Reproduction

```js
import { reactive, effect } from '@vue/reactivity'

// Case 1: Adding properties
const obj = reactive({})
let count = 0
effect(() => {
  Object.keys(obj).length
  count++
})
obj.newProp = 'value' // Should trigger effect, but doesn't

// Case 2: Map operations
const map = reactive(new Map())
let mapCount = 0
effect(() => {
  map.size
  mapCount++
})
map.set('key', 'value') // Should trigger effect, but doesn't

// Case 3: Array length changes
const arr = reactive([])
let arrCount = 0
effect(() => {
  arr.length
  arrCount++
})
arr.push(1) // Should trigger effect, but doesn't
```

### Expected behavior

- Adding new properties to reactive objects should trigger effects that depend on iteration
- Map.set() operations should trigger effects
- Array operations that modify length should trigger length-dependent effects
- DELETE operations should trigger iteration effects

### System Info

- Package: @vue/reactivity
- Version: latest

This seems like a critical regression as it breaks core reactivity functionality. The reactive system appears to be non-functional for ADD, DELETE, and SET operations.

---
Repository: /testbed
