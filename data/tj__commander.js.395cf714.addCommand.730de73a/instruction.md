# Bug Report

### Describe the bug

When adding multiple subcommands with `isDefault: true` option, the last command added with this option doesn't become the default command. Instead, the first command added with `isDefault: true` remains as the default, even though subsequent calls to `addCommand()` with `isDefault: true` should override it.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

const cmd1 = new Command('first');
const cmd2 = new Command('second');

program.addCommand(cmd1, { isDefault: true });
program.addCommand(cmd2, { isDefault: true });

// Expected: cmd2 should be the default command
// Actual: cmd1 remains the default command
```

### Expected behavior

When adding a command with `isDefault: true`, it should override any previously set default command. The most recently added default command should be the active default.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
