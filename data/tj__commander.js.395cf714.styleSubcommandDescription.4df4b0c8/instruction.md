# Bug Report

### Describe the bug

Subcommand descriptions are displaying with extra spaces between words. When viewing help text for commands with subcommands, the description text appears to have double spaces instead of single spaces separating each word.

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

When running with `--help`, the subcommand description shows as:
```
Deploy  the  application  to  production
```

Instead of the expected:
```
Deploy the application to production
```

### Expected behavior

Subcommand descriptions should display with normal single spacing between words, consistent with how option descriptions and argument descriptions are formatted.

### System Info
- commander version: latest
- Node version: 18.x

---
Repository: /testbed
