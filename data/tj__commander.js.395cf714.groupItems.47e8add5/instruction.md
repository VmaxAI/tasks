# Bug Report

### Describe the bug

I'm experiencing an issue with command grouping in the help output. When displaying help text with multiple commands or options that belong to the same group, only the last item in each group is shown instead of all items. It looks like items are being overwritten rather than accumulated.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('init')
  .description('Initialize project')
  .addHelpGroup('setup');

program
  .command('config')
  .description('Configure project')
  .addHelpGroup('setup');

program
  .command('build')
  .description('Build project')
  .addHelpGroup('build');

program.help();
```

### Expected behavior

The help output should show both `init` and `config` commands under the "setup" group. Instead, only the last command added to each group appears in the help text.

Expected:
```
Setup Commands:
  init     Initialize project
  config   Configure project

Build Commands:
  build    Build project
```

Actual:
```
Setup Commands:
  config   Configure project

Build Commands:
  build    Build project
```

The `init` command is missing from the output even though it was registered.

### System Info
- Node version: v18.x
- commander version: latest

---
Repository: /testbed
