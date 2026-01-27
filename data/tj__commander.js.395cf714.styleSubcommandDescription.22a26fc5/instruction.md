# Bug Report

### Describe the bug

I'm encountering an issue with subcommand descriptions where the styling is not being applied correctly. When I have a subcommand with a description, the styled output shows `true` or `false` instead of the actual description text.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('deploy')
  .description('Deploy the application to production')
  .action(() => {
    console.log('Deploying...');
  });

program.parse();
```

When running `node app.js --help`, the help output shows:

```
Commands:
  deploy      true
```

Instead of showing the actual description text.

### Expected behavior

The help output should display the actual subcommand description:

```
Commands:
  deploy      Deploy the application to production
```

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
