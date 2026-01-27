# Bug Report

### Describe the bug

When displaying help text for subcommands, the description fallback is not working as expected. If a subcommand has a `description()` but no `summary()`, the description is no longer shown in the help output. Instead, an empty string is displayed.

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

When running `node app.js --help`, the subcommand list shows:

```
Commands:
  deploy    
```

Instead of showing the description text.

### Expected behavior

The help output should display the description when no summary is provided:

```
Commands:
  deploy    Deploy the application to production
```

The description should be used as a fallback when summary is not defined.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
