# Bug Report

### Describe the bug

I'm experiencing an issue with object property copying in the rehype-stringify vendor module. When copying properties from one object to another, properties that should be excluded are being copied, and properties that should be included are being excluded.

### Reproduction

```js
const source = {
  foo: 'value1',
  bar: 'value2',
  baz: 'value3'
}

const target = {}

// Trying to copy all properties except 'bar'
// But 'bar' gets copied and everything else is excluded
copyProps(target, source, 'bar')

console.log(target)
// Expected: { foo: 'value1', baz: 'value3' }
// Actual: { bar: 'value2' }
```

The behavior is completely inverted - the property specified as the exception is the only one being copied, while all other properties are being ignored.

### Expected behavior

When using the property copy function with an exception parameter, all properties should be copied EXCEPT the one specified in the exception parameter. Currently it's doing the opposite.

### System Info
- rehype-stringify version: 10.0.0
- Node version: Latest

---
Repository: /testbed
