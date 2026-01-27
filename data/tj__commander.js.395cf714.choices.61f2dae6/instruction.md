# Bug Report

### Describe the bug

When using variadic arguments with `.choices()`, the values are being concatenated in the wrong order. The new value is being added before the previous values instead of after them, which breaks the expected behavior where arguments should be accumulated in the order they are provided.

### Reproduction

```js
const { Argument } = require('commander');

const arg = new Argument('<items...>')
  .choices(['apple', 'banana', 'orange']);

// Simulate parsing multiple values
let result = arg.parseArg('apple', []);
result = arg.parseArg('banana', result);
result = arg.parseArg('orange', result);

console.log(result);
// Expected: ['apple', 'banana', 'orange']
// Actual: ['orange', 'banana', 'apple'] (reversed order)
```

### Expected behavior

Variadic arguments should be accumulated in the order they are provided on the command line. If I pass `--items apple banana orange`, the resulting array should be `['apple', 'banana', 'orange']`, not reversed.

### System Info
- commander.js version: latest
- Node.js version: v18.x

---
Repository: /testbed
