# Bug Report

### Describe the bug

When generating help text for subcommands, the description is not being displayed correctly. It seems like when a subcommand has a summary but no description (or vice versa), nothing is shown in the help output at all.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('deploy')
  .summary('Deploy the application')
  .action(() => {});

program.parse();
```

When running with `--help`, the deploy command shows up but has no description text, even though a summary was provided.

### Expected behavior

The help text should display the summary if available, or fall back to the description if there's no summary. At least one of them should be shown if either is defined.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
