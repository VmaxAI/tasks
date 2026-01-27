# Bug Report

### Describe the bug

I'm experiencing a crash when trying to use an unknown/invalid subcommand. Instead of displaying the help message, the application throws an error and crashes.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .command('valid')
  .action(() => {
    console.log('Valid command executed');
  });

program.parse(['node', 'script.js', 'invalid-command']);
```

When running this with an invalid subcommand name, the program crashes instead of showing help or an error message.

### Expected behavior

When an unknown subcommand is provided, the program should display the help message (similar to what happens in earlier versions). The application shouldn't crash.

### System Info
- commander version: latest
- Node.js: v18.x

---
Repository: /testbed
