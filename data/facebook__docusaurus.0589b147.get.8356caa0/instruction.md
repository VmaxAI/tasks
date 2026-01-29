# Bug Report

### Describe the bug
I'm experiencing an issue with object property copying that's causing an infinite loop/stack overflow. When copying properties between objects, the code seems to be referencing itself instead of the source object, which leads to recursive calls until the stack overflows.

### Reproduction
```js
const source = {
  name: 'test',
  value: 42,
  nested: { data: 'example' }
}

const target = {}

// Attempting to copy properties from source to target
// Results in stack overflow error
copyProperties(target, source)
```

### Expected behavior
Properties should be copied from the source object to the target object without errors. The target object should have the same properties as the source with proper values.

### System Info
- Node version: 18.x
- Browser: N/A (server-side issue)

This is blocking our build process as it causes crashes during property enumeration. Any help would be appreciated!

---
Repository: /testbed
