# Bug Report

### Describe the bug

When using variadic options with the `collect` behavior, the order of collected values is reversed. Values are being prepended instead of appended, causing the most recent value to appear first rather than last in the array.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-v, --value <value>', 'value to collect', (value, previous) => {
    return previous.concat(value);
  }, []);

program.parse(['node', 'test', '-v', 'first', '-v', 'second', '-v', 'third']);

console.log(program.opts().value);
// Expected: ['first', 'second', 'third']
// Actual: ['third', 'second', 'first']
```

The values appear in reverse order compared to how they were provided on the command line.

### Expected behavior

When collecting multiple values for an option, they should be stored in the order they appear on the command line. The first occurrence should be at index 0, the second at index 1, and so on.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
