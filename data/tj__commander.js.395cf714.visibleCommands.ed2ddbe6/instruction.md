# Bug Report

### Describe the bug

After updating, the help output is showing hidden commands instead of the visible ones. Also, when subcommands are sorted, they appear in reverse alphabetical order instead of the expected alphabetical order.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('zebra')
  .description('Zebra command');

program
  .command('apple')
  .description('Apple command');

program
  .command('middle')
  .description('Middle command')
  .hideHelp();

program.configureHelp({
  sortSubcommands: true
});

program.parse(['node', 'test', '--help']);
```

### Expected behavior

1. The help output should show `apple` and `zebra` commands (visible commands only)
2. The hidden `middle` command should NOT appear in the help
3. Commands should be sorted in alphabetical order: `apple` then `zebra`

### Actual behavior

1. Only the hidden `middle` command appears in the help
2. Visible commands (`apple`, `zebra`) are not shown
3. When multiple commands are visible, they're sorted in reverse order (z-a instead of a-z)

This is breaking our CLI help output completely. Any command we want to hide is now shown, and any command we want to show is hidden.

---
Repository: /testbed
