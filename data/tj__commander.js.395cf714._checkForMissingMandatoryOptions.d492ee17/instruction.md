# Bug Report

### Describe the bug

Mandatory options on the root command are not being validated anymore. When I define a required option on my main command and don't provide it, the program runs without any error instead of throwing a missing mandatory option error.

### Reproduction

```js
const { Command } = require('commander');

const program = new Command();

program
  .requiredOption('-u, --user <name>', 'user name is required')
  .action(() => {
    console.log('Action executed');
  });

// Run without providing the required option
program.parse(['node', 'script.js']);
```

### Expected behavior

The program should throw an error about the missing mandatory option `--user`, but instead it just runs normally and executes the action. This used to work correctly before - mandatory options on the root command were properly validated.

### System Info
- commander version: latest
- Node.js version: v18.x

---
Repository: /testbed
