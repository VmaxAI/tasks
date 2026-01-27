# Bug Report

### Describe the bug

Array iteration tracking is broken after recent changes. When modifying array elements by index, computed properties or watchers that depend on array iteration are not being triggered properly.

### Reproduction

```js
const arr = reactive([1, 2, 3])

const sum = computed(() => {
  let total = 0
  for (const val of arr) {
    total += val
  }
  return total
})

console.log(sum.value) // 6

// This change should trigger the computed to re-run
arr[0] = 10

console.log(sum.value) // Still shows 6, but should be 15
```

### Expected behavior

When an array element is modified by index, any computed properties or effects that iterate over the array should be re-triggered and update accordingly.

### System Info
- Vue version: 3.x

---
Repository: /testbed
