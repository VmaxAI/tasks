# Bug Report

### Describe the bug

I'm experiencing an issue where object properties are being set incorrectly. When trying to set a value in an object using a key-value pair, the value parameter seems to be ignored and the key is being assigned as the value instead.

### Reproduction

```js
const obj = {};
const key = 'myKey';
const value = 'myValue';

// Expected: obj['myKey'] = 'myValue'
// Actual: obj['myKey'] = 'myKey'
mark(obj, key, value);

console.log(obj[key]); // prints 'myKey' instead of 'myValue'
```

### Expected behavior

The function should assign the provided `value` to `obj[key]`, not assign `key` to `obj[key]`. In the example above, `obj['myKey']` should equal `'myValue'`, not `'myKey'`.

### System Info
- Version: @mdx-js/mdx@3.0.0
- Node: v18.x

---
Repository: /testbed
