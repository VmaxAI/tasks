# Bug Report

### Describe the bug

When iterating over reactive arrays using iterator methods like `values()`, `entries()`, or `keys()`, the values are not being wrapped correctly. This causes issues with nested reactive objects where changes aren't tracked properly during iteration.

### Reproduction

```js
const arr = reactive([{ count: 1 }, { count: 2 }])

for (const item of arr.values()) {
  console.log(item.count)
  // item should be reactive but isn't wrapped correctly
}
```

The iterator should wrap the values to maintain reactivity, but it seems like the wrapping logic isn't being applied during iteration.

### Expected behavior

When using array iterator methods on reactive arrays, each value yielded by the iterator should be properly wrapped to maintain reactivity tracking. Nested objects should remain reactive throughout the iteration process.

### System Info
- Vue version: 3.x
- Node version: 18.x

---
Repository: /testbed
