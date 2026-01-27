# Bug Report

### Describe the bug

I'm experiencing an issue with reactive Maps when using object keys. When I store a value using a reactive object as the key and then try to retrieve it using the raw (non-reactive) version of that same object, the retrieval returns `undefined` instead of the stored value.

### Reproduction

```js
const key = { id: 1 }
const reactiveKey = reactive(key)
const map = reactive(new Map())

// Store value with reactive key
map.set(reactiveKey, 'test value')

// Try to retrieve with raw key - doesn't work
console.log(map.get(key)) // Expected: 'test value', Actual: undefined

// Only works if we use the exact same reactive reference
console.log(map.get(reactiveKey)) // Works: 'test value'
```

### Expected behavior

The Map should be able to retrieve values using either the reactive key or its raw equivalent, since they represent the same underlying object. This is important for cases where you might not have direct access to the reactive wrapper but have the original object reference.

### System Info
- Vue version: 3.x
- Using reactive Maps with object keys

---
Repository: /testbed
