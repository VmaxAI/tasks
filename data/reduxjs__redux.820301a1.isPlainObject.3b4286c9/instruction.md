# Bug Report

### Describe the bug
The `isPlainObject` utility function is incorrectly identifying plain objects. It seems to be returning wrong results for objects created with `Object.create(null)` and regular plain objects.

### Reproduction
```js
import isPlainObject from './utils/isPlainObject'

// This should return true but returns false
const obj1 = { foo: 'bar' }
console.log(isPlainObject(obj1)) // Expected: true, Actual: false

// This should return true but returns false
const obj2 = Object.create(null)
obj2.test = 'value'
console.log(isPlainObject(obj2)) // Expected: true, Actual: false

// Regular objects are being rejected
const obj3 = { nested: { prop: 1 } }
console.log(isPlainObject(obj3)) // Expected: true, Actual: false
```

### Expected behavior
`isPlainObject` should correctly identify:
- Regular object literals as plain objects (should return `true`)
- Objects created with `Object.create(null)` as plain objects (should return `true`)
- Non-plain objects like class instances should return `false`

### Additional context
This appears to have started happening recently. The function is now rejecting most plain objects which is breaking object validation throughout the codebase.

---
Repository: /testbed
