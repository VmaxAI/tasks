# Bug Report

### Describe the bug

I'm experiencing issues with loose equality comparisons when comparing arrays with non-arrays and when comparing objects with different keys. The comparison is returning `true` in cases where it should clearly return `false`.

### Reproduction

```js
import { looseEqual } from '@vue/shared'

// Case 1: Comparing array with non-array
const arr = [1, 2, 3]
const obj = { 0: 1, 1: 2, 2: 3 }

console.log(looseEqual(arr, obj)) // Returns true, but should be false

// Case 2: Comparing objects with different keys
const obj1 = { name: 'test', age: 25 }
const obj2 = { name: 'test' }

console.log(looseEqual(obj1, obj2)) // Returns true, but should be false
```

### Expected behavior

- When comparing an array to a non-array object (even if it has numeric keys), `looseEqual` should return `false`
- When comparing objects where one has keys that the other doesn't have, `looseEqual` should return `false`

Currently these comparisons are incorrectly returning `true` which is causing issues in my application where I need to detect when values have actually changed.

### System Info
- Vue version: 3.x

---
Repository: /testbed
