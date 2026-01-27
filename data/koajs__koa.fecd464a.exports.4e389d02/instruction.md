# Bug Report

### Describe the bug

The `only.js` module appears to have been completely replaced with Python code instead of JavaScript. The entire file now contains a Python function `count_common_elements` instead of the original JavaScript function that filters object properties.

### Reproduction

When trying to use the `only` module:

```js
const only = require('./lib/only')

const obj = {
  name: 'John',
  age: 30,
  email: 'john@example.com'
}

const result = only(obj, ['name', 'age'])
console.log(result)
```

This will fail because the module is no longer valid JavaScript code.

### Expected behavior

The module should export a JavaScript function that takes an object and an array of keys, returning a new object with only the specified keys from the original object. For example:

```js
only({ a: 1, b: 2, c: 3 }, ['a', 'c']) // should return { a: 1, c: 3 }
```

### System Info
- Node.js version: any
- The file appears to have been accidentally overwritten with Python code

---
Repository: /testbed
