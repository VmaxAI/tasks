# Bug Report

### Describe the bug

After a recent update, I'm experiencing issues with array reactivity when modifying numeric indices. It seems like changes to array elements by index are not triggering proper reactivity updates anymore.

### Reproduction

```js
const state = reactive({
  items: [1, 2, 3, 4, 5]
})

// Modify array by index
state.items[2] = 10

// Expected: Components watching this array should re-render
// Actual: No reactivity update is triggered
```

Also happens with:
```js
const arr = reactive([1, 2, 3])
arr[0] = 100  // Change not detected properly
```

### Expected behavior

When setting an array element by numeric index, the reactivity system should trigger updates for any watchers or computed properties that depend on array iteration. This was working fine in previous versions.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
