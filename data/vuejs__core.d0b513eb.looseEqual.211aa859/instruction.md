# Bug Report

### Describe the bug

I'm experiencing an issue with object comparison using `looseEqual()`. When comparing two objects where the second object has more properties than the first, the function returns `true` even though the objects are clearly not equal.

### Reproduction

```js
const obj1 = { name: 'test' }
const obj2 = { name: 'test', age: 25 }

// This returns true but should return false
const result = looseEqual(obj1, obj2)
console.log(result) // Expected: false, Actual: true
```

The objects have different numbers of keys, so they shouldn't be considered equal. This seems to only happen when the second object has additional properties that the first one doesn't have.

### Expected behavior

`looseEqual()` should return `false` when comparing objects with different numbers of properties, regardless of which object has more keys.

### System Info
- Vue version: 3.x

---
Repository: /testbed
