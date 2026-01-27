# Bug Report

### Describe the bug

When displaying help text for command arguments that have both a description and extra info (like choices or default values), the description appears in the wrong position. The extra info (in parentheses) is being shown before the description instead of after it.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .argument('<type>', 'The type of operation', 'create')
  .action((type) => {
    console.log(`Type: ${type}`);
  });

program.parse();
```

Run with `--help` flag. The output shows the default value info before the description text instead of after it.

### Expected behavior

The help text should display as:
```
Arguments:
  type        The type of operation (default: "create")
```

But instead it's showing the parenthetical info first, followed by the description.

### System Info
- Node version: 18.x
- commander version: latest

---
Repository: /testbed
