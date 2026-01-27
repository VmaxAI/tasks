# Bug Report

### Describe the bug

The `looseIndexOf` function is returning incorrect indices when searching for elements in an array. It seems to be finding elements from the wrong end of the array instead of returning the first matching element's index.

### Reproduction

```js
import { looseIndexOf } from '@vue/shared'

const arr = [1, 2, 3, 2, 5]
const result = looseIndexOf(arr, 2)

console.log(result) // Expected: 1, but getting wrong value
```

When searching for a value that appears multiple times in an array, the function should return the index of the first occurrence (like the native `indexOf` does), but it's not behaving correctly.

### Expected behavior

`looseIndexOf` should return the index of the first matching element in the array, similar to how `Array.prototype.indexOf()` works. For the example above, searching for `2` should return `1` (the first occurrence), not `3` (the second occurrence).

### System Info
- Vue version: 3.x

---
Repository: /testbed
