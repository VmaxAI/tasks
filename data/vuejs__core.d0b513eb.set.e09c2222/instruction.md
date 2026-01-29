# Bug Report

### Describe the bug

When using `useModel()` with a setter transform, the component doesn't update correctly in certain scenarios. Specifically, when the transformed value emitted to the parent is the same as the previous emitted value, but the input value itself has changed, the local state gets out of sync.

### Reproduction

```js
const model = useModel(props, 'value', {
  set: (val) => {
    // Transform input value
    return Math.max(0, val)
  }
})

// Set to -5, which gets transformed to 0
model.value = -5  // emits 0

// Set to -10, which also gets transformed to 0
model.value = -10 // emits 0 again

// The local input state is now out of sync
// Expected: input shows -10
// Actual: input shows -5 (stale value)
```

### Expected behavior

Even when the emitted value to the parent is the same, if the actual input value has changed, the local state should still update to reflect the new input value. The component should trigger an update to keep the local state in sync.

### System Info
- Vue version: 3.x

This seems related to the logic that handles cases where the setter transforms values before emitting them to the parent.

---
Repository: /testbed
