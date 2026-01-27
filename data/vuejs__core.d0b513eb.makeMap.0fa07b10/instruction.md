# Bug Report

### Describe the bug

I'm experiencing an issue with string-based lookup maps where the first item in a comma-separated list is being ignored. When creating a map from a string like `'foo,bar,baz'`, lookups for the first element (`'foo'`) return `undefined` instead of the expected truthy value.

### Reproduction

```js
const isKeyword = makeMap('if,else,for,while')

console.log(isKeyword('if'))     // Expected: true, Actual: undefined
console.log(isKeyword('else'))   // Works correctly: 1
console.log(isKeyword('for'))    // Works correctly: 1
console.log(isKeyword('while'))  // Works correctly: 1
console.log(isKeyword('other'))  // Expected: false/undefined, Actual: undefined
```

The first item in the list is consistently missing from the map, but all subsequent items work as expected.

### Expected behavior

All items in the comma-separated string should be included in the map and return a truthy value when looked up. The first element should not be skipped.

### System Info
- Version: latest
- Environment: Node.js

---
Repository: /testbed
