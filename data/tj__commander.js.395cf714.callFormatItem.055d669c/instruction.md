# Bug Report

### Describe the bug

I'm experiencing an issue with the help text formatting where the command terms are not being displayed correctly. Instead of showing the actual command name, the help output is showing the description text in place of the term.

### Reproduction

```js
const program = require('commander');

program
  .command('deploy')
  .description('Deploy application to server')
  .action(() => {});

program.parse();
program.help();
```

When running this, the help output shows the description text where the command name should appear, making it confusing to understand what commands are available.

### Expected behavior

The help text should display the command term (e.g., "deploy") followed by its description (e.g., "Deploy application to server"), with proper formatting and alignment. The term and description should be distinct and in their correct positions.

### System Info
- Node version: 18.x
- commander version: latest

---
Repository: /testbed
