# Bug Report

### Describe the bug

When displaying help text for subcommands, the description text appears to have styling applied twice, resulting in malformed or duplicated formatting codes. This doesn't happen with regular option descriptions or argument descriptions.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('deploy')
  .description('Deploy the application to production')
  .action(() => {});

program.parse();
```

When running with `--help`, the subcommand description shows doubled styling effects compared to other help text elements.

### Expected behavior

Subcommand descriptions should have the same styling treatment as option descriptions and argument descriptions - styling should only be applied once to maintain consistent formatting across all help text.

### System Info
- commander.js version: latest
- Node version: 18.x

---
Repository: /testbed
