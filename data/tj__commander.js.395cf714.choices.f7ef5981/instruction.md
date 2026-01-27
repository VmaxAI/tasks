# Bug Report

### Describe the bug

When using variadic arguments with `.choices()`, the values are being concatenated in the wrong order. The new value gets prepended instead of appended to the previous values array.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<items...>')
  .choices(['apple', 'banana', 'orange']);

// Parsing multiple values
const result1 = arg.parseArg('apple', []);
const result2 = arg.parseArg('banana', result1);
const result3 = arg.parseArg('orange', result2);

console.log(result3);
// Expected: ['apple', 'banana', 'orange']
// Actual: ['orange', 'banana', 'apple']
```

### Expected behavior

Variadic arguments should maintain the order they were provided in. The first value should be at index 0, the second at index 1, and so on.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
