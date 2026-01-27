# Bug Report

### Describe the bug

When adding a subcommand using `.addCommand()`, the subcommand is incorrectly being hidden by default. It seems like subcommands are now hidden unless you explicitly pass `noHelp: true` or `hidden: true` in the options, which is the opposite of what should happen.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

const subcommand = new Command('serve')
  .description('Start the server');

program.addCommand(subcommand);

// When checking help output, 'serve' command is hidden
// even though we didn't specify noHelp or hidden options
```

### Expected behavior

Subcommands should be visible in help output by default. They should only be hidden when explicitly setting `noHelp: true` or `hidden: true` in the options passed to `.addCommand()`.

### Additional context

This appears to have started happening recently. Previously, subcommands were visible by default and you had to explicitly hide them. Now the behavior seems reversed - they're hidden unless you tell them to be hidden (which doesn't make sense).

---
Repository: /testbed
