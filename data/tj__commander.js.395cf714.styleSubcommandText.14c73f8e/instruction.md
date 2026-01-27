# Bug Report

### Describe the bug

After a recent update, subcommand text in help output is not being reset properly and is causing styling to bleed into subsequent text. The cyan bold styling applied to subcommands continues to affect text that appears after it, making the help output difficult to read.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();
program
  .command('install')
  .description('Install a package');

program
  .command('update')
  .description('Update packages');

program.parse();
```

Run with `--help` flag and observe that the styling from subcommand names continues into the descriptions or other parts of the help text instead of being properly terminated.

### Expected behavior

Subcommand styling should be self-contained and not affect surrounding text. Each styled element should have proper ANSI reset codes so that styling doesn't leak into other parts of the help output.

### System Info
- Node version: 18.x
- commander version: latest

---
Repository: /testbed
