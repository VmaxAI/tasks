# Bug Report

### Describe the bug

The help text for command arguments is displaying incorrectly. When an argument has both a description and extra information (like default values or choices), only the extra information is shown without the description text.

### Reproduction

```js
const program = require('commander');

program
  .argument('<name>', 'User name to process')
  .option('-t, --type <type>', 'Type of user', 'regular')
  .parse();

program.help();
```

Expected output should show something like:
```
Arguments:
  name                User name to process
```

But the description part is missing or not displaying as expected.

### Expected behavior

When arguments have descriptions along with default values or choices, both should be displayed together in the help output. The description should come first, followed by the extra info in parentheses.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
