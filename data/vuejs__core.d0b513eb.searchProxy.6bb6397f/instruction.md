# Bug Report

### Describe the bug

Array search methods like `indexOf`, `lastIndexOf`, and `includes` are completely broken after a recent update. These methods are essential for finding elements in reactive arrays but they no longer work at all.

### Reproduction

```js
import { reactive } from 'vue'

const arr = reactive([1, 2, 3, 4])
const result = arr.indexOf(2)
// TypeError: arr[method] is not a function

const items = reactive([{ id: 1 }, { id: 2 }])
const target = items[0]
const index = items.indexOf(target)
// Also throws error
```

### Expected behavior

Array search methods should work normally on reactive arrays:
- `indexOf()` should return the index of the element or -1 if not found
- `lastIndexOf()` should return the last index of the element or -1 if not found  
- `includes()` should return true/false based on whether the element exists

These methods should also handle reactive proxy objects correctly - searching for a reactive object should find it even if the search argument is the raw version or vice versa.

### System Info
- Vue version: 3.x
- Node version: 18.x

This is blocking our application from working as we rely heavily on array search operations. Any help would be appreciated!

---
Repository: /testbed
