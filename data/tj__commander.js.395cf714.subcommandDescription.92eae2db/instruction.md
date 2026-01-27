# Bug Report

### Describe the bug

When displaying help text for subcommands, the description priority seems to have changed unexpectedly. Previously, if a subcommand had both a `summary()` and a `description()`, the summary would be shown in the help output. Now it appears the full description is being displayed instead, which can make the help output verbose and harder to scan.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('deploy')
  .summary('Deploy the application')
  .description('Deploy the application to the specified environment with various configuration options and settings')
  .action(() => {});

program.parse();
```

When running with `--help`, the longer description is now shown in the subcommand list instead of the shorter summary.

### Expected behavior

The help output should prioritize showing the summary (if available) for subcommands in the command list, since summaries are typically shorter and more suitable for overview displays. The full description should only be shown if no summary is provided.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
