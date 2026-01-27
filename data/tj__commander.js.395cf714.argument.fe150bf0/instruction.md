# Bug Report

### Describe the bug

When defining command arguments with both a custom parser function and a default value, the argument gets added to the command twice. This causes the argument to appear duplicated in help text and may lead to unexpected parsing behavior.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<value>', 'A value to process', parseInt, 42)
  .action((value) => {
    console.log('Value:', value);
  });

program.parse();
```

When running `--help`, the argument appears twice in the output. The command also behaves strangely when trying to parse the argument.

### Expected behavior

The argument should only be added once to the command, regardless of whether a parser function and default value are provided. Help text should show the argument only once, and parsing should work correctly.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
