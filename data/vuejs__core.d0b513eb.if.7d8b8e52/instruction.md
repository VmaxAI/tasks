# Bug Report

### Describe the bug

After a recent update, array reactivity seems to be completely broken. When modifying array elements by index, the reactive system doesn't trigger updates anymore. This is affecting all array operations in my application.

### Reproduction

```js
const state = reactive({
  items: [1, 2, 3, 4, 5]
})

// Modifying array element by index
state.items[2] = 99

// Expected: watchers/effects should trigger
// Actual: no reactivity updates occur
```

Also happens with computed properties that depend on array elements:

```js
const state = reactive({
  numbers: [10, 20, 30]
})

const sum = computed(() => {
  return state.numbers.reduce((a, b) => a + b, 0)
})

console.log(sum.value) // 60

state.numbers[1] = 100

console.log(sum.value) // Still 60, should be 140
```

### Expected behavior

Array index assignments should trigger reactivity updates just like they did before. Any watchers, computed properties, or effects that depend on the array should re-run when individual elements are modified.

### System Info
- Vue version: 3.x (latest)
- Node: 18.x

This is blocking my project as arrays are used extensively throughout the codebase. Any help would be greatly appreciated!

---
Repository: /testbed
