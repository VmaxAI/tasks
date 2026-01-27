# Bug Report

### Describe the bug

When defining command arguments with a custom parser function and a default value, the default value is not being applied correctly. Instead, the parser function itself seems to be used as the default value.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .argument('<value>', 'A value to parse', parseInt, 42)
  .action((value) => {
    console.log('Value:', value);
    console.log('Type:', typeof value);
  });

// When no argument is provided, expecting default value 42
// But getting unexpected behavior with the parser function
program.parse(['node', 'test']);
```

### Expected behavior

When an argument is defined with both a custom parser function and a default value, the default value should be used when the argument is not provided. In the example above, if no value is passed, it should use `42` as the default.

### Actual behavior

The default value parameter is not being applied correctly when a parser function is provided. The behavior suggests the parameters are being mixed up.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
