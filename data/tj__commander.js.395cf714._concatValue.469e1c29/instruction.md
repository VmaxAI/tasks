# Bug Report

### Describe the bug

I'm experiencing an issue with variadic arguments when using the same option multiple times. The values are being collected in the wrong order - later values appear before earlier ones instead of being appended.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-v, --value <item>', 'add value', (value, previous) => {
    // Using default concat behavior
    return previous ? previous.concat(value) : [value];
  }, []);

program.parse(['node', 'test', '-v', 'first', '-v', 'second', '-v', 'third']);

console.log(program.opts().value);
// Expected: ['first', 'second', 'third']
// Actual: ['third', 'second', 'first']
```

### Expected behavior

When specifying an option multiple times, the values should be accumulated in the order they were provided on the command line. The first value should appear first in the array, and subsequent values should be appended.

### System Info
- commander version: latest
- Node.js version: v18.x

---
Repository: /testbed
