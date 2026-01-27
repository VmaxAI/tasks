# Bug Report

### Describe the bug

I'm experiencing an issue where command descriptions are not being displayed properly in the help output. When I define a command with a description, the description text doesn't show up at all - it just appears blank or empty in the help menu.

### Reproduction

```js
const program = require('commander');

program
  .command('deploy')
  .description('Deploy the application to production')
  .action(() => {
    // command logic
  });

program.parse(process.argv);
```

When running `node myapp.js deploy --help`, the description for the deploy command is missing from the output. The command name appears but the description is blank.

### Expected behavior

The help output should display "Deploy the application to production" next to the deploy command, similar to how option descriptions are shown correctly.

### System Info
- Node version: 18.x
- OS: macOS

This seems to have started recently - command descriptions were working fine before. Option descriptions still work as expected, it's only the command descriptions that are affected.

---
Repository: /testbed
