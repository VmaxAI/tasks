# Bug Report

### Describe the bug

After updating to the latest version, subcommands are now being sorted alphabetically in the help output. This is breaking our CLI where we intentionally ordered subcommands in a specific logical sequence (e.g., `init`, `build`, `deploy` rather than alphabetically).

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('deploy')
  .description('Deploy the application');

program
  .command('build')
  .description('Build the application');

program
  .command('init')
  .description('Initialize a new project');

program.parse();
```

When running with `--help`, the commands now appear as:
```
Commands:
  build    Build the application
  deploy   Deploy the application
  init     Initialize a new project
```

### Expected behavior

Commands should appear in the order they were added:
```
Commands:
  deploy   Deploy the application
  build    Build the application
  init     Initialize a new project
```

This was the default behavior in previous versions. The sorting seems to be enabled by default now, which changes the help output for existing CLIs that relied on the registration order.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
