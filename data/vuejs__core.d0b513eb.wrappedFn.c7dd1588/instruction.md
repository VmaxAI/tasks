# Bug Report

### Describe the bug

I'm encountering an issue with the `reduce()` method on reactive arrays. When calling `reduce()` on a non-shallow reactive array, the accumulator callback doesn't execute properly and the reduction fails completely.

### Reproduction

```js
import { reactive } from 'vue'

const arr = reactive([1, 2, 3, 4])

// This should return 10, but doesn't work
const sum = arr.reduce((acc, item) => {
  return acc + item
}, 0)

console.log(sum) // Expected: 10, Actual: undefined or error
```

Another example with objects:

```js
const items = reactive([
  { value: 1 },
  { value: 2 },
  { value: 3 }
])

const total = items.reduce((acc, item) => {
  return acc + item.value
}, 0)

console.log(total) // Should be 6, but fails
```

### Expected behavior

The `reduce()` method should work normally on reactive arrays, properly iterating through elements and accumulating the result. The callback function should receive the accumulator and current item as expected.

### System Info
- Vue version: 3.x
- Using reactive arrays with reduce method

This seems to have broken recently - reduce was working fine before. Any help would be appreciated!

---
Repository: /testbed
