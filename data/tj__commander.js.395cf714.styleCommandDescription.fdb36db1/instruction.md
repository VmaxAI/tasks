# Bug Report

### Describe the bug

Command descriptions are not displaying correctly in help output. When a command has a description text, it shows up as empty/blank instead of the actual description content.

### Reproduction

```js
const program = require('commander');

program
  .command('deploy')
  .description('Deploy application to production')
  .action(() => {});

program.parse();
```

When running with `--help`, the description for the `deploy` command appears blank even though a description was provided.

### Expected behavior

The help output should display "Deploy application to production" next to the deploy command, but instead it shows an empty string.

### System Info
- Node version: 18.x
- commander.js version: latest

---
Repository: /testbed
