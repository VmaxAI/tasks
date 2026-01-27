# Bug Report

### Describe the bug

I'm experiencing an issue with command help groups where the default help group is not being applied to subcommands correctly. When I set a default help group for a parent command and add subcommands without explicitly setting their help group, the subcommands don't inherit the default help group as expected.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

// Set a default help group
program.configureHelp({
  sortSubcommands: true,
});
program.setDefaultCommandGroup('Basic Commands');

// Add a subcommand without specifying a help group
program
  .command('init')
  .description('Initialize a new project');

program
  .command('build')
  .description('Build the project');

program.parse();
```

When running `--help`, the subcommands `init` and `build` don't appear under the "Basic Commands" group. They either appear ungrouped or in the wrong section.

### Expected behavior

Subcommands that don't have an explicit help group should automatically inherit the default help group set on the parent command. The commands `init` and `build` should appear under "Basic Commands" in the help output.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
