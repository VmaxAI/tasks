# Bug Report

### Describe the bug

The help output is showing hidden commands instead of visible ones. When I run `--help` on my CLI application, I'm seeing commands that should be hidden (marked with `_hidden`), while the normal visible commands are not appearing at all.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('public-cmd')
  .description('This should be visible');

program
  .command('secret-cmd')
  .description('This should be hidden')
  .hideHelp();

program.parse();
```

When running with `--help`, the output shows `secret-cmd` but not `public-cmd`. It's completely backwards - hidden commands are visible and visible commands are hidden.

### Expected behavior

The help text should display only the visible commands (those without `_hidden` set or with `_hidden: false`). Hidden commands should not appear in the help output.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
