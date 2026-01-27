# Bug Report

### Describe the bug

When trying to add a command with a name that conflicts with an existing command, the error message shows incorrect information. Instead of displaying the existing command's name/aliases, it just shows the conflicting name itself.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('deploy')
  .alias('d')
  .description('Deploy the application');

// Try to add another command with a conflicting alias
program
  .command('download')
  .alias('d')
  .description('Download files');
```

### Expected behavior

The error message should show the full details of the existing command, something like:
```
cannot add command 'download|d' as already have command 'deploy|d'
```

### Actual behavior

The error message shows something unexpected - it seems like the existing command reference is not being resolved properly in the error message.

### System Info
- commander version: latest
- Node.js version: 18.x

---
Repository: /testbed
