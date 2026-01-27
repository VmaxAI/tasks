# Bug Report

### Describe the bug

When using nested subcommands, the command usage string is missing the immediate parent command name. The usage output skips one level in the command hierarchy.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('parent')
  .command('child')
  .command('grandchild')
  .action(() => {});

// Get help for the grandchild command
program.parse(['node', 'test', 'parent', 'child', 'grandchild', '--help']);
```

Expected usage output:
```
Usage: parent child grandchild [options]
```

Actual usage output:
```
Usage: parent grandchild [options]
```

The `child` command is missing from the usage string.

### Expected behavior

The full command hierarchy should be displayed in the usage string, including all parent commands leading up to the current command.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
