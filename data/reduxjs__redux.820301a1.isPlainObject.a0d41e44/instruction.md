# Bug Report

### Describe the bug

I'm experiencing an issue with object detection where certain plain objects are not being recognized correctly. Specifically, objects created with `Object.create(null)` seem to be treated differently than expected.

### Reproduction

```js
const obj1 = Object.create(null)
obj1.foo = 'bar'

const obj2 = {}
obj2.foo = 'bar'

// obj1 should be treated the same way as obj2
// but it's being handled differently
```

When I pass `obj1` (created with `Object.create(null)`) to functions that check if something is a plain object, it doesn't behave the same way as `obj2` (regular object literal).

### Expected behavior

Objects created with `Object.create(null)` should be recognized as plain objects since they're commonly used to create dictionary-like objects without prototype pollution concerns. Both `obj1` and `obj2` from the reproduction should be treated consistently.

### System Info
- Version: latest
- Node: v18.x

---
Repository: /testbed
