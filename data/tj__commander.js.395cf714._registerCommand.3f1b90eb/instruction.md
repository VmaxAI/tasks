# Bug Report

### Describe the bug

I'm experiencing an issue where duplicate command names are not being detected properly when adding commands. It seems like the duplicate check is failing and allowing commands with the same name to be registered.

### Reproduction

```js
const { Command } = require('commander');
const program = new Command();

program
  .command('deploy')
  .description('Deploy application');

// This should throw an error but doesn't
program
  .command('deploy')
  .description('Deploy with different options');

program.parse();
```

### Expected behavior

When trying to register a command with a name that already exists, it should throw an error like:
```
Error: cannot add command 'deploy' as already have command 'deploy'
```

Instead, the second command seems to be registered without any error being raised.

### System Info
- commander.js version: latest
- Node.js version: 18.x

---
Repository: /testbed
