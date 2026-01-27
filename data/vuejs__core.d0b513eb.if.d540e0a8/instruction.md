# Bug Report

### Describe the bug

I'm experiencing an issue with array reactivity where certain operations on reactive arrays seem to cause unnecessary performance overhead or potential issues with dependency tracking. 

When working with reactive arrays and performing operations that modify array elements by index, I've noticed some unexpected behavior related to iteration tracking. It appears that the system is attempting to trigger array iteration dependencies even when there are no active watchers/effects that actually depend on array iteration.

### Reproduction

```js
const state = reactive({
  items: [1, 2, 3, 4, 5]
})

// Modifying array by index
state.items[2] = 10

// Or using numeric keys
state.items[0] = 100
```

When modifying array elements by numeric index, the reactivity system seems to be checking/running iteration dependencies regardless of whether any effects are actually watching for array iteration changes. This could potentially cause performance issues or unexpected behavior in larger applications.

### Expected behavior

The reactivity system should only trigger iteration-related effects when there are actual dependencies that need to be notified. If there are no effects watching for array iteration changes, those dependency checks/runs should be skipped entirely.

### System Info
- Vue version: 3.x
- Node: 18.x

---
Repository: /testbed
