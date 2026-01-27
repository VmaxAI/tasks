# Bug Report

### Describe the bug

When using variadic options/arguments that can be specified multiple times, the order of values is reversed. The last specified value appears first in the resulting array instead of maintaining the order they were provided on the command line.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .option('-v, --value <items...>', 'values');

program.parse([
  'node',
  'test.js',
  '--value', 'first',
  '--value', 'second',
  '--value', 'third'
]);

console.log(program.opts().value);
// Outputs: ['third', 'second', 'first']
// Expected: ['first', 'second', 'third']
```

### Expected behavior

Values should be collected in the order they appear on the command line. When specifying `--value first --value second --value third`, the resulting array should be `['first', 'second', 'third']`, not reversed.

This is breaking existing scripts that rely on the order of arguments being preserved (e.g., processing files in a specific sequence, priority ordering, etc.).

---
Repository: /testbed
