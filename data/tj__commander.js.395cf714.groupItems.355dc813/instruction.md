# Bug Report

### Describe the bug

When using custom help formatting with grouped commands/options, the groups are no longer appearing in the correct order. Previously, groups would maintain the order they were defined in the original command configuration, but now they seem to only follow the order of visible items.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('alpha')
  .description('First command')
  .option('--group1', 'Group 1 option');

program
  .command('beta')
  .description('Second command')
  .option('--group2', 'Group 2 option');

program
  .command('gamma')
  .description('Third command')
  .option('--group1', 'Another Group 1 option');

// When displaying help, Group 1 should appear before Group 2
// based on the order commands were added, but the order is wrong
program.parse();
```

The issue is that when you have commands or options that belong to different groups, and those groups should appear in a specific order based on when they were first defined, the help output doesn't respect that ordering anymore.

### Expected behavior

Groups should maintain their order based on the first occurrence in the original item list, not just the visible items. If Group 1 is defined before Group 2 in the command structure, Group 1 should appear first in the help output even if Group 2 items happen to be visible first.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
