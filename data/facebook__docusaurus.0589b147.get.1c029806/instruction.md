# Bug Report

### Describe the bug

I'm experiencing an issue with property copying in the vendored `mdast-util-to-string` module. When properties are being copied from one object to another, the wrong values are being accessed, causing properties to have incorrect or undefined values.

### Reproduction

```js
const source = {
  prop1: 'value1',
  prop2: 'value2',
  prop3: 'value3'
};

const target = {};

// Copy properties using the utility
// Expected: target.prop1 = 'value1', target.prop2 = 'value2', etc.
// Actual: Properties get wrong values or undefined
```

When copying properties between objects, the getter function is accessing the wrong variable, leading to incorrect property values being returned. This affects any code that relies on property enumeration and copying.

### Expected behavior

Properties should be copied with their correct values. When accessing a property on the target object, it should return the same value as the corresponding property on the source object.

### System Info

- Module: mdast-util-to-string@4.0.0
- Affected file: jest/vendor/mdast-util-to-string@4.0.0.js

---
Repository: /testbed
